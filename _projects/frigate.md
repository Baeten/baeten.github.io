---
layout: page
title: Frigate
description: NVR with realtime local object detection for IP cameras.
img: assets/img/project-icons/frigate-icon.webp
importance: 7
category: self-hosting
---

### What is Frigate?
Frigate is a completely open-source and highly optimized Network Video Recorder (NVR) designed specifically for AI object detection. Instead of relying on motion detection algorithms that trigger on every swaying tree branch, Frigate uses local machine learning models (via CPU, GPU, or dedicated Google Coral TPUs) to analyze video feeds in real-time, identifying specific objects like humans, cars, or animals.

### The Home Lab Role
Security cameras generate massive amounts of continuous data. Sending 4K video streams to a cloud provider for analysis is extremely bandwidth-intensive and presents a huge privacy risk. Frigate runs entirely locally. It connects to your existing IP cameras via RTSP (Real Time Streaming Protocol), processes the frames directly on your home lab hardware, and records only when a valid object is detected, saving massive amounts of disk space.

### Educational Value for IT Students
Frigate is a fantastic entry point into practical computer vision. Deploying it teaches you:
- **Local Machine Learning:** Understanding how TensorFlow models run locally on hardware accelerators (like TPUs) to process frames efficiently.
- **Video Streaming Protocols:** Learning about RTSP, FFmpeg, hardware decoding, and bitrates.
- **Event-Driven Security:** Integrating Frigate's MQTT topic broadcasts with Home Assistant to trigger automations (e.g., turning on the porch light only when a *person* is detected).
