---
layout: page
title: Caddy
description: Fast and extensible multi-platform HTTP/1-2-3 web server with automatic HTTPS.
img: assets/img/project-icons/caddy-icon.png
importance: 3
category: self-hosting
---

### What is Caddy?
Caddy is a highly extensible, open-source web server written in Go. Its defining feature is its role as an automated **Reverse Proxy**. It sits at the edge of your network, intercepts incoming web traffic, and seamlessly routes that traffic to the correct internal container based on the domain name requested. Most impressively, Caddy automates the provisioning and renewal of Let's Encrypt SSL/TLS certificates by default.

### The Home Lab Role
When you self-host multiple services (like a blog, a password manager, and a media server), they all typically run on different internal ports (e.g., `8080`, `8443`, `3000`). Memorizing these ports is tedious, and exposing them directly to the internet is a severe security risk. Caddy acts as the singular, secure gateway. It listens on the standard HTTP/HTTPS ports (80/443), secures the connection with encryption, and silently passes the traffic to the correct backend service based on subdomains (e.g., `media.yourdomain.com`).

### Educational Value for IT Students
Configuring a reverse proxy is a mandatory skill for modern web administration. Implementing Caddy teaches you:
- **DNS & Routing:** Understanding how domain names resolve to IP addresses, and how traffic is forwarded through NAT/firewalls to an internal gateway.
- **SSL/TLS Encryption:** Learning the mechanics of HTTPS, certificate authorities (Let's Encrypt), and automated ACME challenges.
- **Web Server Configuration:** Using the `Caddyfile` syntax to define routing rules, proxy headers, and access logs.
