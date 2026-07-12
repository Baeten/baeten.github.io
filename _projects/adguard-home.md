---
layout: page
title: AdGuard Home
description: Network-wide ads & trackers blocking DNS server.
img: assets/img/project-icons/adguardhome-icon.png
importance: 4
category: self-hosting
---

### What is AdGuard Home?
AdGuard Home is a network-wide software for blocking ads and tracking. Once you set it up, it covers all your home devices, and you don't need any client-side software. It operates as a DNS (Domain Name System) sinkhole. When a device on your network requests the IP address for a known ad or tracking domain, AdGuard Home intercepts the request and returns a "null" response, preventing the ad from ever loading.

### The Home Lab Role
Typically deployed alongside your router or on a dedicated Raspberry Pi/container, AdGuard Home becomes the primary DNS server for your entire network. By configuring your router's DHCP settings to hand out AdGuard's IP address for DNS resolution, every phone, smart TV, and computer is instantly protected from malware domains and invasive telemetry without installing a single browser extension.

### Educational Value for IT Students
Understanding DNS is critical for any network engineer. Running AdGuard Home provides hands-on experience with:
- **DNS Resolution:** Learning how queries are forwarded to upstream providers (like Cloudflare or Google) and cached locally.
- **DHCP Configuration:** Understanding how network configurations are dynamically assigned to client devices.
- **Network Security:** Managing blocklists, analyzing query logs, and understanding how modern malware relies on DNS for command-and-control communication.
