---
title: Transmission Control Protocol (TCP)
---

TCP is a protocol which offers reliable communication channel over an unreliable network. It ensures that packets are delivered in-order, even over a congested network.

# Operation
* TCP connection starts with a three way handshake. The happy path is `client: syn`, `server: syn-ack`, `client: ack`. If the port is closed the server responds with `rst`, or if the port is filtered there's no response.
* The connection ends with `fin`.
* TCP operates on the transport layer and wraps the data written to it in segments. Then hands the segments to network layer.
* TCP stores the data to send in __send buffer__ and to receive in __receive buffer__. When application is ready it will read from the receive buffer.

# Features
* In-order delivery
* Congestion control
    * slow start and congestion avoidance.
* Flow control
    * to make sure the receiver is not overwhelmed with packages (when the receive buffer is full the receiver needs to drop packages) but also the network is utilized, see Z: Bandwidth-delay product (BDP).
        * Receive window `rwnd` is the space left in the TCP receive buffer. The receiver sends it current `rwnd` with each ACK message.
        * The sender will keep sending packets as long us `rwnd > 0`. It will aim to keep the `Last byte sent last byte ACKed <= rwnd`.
        * When`rwnd == 0` the sender stops sending packets. It then occasionally probs the receiver with `WindowProbe` packet (sent after __persist timer__) so the receiver can advertise a non-empty window.



# References
* Talk _Networking Best Practices_ by Joshua Graessley
    * [WWDC 2012 session 706](./https://www.youtube.com/watch?v=aRsPC2g77es)
* Article on [TCP flow control](https://www.brianstorti.com/tcp-flow-control/)
    * And my [repo where I recreate their Wireshark example](https://github.com/igor-kupczynski/wireshark-examples/tree/master/02-flowcontrol)