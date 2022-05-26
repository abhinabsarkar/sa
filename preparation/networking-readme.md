# Networking - Technical interview questions & answers
1. What is layer 3 of the OSI model. Describe. - Network Layer where we deal with routing & IP addresses (logical address) - data gets converted to packets, Router works on this layer & that's how two machines on the internet interact with each other. The network layer performs network routing functions, and might also perform fragmentation and reassembly, and report delivery errors. [Video explanation](https://youtu.be/Wv-K6hr23iE?t=16)

    * Explain OSI model - [OSI - Open System Interconnection model explained](https://github.com/abhinabsarkar/networking-concepts/blob/master/concepts/osi-readme.md)
    * Networking basics - [CIDR, Subnet, IP addressing](https://github.com/abhinabsarkar/networking-concepts/blob/master/concepts/subnetting-readme.md)

2. Difference between broadcast, multicast and unicast - A Unicast transmission/stream sends IP packets to a single recipient on a network. A Multicast transmission sends IP packets to a group of hosts on a network. [Video explanation](https://www.youtube.com/watch?v=xr1u3LUwcek)

3. TCP vs UDP - Transmission Control Protocol (TCP) is a connection-oriented protocol, which means a connection is established and maintained until the application programs at each end have finished exchanging messages. It determines how to break application data into packets that networks can deliver, sends packets to and accepts packets from the network layer, manages flow control and handles retransmission of dropped or garbled packets and acknowledges all packets that arrive. In the Open Systems Interconnection (OSI) communication model, TCP covers parts of Layer 4, the transport layer, and parts of Layer 5, the session layer. This process of error detection, in which TCP retransmits and reorders packets after they arrive, can introduce latency in a TCP stream. 

   When a web server sends an HTML file to a client, it uses the hypertext transfer protocol (HTTP) to do so. The HTTP program layer asks the TCP layer to set up the connection and send the file. The TCP stack divides the file into data packets, numbers them and then forwards them individually to the IP layer for delivery. Although each packet in the transmission has the same source and destination IP address, packets may be sent along multiple routes. The TCP program layer in the client computer waits until all packets have arrived. It then acknowledges those it receives and asks for the retransmission of any it does not, based on missing packet numbers. The TCP layer then assembles the packets into a file and delivers the file to the receiving application. [Explanation](https://www.techtarget.com/searchnetworking/definition/TCP)

    UDP is classified as a datagram protocol, or connectionless protocol, because it has no way of detecting whether both applications have finished their back-and-forth communication. Instead of correcting invalid data packets, as TCP does, UDP discards those packets and defers to the application layer for more detailed error detection. Highly time-sensitive applications such as voice over IP (VoIP), streaming video and gaming generally rely on a transport process such as User Datagram Protocol (UDP) because it reduces latency and jitter -- variation in latency -- by not worrying about reordering packets or getting missing data re-transmitted.

* TCP 3 way handshake SYN, SYN-ACK, and ACK - how it works?
![alt txt](/images/handshake-1.png)
* Step 1 (SYN): In the first step, the client wants to establish a connection with a server, so it sends a segment with SYN which informs the server that the client is likely to start communication
* Step 2 (SYN + ACK): Server responds to the client request with SYN-ACK. Acknowledgement(ACK) signifies the response received by the server and SYN signifies the server wants to establish connection with the client since it is a bi-directional channel
* Step 3 (ACK): In the final part client acknowledges the response of the server and they both establish a reliable connection with which they will start the actual data transfer

> Unlike TCP, UDP is an unreliable and connectionless protocol. So, there is no need to establish a connection prior to data transfer. UDP permits packets to be dropped instead of processing delayed packets.

4. What is the difference between network Layer 2 and 3? - Layer 2 works on physical addressing like Mac address (Media Access Control layer) as well as logical layer i.e Logical Link Control layer. Switches work on this layer. Layer 3 works on logical addressing i.e. IP addresses. Router works on Layer 3.

5. What is the difference between layer-4 and layer-7 load balancing?

    A layer 3 load-balancer takes routing decisions based on IP addressing alone (source & destination).

    A layer 4 load-balancer takes routing decision based on IPs and TCP or UDP ports. It has a packet view of the traffic exchanged between the client and a server which means it takes decisions packet by packet. This allows you to redirect traffic based on the ports in use (so port 80/443 for http/https, port 5060 for SIP etc) and so you can have multiple pools of VoiP and web servers and load balance specific flows across the pools. However a layer 4 load balancer can not see the content of the data being passed through it or make routing decisions based on the content itself.

    Layer 7 load balancer operates at the high-level application layer, which deals with the actual content of each message. HTTP is the predominant Layer 7 protocol for website traffic on the Internet. Layer 7 load balancers route network traffic in a much more sophisticated way than Layer 4 load balancers, particularly applicable to TCP-based traffic such as HTTP. A Layer 7 load balancer terminates the network traffic and reads the message within. It can make a load-balancing decision based on the content of the message (the URL or cookie, for example). It then makes a new TCP connection to the selected upstream server (or reuses an existing one, by means of HTTP Keep-alives) and writes the request to the server.

6. What is the difference between TCP vs HTTP?
![alt txt](/images/tcp-vs-http.png)

7. What does TCP/IP do, exactly? And how does it work?
TCP and IP are two separate computer network protocols. IP is the part that obtains the address to which data is sent. TCP is responsible for data delivery once that IP address has been found.

    TCP/IP breaks each message into packets, and those packets are then reassembled on the other end. In fact, each packet could take a different route to the other computer, if the first route is unavailable or congested. TCP/IP divides the different communications tasks into layers. Data goes through individual layers before it is received on the other end. TCP/IP then goes through these layers in reverse order to reassemble the data and to present it to the recipient.

8. What is BGP (Border Gateway Protocol)?  It is the protocol underlying the global routing system of the internet. It manages how packets get routed from network to network through the exchange of routing and reachability information among edge routers.

9. What is an Autonomous System (AS)? Is a set of Internet routable IP prefixes belonging to a network or a collection of networks that are all managed, controlled and supervised by a single entity or organization. [BGP & Autonomous System](https://github.com/abhinabsarkar/networking-basics/blob/main/concepts/bgp-overview.md)

10. What is a DNS server & how it works? DNS resolves domain name to IP Address. It does this using by making a set of recursive DNS requests via Root DNS server, TLD DNS server & Authoritative DNS server. [Video explanation](https://youtu.be/mpQZVYPuDGU?t=157)
