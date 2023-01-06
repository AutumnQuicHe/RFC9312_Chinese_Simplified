---
title: "3.4. 服务器名称指示（SNI）"
anchor: "3.4_Server_Name_Indication_SNI"
weight: 340
rank: "h2"
---

客户端的TLS `ClientHello`中可能含有服务器名称指示（SNI）扩展（详见《[RFC6066](https://www.rfc-editor.org/info/rfc6066)》），客户端通过它来表明想要连接的服务器的名称，以使得服务器能够基于该名称来提供证书。
如果使用了该扩展，那么在由客户端至服务器的路径上的单向观察者就能看到SNI信息。

TLS `ClientHello`中还可能含有应用层协议协商（ALPN）扩展（详见《[RFC7301](https://www.rfc-editor.org/info/rfc7301)》），客户端通过它来宣告它支持的应用层协议名称列表；观察者可以推断出这些协议中的一个会在后续连接中得到使用。

TLS工作组正在进行为TLS 1.3中的`ClientHello`内容加密的工作（详见《[TLS-ECH](https://datatracker.ietf.org/doc/html/draft-ietf-tls-esni-14)》）。
这将消除通过在路径上观察QUIC和其他使用TLS的协议来基于SNI识别应用的可能性。
