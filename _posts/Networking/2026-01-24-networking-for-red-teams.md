---
title: "Networking 0x01: The OSI Model for Attackers"
date: 2026-01-24 16:00:00 +0530
categories: [Red Teaming, Networking]
tags: [osi-model, theory, basics]
---

## Introduction
To break a network, you must first understand how it is built. In this post, I am exploring the OSI model—not as a network engineer, but as a Red Teamer looking for vulnerabilities at every layer.

## The 7 Layers of Attack
Most people see the OSI model as theory. I see it as an attack surface.

<!-- ![OSI Model Diagram](/assets/img/osi-model-diagram.png) -->
_Figure 1: The standard 7-layer model_

### Layer 1: Physical
* **Concept:** The actual cables and hardware.
* **Attack:** If I can physically touch the server, I own it. (e.g., Plugging in a Rubber Ducky USB).

### Layer 3: Network
* **Concept:** Routing and IP addresses.
* **Attack:** This is where we perform reconnaissance using tools like `ping` to see if a host is alive.

## The Code: Python Ping Scanner
We don't need complex tools to interact with Layer 3. Here is a simple Python script I wrote to check for active hosts:

```python
import os

hostname = "google.com"
# Note: '-c 1' is for Linux/Mac. Use '-n 1' if running on Windows.
response = os.system("ping -c 1 " + hostname)

if response == 0:
  print(f"{hostname} is up!")
else:
  print(f"{hostname} is down!")