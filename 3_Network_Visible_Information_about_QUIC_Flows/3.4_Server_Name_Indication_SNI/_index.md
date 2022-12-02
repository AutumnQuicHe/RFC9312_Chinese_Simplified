---
title: "3.4. 服务器名称指示（SNI）"
anchor: "3.4_Server_Name_Indication_SNI"
weight: 340
rank: "h2"
---

The client's TLS ClientHello may contain a Server Name Indication (SNI) extension [RFC6066] by which the client reveals the name of the server it intends to connect to in order to allow the server to present a certificate based on that name. If present, SNI information is available to unidirectional observers on the client-to-server path if it.

客户端的TLS `ClientHello`中可能含有服务器名称指示（SNI）扩展（详见《[RFC6066](https://www.rfc-editor.org/info/rfc6066)》），客户端通过它来表明想要连接的服务器的名称，以使得服务器能够基于该名称来提供证书。
如果使用了该扩展，那么在由客户端至服务器的路径上的单向观察者就能看到SNI信息。

The TLS ClientHello may also contain an Application-Layer Protocol Negotiation (ALPN) extension [RFC7301], by which the client exposes the names of application-layer protocols it supports; an observer can deduce that one of those protocols will be used if the connection continues.

TLS `ClientHello`中还可能含有应用层协议协商（ALPN）扩展（详见《[RFC7301](https://www.rfc-editor.org/info/rfc7301)》），客户端通过它来宣告它支持的应用层协议名称列表；观察者可以推断出这些协议中的一个会在后续连接中得到使用。

Work is currently underway in the TLS working group to encrypt the contents of the ClientHello in TLS 1.3 [TLS-ECH]. This would make SNI-based application identification impossible by on-path observation for QUIC and other protocols that use TLS.

TLS工作组正在进行为TLS 1.3中的`ClientHello`内容加密的工作（详见《[TLS-ECH](https://datatracker.ietf.org/doc/html/draft-ietf-tls-esni-14)》）。
这将消除通过在路径上观察QUIC和其他使用TLS的协议来基于SNI识别应用的可能性。
