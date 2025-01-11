---
id: 93929
title: 'Apache Ignite: "IgniteCheckedException: No clients found"'
date: '2024-07-02T10:48:00+01:00'
author: 'Stephen Darlington'
excerpt: 'Debugging a common exception seen when using Apache Ignite.'
layout: post
guid: 'https://www.zx81.org.uk/?p=93929'
aliases: ['/computing/opinion/apache-ignite-ignitecheckedexception-no-clients-found.html']
categories:
    - Opinion
tags:
    - 'Apache Ignite'
    - debug
    - java
    - Programming
---

You know that thing were you’re trying to debug a problem and you just know that *you’re* the culprit, that past-you did something stupid, and you just can’t figure out what?

Welcome to my day.

Anyway, I’m documenting my stupidity so you don’t have to suffer as long as I did.

The background: in order to debug an application that runs on a cluster can be a challenge. The way I tend to do it is to run a server in debug mode in my IDE and connect to that same server using a client. The server is super-simple:

```scala
object Server extends App {
    val ignite = {
        val igniteConfiguration = new IgniteConfiguration()
        igniteConfiguration.setPeerClassLoadingEnabled(true)
        val ipFinder = new TcpDiscoveryVmIpFinder()
        val addresses = util.Arrays.asList("127.0.0.1")
        ipFinder.setAddresses(addresses)
        val discoverySpi = new TcpDiscoverySpi()
        discoverySpi.setIpFinder(ipFinder)
        igniteConfiguration.setDiscoverySpi(discoverySpi)
        Ignition.start(igniteConfiguration)
    }
}
```

I click the “Debug” button in my IDE and away it goes.

My client starts basically the same way, except I have the `Ignition.setClientMode(true)` statement first. There’s more stuff, but it never gets there.

Instead I get a stack trace:

```
Aug 15, 2019 4:56:41 PM org.apache.ignite.logger.java.JavaLogger error
SEVERE: Failed to send message to remote node [node=TcpDiscoveryNode [id=d7248cbc-39b5-496a-a4e4-cf1f49eb5cb3, consistentId=127.0.0.1,192.168.1.16:47500, addrs=[127.0.0.1, 192.168.1.16], sockAddrs=[/192.168.1.16:47500, /127.0.0.1:47500], discPort=47500, order=1, intOrder=1, lastExchangeTime=1565884601101, loc=false, ver=8.7.6#20190704-sha1:6449a674, isClient=false], msg=GridIoMessage [plc=2, topic=TOPIC_CACHE, topicOrd=8, ordered=false, timeout=0, skipOnTimeout=false, msg=GridDhtPartitionsSingleMessage [parts=null, partCntrs=null, partsSizes=null, partHistCntrs=null, err=null, client=true, exchangeStartTime=100453829886160, finishMsg=null, super=GridDhtPartitionsAbstractMessage [exchId=GridDhtPartitionExchangeId [topVer=AffinityTopologyVersion [topVer=2, minorTopVer=0], discoEvt=DiscoveryEvent [evtNode=TcpDiscoveryNode [id=591e6724-f22d-4bad-a906-819862178db2, consistentId=591e6724-f22d-4bad-a906-819862178db2, addrs=[0:0:0:0:0:0:0:1%lo0, 127.0.0.1, 192.168.1.16], sockAddrs=[/192.168.1.16:0, /0:0:0:0:0:0:0:1%lo0:0, /127.0.0.1:0], discPort=0, order=2, intOrder=0, lastExchangeTime=1565884600967, loc=true, ver=8.7.6#20190704-sha1:6449a674, isClient=true], topVer=2, nodeId8=591e6724, msg=null, type=NODE_JOINED, tstamp=1565884601135], nodeId=591e6724, evt=NODE_JOINED], lastVer=GridCacheVersion [topVer=0, order=1565884600540, nodeOrder=0], super=GridCacheMessage [msgId=1, depInfo=null, lastAffChangedTopVer=AffinityTopologyVersion [topVer=-1, minorTopVer=0], err=null, skipPrepare=false]]]]]<br></br>class org.apache.ignite.IgniteCheckedException: No clients found<br></br> at org.apache.ignite.spi.communication.tcp.TcpCommunicationSpi.createTcpClient(TcpCommunicationSpi.java:3536)<br></br> at org.apache.ignite.spi.communication.tcp.TcpCommunicationSpi.createNioClient(TcpCommunicationSpi.java:3035)<br></br> at org.apache.ignite.spi.communication.tcp.TcpCommunicationSpi.reserveClient(TcpCommunicationSpi.java:2915)
```

The important bit here is the “IgniteCheckedException: No clients found” part. The server does see the client, and logs the fact that there is now a new client.

```
[16:56:34] Topology snapshot [ver=1, locNode=d7248cbc, servers=1, clients=0, state=ACTIVE, CPUs=8, offheap=3.2GB, heap=4.0GB]
[16:56:41] Topology snapshot [ver=2, locNode=d7248cbc, servers=1, clients=1, state=ACTIVE, CPUs=16, offheap=3.2GB, heap=8.0GB]
[16:57:11] Topology snapshot [ver=3, locNode=d7248cbc, servers=1, clients=0, state=ACTIVE, CPUs=8, offheap=3.2GB, heap=4.0GB]
```

So discovery worked but it can’t connect. Firewalls? Some weird permissions? (Just me that thinks of [this routine](https://www.youtube.com/watch?v=TKQzqwn-jIM)? ?It’s *here!*?)

I created a plain Java version of the server and that worked! I’m really confused now.

Scala just kicks off the Java code, so it can’t be the difference in language. Which leaves? how we call it.

On the server, long ago, I’d set the following as the options for the VM:

```
-Djava.net.preferIPv4Stack=true -XX:+UseG1GC -XX:+DisableExplicitGC
```

My newly created client did not. I *guess* it was trying to connect to the IPv6 address/port and that’s why it couldn’t find the server node; I didn’t delve too deeply.

Instead, I just added the “`-Djava.net.preferIPv4Stack=true`” option to the client and everything worked.

*This post originally appeared on Medium in 2019. It has been lightly edited to reflect recent technical changes.*