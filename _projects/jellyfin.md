---
layout: page
title: Jellyfin
description: The Free Software Media System.
img: assets/img/project-icons/jellyfin-icon.png
importance: 8
category: self-hosting
---

### What is Jellyfin?
Jellyfin is a completely free, volunteer-built media system that puts you in control of managing and streaming your media. It is an alternative to proprietary solutions like Plex or Emby. It organizes your local movies, TV shows, and music into a beautiful Netflix-style interface that can be streamed to web browsers, smart TVs, and mobile devices.

### The Home Lab Role
With streaming services becoming increasingly fragmented and expensive, many users are returning to local media curation. Jellyfin serves as the core media engine of the home lab. Because it does not rely on third-party authentication servers, your media is always accessible on your local network even without internet access. It automatically scrapes metadata (posters, cast lists, synopses) from public databases to enrich the viewing experience.

### Educational Value for IT Students
Deploying a media server touches on several critical aspects of systems administration:
- **Hardware Transcoding:** Learning how to pass through a GPU (like Intel QuickSync or an NVIDIA card) to a container to convert video formats on-the-fly without maxing out the CPU.
- **Bandwidth Management:** Understanding bitrates, video compression algorithms (H.264 vs H.265), and the network requirements for streaming 4K media across a LAN or WAN.
- **Storage Tiering:** Managing massive data pools using arrays like ZFS or Unraid, balancing read/write speeds with redundancy.
