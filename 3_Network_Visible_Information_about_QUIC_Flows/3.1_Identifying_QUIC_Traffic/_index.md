---
title: "3.1. 识别QUIC流量"
anchor: "3.1_Identifying_QUIC_Traffic"
weight: 310
rank: "h2"
---

The QUIC wire image is not specifically designed to be distinguishable from other UDP traffic by a passive observer in the network. While certain QUIC applications may be heuristically identifiable on a per-application basis, there is no general method for distinguishing QUIC traffic from otherwise unclassifiable UDP traffic on a given link. Therefore, any unrecognized UDP traffic may be QUIC traffic.

QUIC的通信线路图象并没有被专门设计成对网络内的被动观察者来说可以与其他UDP流量相互区分的样子。尽管有可能用启发式的方法一个个识别出QUIC应用的流量，但是不存在将QUIC流量从给定链路上的所有未分类UDP流量中挑选出来的方法。因此，任何未归类的UDP流量都可能是QUIC流量。

At the time of writing, two application bindings for QUIC have been published or adopted by the IETF: HTTP/3 [QUIC-HTTP] and DNS over Dedicated QUIC Connections [RFC9250]. These are both known to have active Internet deployments, so an assumption that all QUIC traffic is HTTP/3 is not valid. HTTP/3 uses UDP port 443 by convention but various methods can be used to specify alternate port numbers. Other applications (e.g., Microsoft's SMB over QUIC) also use UDP port 443 by default. Therefore, simple assumptions about whether a given flow is using QUIC (or indeed which application might be using QUIC) based solely upon a UDP port number may not hold; see Section 5 of [RFC7605].

在本文写作之时，IETF已经出版或采纳了两种对QUIC的应用绑定：HTTP/3（详见《[QUIC-HTTP]()》）和DNS专用QUIC连接（详见《[RFC9250]()》）。这两者均已知存在活跃的互联网部署，因此所有QUIC流量都是HTTP/3流量的假设是不成立的。按照约定，HTTP/3使用UDP端口`443`，但是可以使用各种各样的方法来指定替代端口号。其他应用（例如，微软的基于QUIC的SMB）也默认使用UDP端口`443`。因此，简单地基于某个UDP端口号来判断给定流量是否使用了QUIC（或实际上是哪个应用在使用QUIC）的做法也是站不住脚的；详见《[RFC7605]()》的[第5章]()。

While the second-most-significant bit (0x40) of the first octet is set to 1 in most QUIC packets of the current version (see Section 2.1 and Section 17 of [QUIC-TRANSPORT]), this method of recognizing QUIC traffic is not reliable. First, it only provides one bit of information and is prone to collision with UDP-based protocols other than those considered in [RFC7983]. Second, this feature of the wire image is not invariant [QUIC-INVARIANTS] and may change in future versions of the protocol or even be negotiated during the handshake via the use of an extension [QUIC-GREASE].

尽管首个字节的第二最高有效位（掩码为`0x40`）在绝大多数当前版本的QUIC数据包中被设置为`1`（详见《[QUIC传输]()》的[第2.1章]()和[第17章]()），但是这种识别QUIC流量的方法是不可靠的。首先，它仅仅提供了一个比特位的信息，并且很容易与除了《[RFC7983]()》中讨论的那些之外的基于UDP的协议冲突。第二，通信线路图象的该特征并不是一成不变的（详见《[QUIC不变量]()》），它在将来版本的协议中可能发生变化，甚至在握手期间通过使用扩展来协商（详见《[QUIC位转义]()》）。

Even though transport parameters transmitted in the client's Initial packet are observable by the network, they cannot be modified by the network without causing a connection failure. Further, the reply from the server cannot be observed, so observers on the network cannot know which parameters are actually in use.

即便在客户端初始数据包中传递的传输参数可以被网络观测到，但是网络无法在不引发连接失败的情况下篡改它们。此外，来自服务器的回复内容无法被观察到，所以网络上的观察者无法知道实际使用了哪些参数。
