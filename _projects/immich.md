---
layout: page
title: Immich
description: High performance self-hosted photo and video management solution.
img: assets/img/project-icons/immich-icon.png
importance: 10
category: self-hosting
---

### What is Immich?
Immich is a high-performance, self-hosted photo and video backup solution explicitly designed as an open-source alternative to Google Photos and Apple iCloud. It features a mobile app that automatically backs up media in the background, a web interface for viewing albums, and advanced machine learning capabilities for facial recognition and semantic search.

### The Home Lab Role
Personal photos are among the most sensitive data a person owns. Entrusting them to Big Tech means surrendering data sovereignty. Immich reclaims that ownership. It runs on your home server, storing original, uncompressed files directly on your local hard drives. It performs all its machine learning tasks—like identifying faces or searching for "dogs at the beach"—entirely locally, ensuring no third party ever scans your memories.

### Educational Value for IT Students
Immich is a complex microservice application, making it a perfect capstone-level deployment. Using it teaches you:
- **Microservice Architectures:** Deploying and managing a stack that includes a PostgreSQL database, a Redis cache, a machine learning container, and a web backend.
- **Data Sovereignty:** Understanding the critical importance of regular 3-2-1 backup strategies when managing irreplaceable user data.
- **Machine Learning Integration:** Seeing how pre-trained computer vision models are integrated into web applications for semantic search and classification.
