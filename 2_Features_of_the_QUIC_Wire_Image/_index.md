---
title: "2. QUIC通信线路图象的特征"
anchor: "2_Features_of_the_QUIC_Wire_Image"
weight: 200
rank: "h1"
---

This section discusses aspects of the QUIC transport protocol that have an impact on the design and operation of devices that forward QUIC packets. Therefore, this section is primarily considering the unencrypted part of QUIC's wire image [WIRE-IMAGE], which is defined as the information available in the packet header in each QUIC packet, and the dynamics of that information. Since QUIC is a versioned protocol, the wire image of the header format can also change from version to version. However, the field that identifies the QUIC version in some packets and the format of the Version Negotiation packet are both inspectable and invariant [QUIC-INVARIANTS].

本章讨论的是QUIC传输协议能够影响转发QUIC数据包的设备的设计及操作的一些方面。因此，本章主要考虑的是QUIC通信线路图象（详见《[WIRE-IMAGE](https://www.rfc-editor.org/info/rfc8546)》）的未加密部分，也就是每个QUIC数据包头部中的信息及其变化规律。由于QUIC是一份版本化的协议，因此其头部格式的通信线路图象还可能随版本变化而变化。不过，部分数据包中用于标识QUIC版本的字段和版本协商数据包的格式都是可检视且不变的（详见《[QUIC不变量](../RFC8999_Chinese_Simplified)》）。

This document addresses version 1 of the QUIC protocol, whose wire image is fully defined in [QUIC-TRANSPORT] and [QUIC-TLS]. Features of the wire image described herein may change in future versions of the protocol except when specified as an invariant [QUIC-INVARIANTS] and cannot be used to identify QUIC as a protocol or to infer the behavior of future versions of QUIC.

本文档的对象是QUIC协议版本1，《[QUIC传输](../RFC9000_Chinese_Simplified)》和《[QUIC-TLS](../RFC9001_Chinese_Simplified)》中定义了其完整的通信线路图象。除非是指定为不变量的（详见《[QUIC不变量](../RFC8999_Chinese_Simplified)》）和无法被用来辨识QUIC协议或用来推断将来版本的QUIC行为的那些，本文中介绍的通信线路图象特征都可能在将来版本的协议中发生变化。
