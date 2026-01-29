---
title: "IP Addressing and Subnet"
date: 2026-01-24 16:00:00 +0530
categories: [Red Teaming, Ip Addressing and Subnet]
tags: [IP Addressing, Subnet, theory, basics]
---

## Introduction
To break a network, We must first understand how it is built. In this post, I am exploring some very first important concepts of networking, but as a Red Teamer perspective.

## IP Addressing & Subnetting
No network can exist without IP address and subnet masks, and that is why is the one of the most important networking topics to learn to become a master in red teaming.

As an aspiring Red Teamer, I realized that I can't just run tools blindly. I need to understand the network I'm attacking. If I don't know the difference between a `/24` and a `/23`, I might end up attacking the wrong target or would miss the target, or even worst target the network for which i am not autorised. Causing a law suit agains't me.


### IP ADDRESSING

* **What is an IP Address :** An IP address is a unique 32 bit number assigned to every device on the netowrk, be it small network or a huge network which uses internet protocol for communication.

  * **Example :** 172.217.19.164 (Google.com)

* **The Anatomy Of An IP Address :**  An IP Address is build wth two portions.
  * **Network Portion :** This portion are the initial bits of the IP address which helps the router to reoute traffic to correct network. This portion also helps to identify the network a device belongs to. This is like a street for traffic that helps which street to go to find the reciver of that traffic.

    ![Network Diagram](/assets/img/Example1.jpeg)

  * **Host Portion :** This portion is the host portion which tells the traffic where exactly it is at that street(Network Portion). These are the very last bits of an IP Address.

    ![Network Diagram](/assets/img/Example2.jpeg)

* **Eaxmple :** Depending on the <b>Subnet Mask </b>, the first part (192.168.1) is likely the street, and the last part (.10) is the specific house.

### SUBNET MASK
An IP Adderss alone won't help us to know the size of the network or what are the host could be available on this network, that's were <b>SUBNET MASK </b> comes in. It is like a fence around the city, which contains many hosts (houses) inside.

We use <b>CIDR</b> (Classless Inter-Domain Routing) notation because it's faster. This is the /XX number at the end of an IP.

    /24 (255.255.255.0): The standard LAN. 254 usable hosts.

    /16 (255.255.0.0): A large campus network. 65,000+ hosts.

* The Red Team "Magic Number" Trick 

  * Calculating ranges in binary is too slow. I learned the Magic Number method to find the range of my target quickly.

        Formula:  256 - (Subnet Mask Value) = Block Size

* EXAMPLE :  