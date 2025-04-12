---
layout: post
title: "Computer Networks"
date: 2025-03-13 00:00:00 +0800
categories: ["Course Notes"] 
tags: Networking
---

This is my personal note that contains the summary of Computer Networks course, from the book "Computer Networking: A Top-Down Approach" by James F. Kurose & Keith W. Ross. 

## Chapters Overview 
1. Computer Networks & Internet 
2. Application Layer 
3. Transport Layer 
4. The Network Layer: Data Plane 
5. The Network Layer: Control Plane 
6. The Link Layer & LAN 
7. Wireless & Mobile Network 
8. Security in Computer Network 

--- 

## Chapter 1 - Computer Networks & Internet 

Overview: 
1.1 Internet  
1.2 Network Edge  
1.3 Network Core  
1.4 Delay, Loss, & Throughput  
1.5 Protocol Layer & Service Model  
1.6 Security  

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

(to be continued...)