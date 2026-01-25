---
title: "IP Addressing and Subnet"
date: 2026-01-24 16:00:00 +0530
categories: [Red Teaming, Ip Addressing and Subnet]
tags: [IP Addressing, Subnet, theory, basics]
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
import platform

# Check if we are on Windows or Linux to choose the correct ping flag
param = '-n' if platform.system().lower() == 'windows' else '-c'
hostname = "google.com"

# The command will now work on both your Windows PC and Linux servers
response = os.system(f"ping {param} 1 {hostname}")

if response == 0:
  print(f"{hostname} is up!")
else:
  print(f"{hostname} is down!")
```