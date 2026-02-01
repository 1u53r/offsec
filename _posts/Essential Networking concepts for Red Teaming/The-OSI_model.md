---
title: "The OSI Model: A Red Teamer's Perspective"
date: 2026-01-31 16:00:00 +0530
categories: [Red Teaming, The OSI Model]
tags: [networking, red-team, basics, osi-model]
---

# The OSI Model: A Red Teamer's Perspective

The **OSI (Open Systems Interconnection) Model** is a conceptual framework used to understand how data travels through a network to reach its destination. While developed for standardization, for a Red Teamer, this model maps out the attack surface.

It consists of 7 layers, ordered from the physical hardware up to the end-user application.

---

## Layer 7: Application Layer
**Function:** Responsible for interfacing with the end-user application. It handles services like authentication, command handling, and request/response logic. This is the layer where the user interacts with the computer.

* **Common Protocols:**
    * **Web:** HTTP, HTTPS
    * **File Transfer:** FTP, TFTP, SFTP
    * **Email:** SMTP, POP3, IMAP
    * **Management:** SSH, Telnet, SNMP
    * **Name Resolution:** DNS (Application logic)

* **Red Team Relevance (Attack Vector):**
    This is where the vast majority of web-based attacks occur. Because this layer handles user input, it is prone to logic flaws.
    * *Attacks:* SQL Injection (SQLi), Cross-Site Scripting (XSS), Command Injection, Credential Stuffing, Business Logic Errors.

---

## Layer 6: Presentation Layer
**Function:** Responsible for "translating" data into an understandable format for the receiver. This includes encryption/decryption, encoding/decoding, and compression. It ensures that the application layer receives data in a readable format.

* **Common Protocols & Formats:**
    * **Encryption:** SSL/TLS (Conceptually), SSH keys
    * **Data Formatting:** ASCII, EBCDIC, JSON, XML
    * **Media:** JPEG, MPEG, GIF

* **Red Team Relevance (Attack Vector):**
    Attacks here focus on how the application interprets data.
    * *Attacks:* Weak cipher downgrades, Malformed data injection (fuzzing), Encoding bypasses (e.g., using different character sets to bypass WAFs).

---

## Layer 5: Session Layer
**Function:** Responsible for establishing, managing, and terminating sessions between communicating services. It ensures that a connection is open long enough to transfer data and then closes it to free resources.

* **Common Protocols:**
    * **RPC:** Remote Procedure Call
    * **NetBIOS:** Network Basic Input/Output System
    * **SMB:** Server Message Block (Session management aspects)
    * **PPTP:** Point-to-Point Tunneling Protocol
    * **SOCKS:** Socket Secure

* **Red Team Relevance (Attack Vector):**
    This layer maintains the "state" of a user. If you can manipulate the session, you can become the user.
    * *Attacks:* Session Hijacking, Session Fixation, SMB Relay attacks, Token theft.

---

## Layer 4: Transport Layer
**Function:** Responsible for the reliable delivery of data and error checking. It ensures data packets reach the specific service (port) on the destination device.

* **Common Protocols:**
    * **TCP:** Transmission Control Protocol (Reliable, connection-oriented)
    * **UDP:** User Datagram Protocol (Fast, connectionless)
    * **SCTP:** Stream Control Transmission Protocol

* **Red Team Relevance (Attack Vector):**
    This is the layer of ports and services. Enumeration happens here.
    * *Attacks:* SYN Flooding (DoS), Port Scanning (Nmap), UDP Amplification attacks.

---

## Layer 3: Network Layer
**Function:** Responsible for logical addressing and routing. It determines the best physical path for data to travel from one network to another.

* **Common Protocols:**
    * **Addressing:** IPv4, IPv6
    * **Control:** ICMP (Ping), IGMP
    * **Security:** IPSec
    * **Routing:** OSPF, BGP, RIP

* **Red Team Relevance (Attack Vector):**
    Attacks here target the flow of traffic across the internet or subnets.
    * *Attacks:* IP Spoofing, Route Injection, ICMP Redirects, Smurf Attacks (DDoS).

---

## Layer 2: Data Link Layer
**Function:** Responsible for the physical addressing (MAC) and delivery of frames to the intended device within the *same* local network (LAN). It handles error detection in the physical transmission.

* **Common Protocols:**
    * **Ethernet:** 802.3
    * **Wireless:** Wi-Fi (802.11)
    * **Resolution:** ARP (Address Resolution Protocol)
    * **Switching:** VLAN (802.1Q), STP (Spanning Tree Protocol)
    * **Discovery:** CDP, LLDP

* **Red Team Relevance (Attack Vector):**
    If you have physical access or are on the same Wi-Fi, you own this layer.
    * *Attacks:* ARP Spoofing (Man-in-the-Middle), MAC Flooding (forcing a switch to act like a hub), VLAN Hopping.

---

## Layer 1: Physical Layer
**Function:** The actual hardware and transmission medium. This layer deals with the flow of raw bits (0s and 1s) over wires, fiber optics, or radio waves.

* **Common Technologies:**
    * **Cables:** Cat6, Fiber Optic, Coaxial
    * **Wireless:** Radio Frequencies (RF), Bluetooth, NFC
    * **Hardware:** Network Interface Cards (NICs), Hubs, Repeaters

* **Red Team Relevance (Attack Vector):**
    The "hands-on" layer.
    * *Attacks:* Wiretapping, Physical Keyloggers, Evil Maid attacks, Signal Jamming.