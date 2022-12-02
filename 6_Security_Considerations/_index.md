---
title: "6. 关于安全性的考量"
anchor: "6_Security_Considerations"
weight: 600
rank: "h1"
---

QUIC is an encrypted and authenticated transport. That means once the cryptographic handshake is complete, QUIC endpoints discard most packets that are not authenticated, greatly limiting the ability of an attacker to interfere with existing connections.

QUIC是一份受加密且经认证的传输协议。这意味着一旦加密握手完成，QUIC终端就会丢弃绝大多数未经认证的数据包，极大地限制了攻击者介入已建立的连接的能力。

However, some information is still observable as supporting manageability of QUIC traffic inherently involves trade-offs with the confidentiality of QUIC's control information; this entire document is therefore security-relevant.

然而，仍然可以观察到一些信息，因为对QUIC流量可管理性的支持，其本质涉及到对QUIC控制信息机密性的权衡；因此通篇文档的内容都是关于安全性的。

More security considerations for QUIC are discussed in [QUIC-TRANSPORT] and [QUIC-TLS], which generally consider active or passive attackers in the network as well as attacks on specific QUIC mechanism.

《[QUIC传输](../RFC9000_Chinese_Simplified)》和《[QUIC-TLS](../RFC9001_Chinese_Simplified)》中对QUIC的安全性进行了更多的讨论，其中一般化地考虑了网络中的主动攻击者与被动攻击者，以及针对特定QUIC机制的攻击。

Version Negotiation packets do not contain any mechanism to prevent version downgrade attacks. However, future versions of QUIC that use Version Negotiation packets are required to define a mechanism that is robust against version downgrade attacks. Therefore, a network node should not attempt to impact version selection, as version downgrade may result in connection failure.

版本协商数据包中并不包含任何防止版本降级攻击的机制。但是，将来的使用版本协商数据包的QUIC版本必须定义一项机制，使其面对版本降级攻击的表现足够健壮。因此，网络节点不应该试图影响版本的选择过程，因为版本降级可能造成连接失败。
