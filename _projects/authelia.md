---
layout: page
title: Authelia
description: The Single Sign-On Multi-Factor portal for web apps.
img: assets/img/project-icons/authelia-icon.png
importance: 5
category: self-hosting
---

### What is Authelia?
Authelia is an open-source authentication and authorization server providing Two-Factor Authentication (2FA) and Single Sign-On (SSO) for your applications via a web portal. It acts as a companion for reverse proxies (like Caddy, Nginx, or Traefik) to let them know whether a user should be granted access to a protected resource.

### The Home Lab Role
When you expose internal services to the internet, relying on their built-in login screens (if they even have one) is risky. Authelia allows you to put a secure, unified "front door" in front of your entire home lab. Before a user can even see the login screen for your media server or download client, they must first authenticate with Authelia using a strong password and a time-based one-time password (TOTP) or hardware security key (like a YubiKey).

### Educational Value for IT Students
Identity and Access Management (IAM) is a cornerstone of cybersecurity. Implementing Authelia teaches you:
- **Authentication Flows:** Understanding how Single Sign-On works across multiple distinct web applications using session cookies.
- **Multi-Factor Authentication (MFA):** The mechanics behind TOTP, WebAuthn, and Duo Push notifications.
- **Proxy Middleware:** How to configure a reverse proxy to perform a forward-auth request, securely gating traffic before it reaches the backend service.
