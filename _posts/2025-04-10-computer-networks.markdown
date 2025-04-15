---
layout: post
title: "Computer Networks"
date: 2025-03-13 00:00:00 +0800
categories: ["Course Notes"] 
tags: Networking
---

This is my personal note that contains the summary of Computer Networks course, from the book "Computer Networking: A Top-Down Approach" by James F. Kurose & Keith W. Ross. 

## Chapters Overview 
[1. Computer Networks & Internet](##Chapter-1-Computer-Networks-&-Internet)  
[2. Application Layer](##-Chapter-2-Application-Layer)  
3. Transport Layer  
4. The Network Layer: Data Plane  
5. The Network Layer: Control Plane  
6. The Link Layer & LAN  
7. Wireless & Mobile Network  
8. Security in Computer Network  

--- 

## Chapter 1 - Computer Networks & Internet 

**Overview:**  
[1.1 Internet](###1.1-Internet)    
[1.2 Network Edge](###1.2-Network-Edge)  
[1.3 Network Core](###1.3-Network-Core)   
[1.4 Delay, Loss, & Throughput](###1.4-Performance)  
[1.5 Protocol Layer & Service Model](###1.5-Protocol-Layers)  
[1.6 Security](###1.6-Network-Attacks)  
[1.7 History](###1.7-History) 

<details> 
<summary>Read more on Chapter 1</summary>  

### 1.1 Internet 
* Internet is a computer network that interconnects any computing devices (devices can be hosts or end systems).  
[show figure internet]  
* Protocols are the rules to run the internet, rules to send the message (data) and what actions should be taken regarding to that message. It also defines the message's format, the order, the action should be taken on data transmission, and how to give the receipt upon data arrival.

Some definitions:  
* DSL (Digital Subscriber Line): broadband internet connection that uses existing telephone line to transmit data. 
* DSLAM (DSL Access Multiplexer): network device that connects multiple customer DSL using multiplexing. 
* Multiplexing: technique that combines multiple data streams or signals into a signle channel transmission. 
* Demultiplexing (Demux): the opposite of multiplexing.  
* Access Network: Network that connects physically an end system to the first router. 
  1. DSL: PC -> DSL model -> DSLAM -> Router  
  2. Cable: Home -> Coax -> Fiber -> CMTS -> Router 

* Physical Media:
  1. Guided Media: 
     * Twisted pair: reduce interference
     * Coax: shared use
     * Fiber optic: high speed, long distance 
  2. Unguided Media: 
     * Radio: path loss, fade, interference 
     * Satellite: highspeed without DSL

### 1.2 Network Edge 
* Network core is the lowest, edge of the global internet in concept. 
* There are three types of network edge: 1. Residential Access Network, 2. Institutional Access Network, and 3. Mobile Network. 

### 1.3 Network Core 
* In order to send and receive the data, it needs to be send forward (or forwarding), or we also call it switching. 
* The router will look at the table from the packet, then transmit the packet to the destined router.  
[show figure packet table]  
* Forwarding: local action to move the arriving packet to the next router. 
* Routing: global action to determine the source to the destination path taken by packets. 
* In transmission, of course delay and loss of packet can happen. It could be from the mediums (hardware) and the process (software). 

[show figure packet switching vs circuit switching] 

#### Packet Switching
* Packet switching is good for bursty data (sometimes big amount of data, but sometimes none), resource sharing (muliple receivers), and it is simpler (no call setup).  
* Packet switching employs store and forward mechanism -> router must receive the packet bits before it can transmit. Router uses forwarding tables and routing protocols to determine output links (IP adress), and routing protocols for automatic forwarding table configurations. 
* Delay happens when link is busy, loss happens when the buffer is full (congestion).
  * Delay (single link): 2L/R (2 x packet length (bits) / transmission rate (bps)) 
  * Delay (multiple links): N x L/R 
  * if (arrival > transmission rate) -> delay
  * if (packet queue > buffer memory) -> loss, packet thrown

### Networks of Networks
#### ISP (Internet Service Provider)
* Global ISP (tier 1): global reach, backbone of large internet, independent, exchange free. 
* Regional ISP: specific region/ continents. Rely on transita greement with tier 1. 
* Transit ISP: traffic between network, service to other ISP. 

#### IXP (Internet Exchange Point)
* IXP: physical location where different internet network (ISP and content providers) connect and exchange traffic. It is used to avoid long routing through multiple network. It can be a data center. 
[show figure ISPs]  

#### CDN vs CPN 
* CDN (Content Delivery Network): a mechanism of networking to deliver content with better performance by replicating data in many servers. Ex: Amazon, Google, Netflix. 
* CPN (Content Provider Network): Network that creates and distributes content (source) and it may/ maynot using CDN. Ex: Socmed, e-commerce. 

#### Circuit Switching
* No queuing, no loss, resources are allocated (buffers and links), no delay except propagation delay. However, it is so ineficient because many of the links will idle often.  
  
There are two ways to send the data through the link: 
* Frequency Division Multiplexing (FDM): each call allocated its own band of frequency. The maximum data transferred relies on the maximum transmission rate of that frequency band. 
* Time Division Multiplexing (TDM): each call allocated periodic slot, transmit under the rate of frequency band but only during its time slot. Therefore, provide more segmentations.  
[show figure fdm vs tdm]

*Study Case:  
Network with 1Gbps link, each user can send 100mbps when active, with active rate is just 10% of most of the time.  
Q: how many users can use the network with circuit and packet switching?  
A: Circuit switch --> 10 users (1Gbps/100mbps). But for Packet switch --> 35 users. 

### 1.4 Performance 
#### Delay 
* Four delay types: nodal processing, queue, transmission, and propagation delays.  
d<sub>total</sub>=d<sub>proc</sub>+d<sub>queue</sub>+d<sub>trans</sub>+d<sub>prop</sub> ms.   

* d<sub>proc</sub> usually very small, because it's in computing process.  
d<sub>queue</sub> depends on the congestion of router.  
d<sub>trans</sub> = L/R ms (packet length/transmission rate).  
d<sub>prop</sub> = d/s ms (length of physical link/ prop speed(2x10<sup>8</sup> m/s)).
* Traffic intensity (debit) = (L.a)/R mbps ((packet length . ratio of arrival rate) / link bandwidth (trans rate)).

[show figure delay types]

*Study Case:  
10 packets @prop speed = 100m/s, @t = 12ms, link = 100m.   
Q: total delay, if no process or queue delays.  
A: d<sub>total</sub> = d<sub>trans</sub> + d<sub>prop</sub>  
   d<sub>total</sub> = (10packets x 12ms) + (100m / 100m/s) = 120ms + 1s = 1.12s

#### Traceroute 
* The time to reach the destination through the route. 
* Traceroute is used to measure end to end delay by tracing the route for packets 3 roundtrips delay. 

#### Throughput 
* Throughput is the actual amount of data transmitted over network in a time frame (bps). 
* Bandwidth is the theoretical maximum capacity of the transmission. 
* There is an instant throughput, and averaged throughputs. It is limmited by min(Rs (trans server), Rc (server client)) because of the bottleneck (just like water pipe).  
* For example, packets sent in 10 connections @R bps. Each connection throughput = min(Rc, Rs, R/10). Usually, R/N is always bigger. 

### 1.5 Protocol Layers 
* Protocol layers are organized layers of protocols providing services from the layer below, by utilizing modularity. Depends, it can be implemented on software, hardware, or both. It is also called protocol stacks. 
* Data is encapsulated through each layer, usually contains Header and Payload (main body). 
There are five protocol layers in the internet.  
1. Application: Control the sending and receiving messages among distributed system of apps. Supporting the network application. Ex: HTTP, SMTP, DNS <- services. 
2. Transport: transport messages from one process to another. No reliability guarantee (delay and loss). Ex: UDP, TCP (that's why we need TCP). 
3. Network: transfer data from one end device to another. No reliability guarantee. Ex: IP, Routing. 
4. Link: data transfer between neighboring network elements. Ex: Ethernet, Wifi. 
5. Physical: control the sending of bits into links.  
[show figure internet layers]
[show figure source to destination process] 

### 1.6 Network Attacks 
* Attacks that focus on the network: Sniffing, DoS, IP Spoofing. 
* More complete types: 
  * Malware: Virus, worms, ransom, trojan, spyware
  * DoS & DDoS
  * Social Engineering: phising, social engineering  
  * Other: MITM, SQL Injection, Brute force, IP Spoofing
* Defense:  
  1. Authentication: proving identity  
  2. Confidentiality: encryption  
  3. Integrity check: digital signature, prevent data tampering
  4. Access restriction: password on VPN 
  5. Firewall: (Hardware) programmed to detect and mitigate attack. Sit in the network edge and core. Can filter the senders, receivers, and apps. 
* Tools in computer network: traceroute, wireshark 

### 1.7 History 
* 1961: Early packet switching   
* 1972: Inter-networking 
* 1980: New protocol: TCP/IP, SMTP, DNS, IP, 200 hosts
* 1990: IPS, Web, HTTP, messaging app, 50 mil hosts 
* 2005 - present: SDN, 5G, Wifi, Socmed, Smartphones

</details>

---  
---  

## Chapter 2 - Application Layer  
**Overview:**  
[2.1 Principles of Network Application](###2.1-Principles-of-Network-Application)   
[2.2 Web & HTTP](###2.2-Web-&-HTTP)    
[2.3 Email](###2.3-Email-SMTP-(Simple-Mail-Transfer-Protocol))  
[2.4 DNS](###2.4-DNS-(Domain-Name-System))  
[2.5 P2P File Distribution](###2.5-P2P-File-Distribution)  
[2.6 Streaming & Content Distributions](###2.6-Streaming-&-Content-Distributions)  
[2.7 Socket Programming](###2.7-Socket-Programming)  

<details> 
<summary>Read more on Chapter 2</summary>  

### 2.1 Principles of Network Application 

* Client-server architecture: there must be a dedicated server, client not interact with each other directly, fixed server IP. Ex: Web, email, FTP, telnet (remote access protocol). 
* Peer-to-peer architecture: host connects each other, no dedicated server, cheap because no server infrastructure but high ristk on security, performance, and reliability. 
* Socket: interface between application layer and network layer. It is an API for the network application. Messages from process (app layer) must pass through a network using software interface (socket). It is like a door which process send and receive messages. Usually, a socket needs a process address, which is contains 2 information: 
  * Host IP --> host identity (address) (32 bits)
  * Host Port number --> specific receiving process. Webserver: 80, mailserver:25.  
Both IP and Port are also protocols.   
[show figure socket] 

#### Transport Services
* Services (I would say that these are mechanisms): 
  * Reliable data transfer: make sure data is sent to destination correctly. Prevent data loss. Ex: multimedia. 
  * Throughput: bit rate sent per time. 
  * Timing: low delay or latency. 
  * Security: provides encryption, data integrity to prevent tampering, and end point authentication to prove user identity. 

#### Transport Protocol 
1. User Datagram Protocol (UDP):
    * UDP is actually run on the network layer. Does not establish connection before sending data, send data directly without waiting for confirmation (faster because no sending queuing). 
    * Does not guarantee delivery, order, thus it may receive unordered data or loss. Ex: usage on online games, DNS, where speed is more important than reliability. 
    * No overhead: no extra data or process to transmit the actual data. 

2. Transmission Control Protocol (TCP):  
   * Establishes connection before transmission (3 way handshake: init-request-file received). 
   * Guarantees correct, ordered delivery without loss using acknowledgment (ACK) and retransmission (slower). Ex: uses on web browsing (HTTP), FTP, email (SMTP). 
   * ACK (acknowledgment): confirmation of data reception. How? --> TCP sender transmit data segments, set timer and wait for and ACK from receiver. Uses cummulative ACK, so even if asegment is loss, it can wait and retransmit. 
   * Retransmission: resend the segment if the sender did not receive ACK of that segment before timer expires (RTO), loss or damaged assumptions. Retransmission interval (RTO) increased exponentially with each subsequent retransmission attempt to prevent network congestion.
   * Both TCP and UDP can't gurarantee throughput and timing.    
   [show tabel UDP vs TCP]

3. Transport Layer Security (TLS): 
   * Cryptographic protocol that provides secure communication. Goal: encrypt data, authenticate, integrity (untampering). Established over TCP. 
4. QUIC: 
   * Built upon UDP. Capble of ACK from discontinued packets, efficient for loss recovery. 
   * Flexible method & algorithm to implement cryptography. 
   [show figure TLS & QUIC]

### Application Layer Protocol:  
### 2.2 Web & HTTP 
* HTTP (HyperText Transfer Protocol): application protocol (for WWW), relies on client & server programs to communicate by HTTP messages. 
* Web pages: composed of objects with unique URL (uniform resource locator) include the base HTML and images, CSS, etc. 
* URL: address of the web that contains the protocol, hostname or domain, and path. 
* HTTP uses TCP. Clients initiate TCP connections with a server to exchange HTTP message. Once connected, browser and server process access TCP using client's socket interface. 
* HTTP is stateless protocol, meaning that server do not store client's previous request (each request each link/ connection). 
* Persistent vs Non-persistent Connection
  * Non-persistent: create new connection for each request. Ex: HTTP
  * Persistent: multiple objects sent over the same connection, efficient HTTP1.  
  * RTT (round trip time): tune for a packet to round travel. Determined by delays {prop, queue, trans, proc}. 
  * `Total response time: 2RTT+d`. This is the minimum total response time for each request of non-persistent connection. 
* HTTP Message format:  
  * Request message: 
    * Method: GET, POST, PUT, DELETE
    * HTTP Version
    * Header: Host, connection, user, language 
  * Response message: 
    * Protocol version 
    * Status code 
    * Header & body (payload): connection, date, server, content length, last modified, content type. 
* Cookies: a small text file stored on the user's browser that web uses to remember information (user ID and tracking). Components: Header, File, Backend DB. Usage: authorization, recommendation, session. BUt it also creates concern regarding privacy & identity sales (GDPR - general data protection regulation to handle this issue). 
* Web cache (proxy server): Store copies of objects to reduce the fetching from original server. CDN uses distributed cahcing to localize delivery. 

### 2.3 Email - SMTP (Simple Mail Transfer Protocol)
* SMTP: Principal protocol to send email between server. 
* Basics: 
  1. Sender server initializes the connection using port 25 via TCP. 
  2. Sedner & recipient info read 
  3. Message transmitted  
  4. close (persistent connection)
* Message structure: 
  1. From 
  2. To 
  3. Subject 
  4. Body   

[show figure message structure]  

* MAP (Mail Access Protocol)  
  * Sender --(SMTP, HTTP)--> sender server --(SMTP)--> recipient server --(HTTP, IMAP)--> recipient. 
  * The sender side is push protocol, while the server side is pull protocol. 

### 2.4 DNS (Domain Name System)
* DNS is a query response protocol. It translates humaly hostname to IP address (32 bits). Distributed DB, app layer ptotocol, use UDP port 53. 
* DNS Service: 
  * Hostname aliasing: host with alias name from canonical. Ex: xx.xx.host.com --> x.host.com (alias). 
  * Mail server aliasing: resolves alias hostname to canonical forms and retrieves IP address. Ex: x@x.com --> x@xx.xx.com. 
* DNS distributed hierarchical database:   
[show figure DNS hierarchy]  
* Caching: DNS utilizes query (dynamic address) for caching (better performance).
  [show figure caching]
* DNS server stores record of record (RR). RR = {A, NS, CNAME, MX}. 
  * Type A (alias): maps hostname to IP address. Ex: hostname: geek.com, IP: 192.168.0.7. 
  * Type NS (name server): maps a domain to the hostname of authorative DNS server. Point to the name server where a domain record is registered. Ex: A= geek.com at NS: xx.akamai.com. 
  * Type CNAME (alias hostname): provides canonical name for alias hostname. Ex: hostname = geek.com, alias = serv.geek.com. 
  * Type MX (mail exchanger): maps to canonical name of mail server with alias hostname. Ex: nx=mailgeek.com, domain=geek.com, cname=mail.geek.com, A=m11.geek.com. Multiple MX are allowed. 
* DNS client does query --> 
  * --> MX: canonical name of a mail server.  
  * --> CNAME: canonical name of other server.  
  * DNS Message Format: 
    * Header: query or reply flag, recursion flag, authorative flag.  
    * Body: question, RR, authority, additional sections.   
[show figure dns replies format]  

* Insert record to DNS DB: 
  1. Provide registrar with DNS server name and IP address. 
  2. Enter type NS and type A records for authoritative DNS server into TLD server. Ex: type NS --> utopia.com, dns1.utopia.com. type A --> dns1.utopia.com, 212.212.212.1. 

### 2.5 P2P File Distribution 
* P2P applications: peers request and provide services to the other peers. Dynamic connection, it scales with the peers. Ex: Bit Torrent, VoIP (Skype). 
* Time to share message in client-server vs P2P (assume all users download concurrently): 
  * Client server:  
    * Server transmission for N copies of file/ users: t<sub>cs</sub> = N x <sup>F</sup>&frasl;<sub>U</sub>, where F = length, and U = upload speed. 
    * Client download from network: t<sub>cs</sub> >= max(N x <sup>F</sup>&frasl;<sub>U</sub>, <sup>F</sup>&frasl;<sub>d<sub>min</sub></sub>). <-- Max, because the congestion might happens so it be the minimum time, and d<sub>min</sub> because it is the minimum client download rate.  
    [show figure client server]  
  * P2P: 
    * Server transmission (for 1 copy at least): t<sub>p2p</sub> = <sup>F</sup>&frasl;<sub>U</sub>, N = 1. 
    * Client download: <sup>F</sup>&frasl;<sub>d<sub>min</sub></sub>.
    * Client as aggregates must download N x F bits from the network, max upload rate: U + ΣU<sub>i</sub>. Therefore, t<sub>p2p</sub> > max(<sup>F</sup>&frasl;<sub>U</sub>, <sup>F</sup>&frasl;<sub>d<sub>min</sub></sub>, <sup>N.F</sup>&frasl;U + ΣU<sub>i</sub>).  
    [show figure tcs vs tp2p]
* Torrent: set of peer. Actually still need a server as a tracker. How does it work? 
  1. New peer join: it can download with default speed. It will download another chunk needed in network (rare will be high priority). It connects to the neighbor by the tracker. 
  2. Requesting chuncks: a peer asks chunk from peers especially the rare chunk.
  3. Sending chuncks: that peer, send chunks to those peers at highest rate. If the neighbors not receiving the chuncks, re-evaluate peer connection.  

### 2.6 Streaming & Content Distributions 
* Challenges: 
  * Bandwidth varies, congestion may occurs. 
  * Packet loss or delay, means low quality of network. 
  * Jitter, client side buffer needed. 
  * Client interactivity --> change knob timestamp. 
* DASH (Dynamic, Adaptive, Streaming over HTTP): 
  * Server: Video --> chunks --> encoded at different rates --> files --> replicated in CDN --> provide URLs for chunks (manifest). 
  * Client: Estimates server-client bandwidth --> manifest: request chunk (choose max rate, from server). If congestion occurs, change server. 
* Solutions: 
  1. Mega server: single source failure risk, congestion, long distance clients. This solution is just does not scale. 
  2. Distributed CDN: store multiple copies at distributed sites. This solution is better. 

### 2.7 Socket Programming
Socket only provides 2 protocols: TCP and UDP. 
1. UDP:  
   * Create socket on server & client, specify UDP with `SOCK_DGRAM`. 
   * Create message process on the client. Must know the server port and address. 
2. TCP: 
   * Similar to UDP, but, each client server need to create new socket. Need source port number to identify clients. 

</details> 

---  
---  
  
(to be continued...)