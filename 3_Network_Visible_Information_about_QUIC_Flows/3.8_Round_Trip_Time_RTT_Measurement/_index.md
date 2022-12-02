---
title: "3.8. 往返时间（RTT）的测量"
anchor: "3.8_Round_Trip_Time_RTT_Measurement"
weight: 380
rank: "h2"
---

The round-trip time (RTT) of QUIC flows can be inferred by observation once per flow during the handshake in passive TCP measurement; this requires parsing of the QUIC packet header and recognition of the handshake, as illustrated in Section 2.4. It can also be inferred during the flow's lifetime if the endpoints use the spin bit facility described below and in Section 17.3.1 of [QUIC-TRANSPORT]. RTT measurement is available to unidirectional observers when the spin bit is enabled.

通过在握手期间用被动TCP测量的方法为每路流量进行一次性的观察，可以推断出QUIC流量的往返时间（RTT）；该方法需要解析QUIC数据包的头部，并识别出握手过程，如[第2.4章]()所示。如果终端使用了下文和《[QUIC传输]()》的[第17.3.1章]()所述的自旋比特位特性，那么还可以在流量存续时推断出往返时间。当自旋比特位被启用时，即使是单向的观察者也可以进行RTT测量。
