---
layout: page
title: Actual Budget
description: A local-first personal finance tool.
img: assets/img/project-icons/actualbudget-icon.png
importance: 11
category: self-hosting
---

### What is Actual Budget?
Actual is a super fast, privacy-focused personal finance and budgeting system built on the principles of zero-based budgeting (where every dollar is assigned a job). It was originally a paid SaaS product that was later open-sourced by its creator, allowing anyone to host the backend sync server for free.

### The Home Lab Role
Financial data is arguably the most sensitive information a user can generate. Cloud-based budgeting apps inherently have access to your spending habits and net worth. By self-hosting the Actual server, you ensure that this data remains strictly within your control. The application utilizes a "local-first" architecture, meaning the web client runs fully in the browser and functions completely offline, syncing with the server only when a connection is available.

### Educational Value for IT Students
Actual Budget is a brilliant case study in modern web application design. Deploying it teaches you:
- **Local-First Architecture:** Understanding how modern apps use IndexedDB and background workers to operate offline and resolve conflict-free syncing (CRDTs).
- **Data Security & Privacy:** Learning why keeping sensitive SQL databases isolated on a private LAN is superior to trusting third-party cloud hosts.
- **SaaS to Open Source:** Observing the architectural changes required to transition a monolithic commercial product into a decentralized, community-driven container.
