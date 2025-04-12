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

#### Packet Switching
* Packet switching is good for bursty data (sometimes big amount of data, but sometimes none), resource sharing (muliple receivers), and it is simpler (no call setup).  
[show figure packet switching vs circuit switching] 

#### Circuit Switching
* No queuing, no loss, links are allocated, no delay except propagation delay. However, it is so ineficient because many of the links will idle often.  
  
  
There are two ways to send the data through the link: 
* Frequency Data Multiplexing (FDM): each call allocated its own band of frequency. The maximum data transferred relies on the maximum transmission rate of that frequency band. 
* Time Data Multiplexing (TDM): each call allocated periodic slot, transmit under the rate of frequency band but only during its time slot. Therefore, provide more segmentations.  
[show figure fdm vs tdm]

*Study Case
Network with 1Gbps link, each user can send 100mbps when active, with active rate is just 10% of most of the time.  
Q: how many users can use the network with circuit and packet switching?  
A: Circuit switch --> 10 users (1Gbps/100mbps). But for Packet switch --> 35 users. 

### 1.4 Performance 
* Four delay types: nodal processing, queue, transmission, and propagation delays.  
```
$d_{total}=d_{proc}+d_{queue}+d_{trans}+d_{prop}$  
d<sub>total</sub>=d<sub>proc</sub>+d<sub>queue</sub>+d<sub>trans</sub>+d<sub>prop</sub>  
```
$d_{total}=d_{proc}+d_{queue}+d_{trans}+d_{prop}$  
d<sub>total</sub>=d<sub>proc</sub>+d<sub>queue</sub>+d<sub>trans</sub>+d<sub>prop</sub>  

(to be continued...)