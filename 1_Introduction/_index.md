---
title: "1. 引言"
anchor: "1_Introduction"
weight: 100
rank: "h1"
---

QUIC [QUIC-TRANSPORT] is a new transport protocol that is encapsulated in UDP. QUIC integrates TLS [QUIC-TLS] to encrypt all payload data and most control information. QUIC version 1 was designed primarily as a transport for HTTP with the resulting protocol being known as HTTP/3 [QUIC-HTTP].

QUIC（详见《[QUIC传输](../RFC9000_Chinese_Simplified)》）是一种封装在UDP中的全新的传输协议。
QUIC集成了TLS（详见《[QUIC-TLS](../RFC9001_Chinese_Simplified)》)，从而加密所有载荷数据与绝大多数控制信息。
QUIC版本1主要是作为HTTP的传输方式来设计的，作为其成果的协议被称为HTTP/3（详见《[QUIC-HTTP](../RFC9114_Chinese_Simplified)》）。

This document provides guidance for network operations that manage QUIC traffic. This includes guidance on how to interpret and utilize information that is exposed by QUIC to the network, requirements and assumptions of the QUIC design with respect to network treatment, and a description of how common network management practices will be impacted by QUIC.

本文档为管理QUIC流量的网络操作提供了指导。
这些指导内容中包含如何解释和利用QUIC向网络暴露的信息、QUIC设计关于网络条件待遇的要求和假设，以及一份QUIC将如何影响常见网络管理实践的说明。

QUIC is an end-to-end transport protocol; therefore, no information in the protocol header is intended to be mutable by the network. This property is enforced through integrity protection of the wire image [WIRE-IMAGE]. Encryption of most transport-layer control signaling means that less information is visible to the network in comparison to TCP.

QUIC是一份端到端的传输协议；因此，协议头部中的所有信息都不得被网络修改。
这项属性是通过对通信线路图象的完整性保护来做到的（详见《[WIRE-IMAGE](https://www.rfc-editor.org/info/rfc8546)》）。
对绝大多数传输层控制信号的加密意味着比起TCP，对网络可见的信息更少。

Integrity protection can also simplify troubleshooting at the end points as none of the nodes on the network path can modify transport layer information. However, it means in-network operations that depend on modification of data (for examples, see [RFC9065]) are not possible without the cooperation of a QUIC endpoint. Such cooperation might be possible with the introduction of a proxy that authenticates as an endpoint. Proxy operations are not in scope for this document.

完整性保护还可以简化终端处的故障排查，因为网络路径上的所有节点都无法修改传输层信息。
不过，这意味着一旦缺少QUIC终端的配合，就无法实施基于数据修改（作为例子，详见《[RFC9065](https://www.rfc-editor.org/info/rfc9065)》）的网络内操作。
通过引入被当成是终端的代理，或许可以实施这类操作。
代理操作不在本文档的讨论范畴之内。

Network management is not a one-size-fits-all endeavor; for example, practices considered necessary or even mandatory within enterprise networks with certain compliance requirements would be impermissible on other networks without those requirements. Therefore, presence of a particular practice in this document should not be construed as a recommendation to apply it. For each practice, this document describes what is and is not possible with the QUIC transport protocol as defined.

网络管理不是一刀切的工作；例如，在具有某些合规性要求的企业网络中被认为是必要甚至是强制的做法在没有这些要求的其他网络中是不被允许的。
因此，本文档中某些做法实践的提及不应该被理解为对它们的推荐。
对于每一种实践，本文档都会介绍QUIC传输协议能够做到什么和不能够做到什么。

This document focuses solely on network management practices that observe traffic on the wire. For example, replacement of troubleshooting based on observation with active measurement techniques is therefore out of scope. A more generalized treatment of network management operations on encrypted transports is given in [RFC9065].

本文档主要着重于能够观察线路上的流量的网络管理实践。
因此，举个例子，使用主动测量技术来代替基于观察的故障排查的做法不在讨论范畴之内。
《[RFC9065](https://www.rfc-editor.org/info/rfc9065)》中针对加密传输协议给出了一份更加通用的的网络管理操作方法。

QUIC-specific terminology used in this document is defined in [QUIC-TRANSPORT].

有关本文档中使用的QUIC相关术语定义，详见《[QUIC传输](../RFC9000_Chinese_Simplified)》。
