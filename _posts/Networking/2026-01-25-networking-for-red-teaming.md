---
title: "Networking 0x01: Python Ping Tool"
date: 2026-01-25 08:00:00 +0530
categories: [Red Teaming, Networking, Testing]
tags: [python, tools]
---

## Introduction

This is a test post to verify code formatting.

## The Code

Here is the Python script. Notice how `import os` is on its own line.

```python
import os

print("Hello World")
hostname = "google.com"
response = os.system("ping -c 1 " + hostname)