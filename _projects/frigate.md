---
layout: page
title: Frigate
description: NVR with realtime local object detection for IP cameras.
img: assets/img/project-icons/frigate-icon.webp
importance: 7
category: self-hosting
mermaid:
  enabled: true
  zoomable: true
---

### What is Frigate?

Frigate is a highly optimized, open-source Network Video Recorder (NVR) built entirely around real-time AI object detection. Traditional, legacy security camera systems rely on pixel-based motion detection—meaning they trigger a recording (and send you an annoying push notification) every time a tree branch sways in the wind, a spider walks across the lens, or a car's headlights sweep across the driveway. 

Frigate completely eliminates false positives by utilizing local machine learning models to analyze video feeds in real-time. Instead of looking for "motion," it looks for specific objects: humans, cars, motorcycles, dogs, cats, or even specific types of packages.

#### Architectural Overview: Local AI Processing

Running machine learning models against multiple 4K video streams at 20 frames per second is incredibly computationally expensive. Frigate solves this by isolating the heavy lifting to dedicated hardware accelerators, specifically the **Google Coral TPU** (Tensor Processing Unit), or via a modern GPU.

```mermaid
graph TD
    subgraph The Physical Environment
        Cam1["Driveway Camera (RTSP)"]
        Cam2["Backyard Camera (RTSP)"]
    end
    
    subgraph Host Server
        subgraph Frigate Container
            FFMPEG["FFmpeg (Hardware Decoding)"]
            Detect["Object Detection Engine"]
            Record["Recording Engine"]
            MQTT["MQTT Client"]
        end
        
        Coral["Google Coral USB TPU"]
        GPU["Intel QuickSync GPU"]
        Disk[("(Surveillance HDD)")]
    end
    
    subgraph Smart Home
        HA["Home Assistant"]
    end

    Cam1 -- "Sub-stream (Low Res)" --> FFMPEG
    Cam1 -- "Main-stream (4K)" --> Record
    Cam2 -- "Sub-stream" --> FFMPEG
    
    FFMPEG -- "Decodes via GPU" --> GPU
    GPU -- "Passes Frames" --> Detect
    
    Detect -- "Runs ML Model" --> Coral
    Coral -- "Returns Coordinates" --> Detect
    
    Detect -. "If Person Detected" .- Record
    Record -- "Writes 4K Video" --> Disk
    
    Detect -- "Publishes Event" --> MQTT
    MQTT -- "Triggers Automation" --> HA
```

To conserve resources, Frigate actually pulls two streams from every camera: a low-resolution stream for the AI to analyze, and a high-resolution 4K stream that is saved directly to disk *only* when the AI detects an object of interest.

---

### The Home Lab Role

Security cameras generate massive amounts of continuous, highly sensitive data. Sending indoor or outdoor video streams to a cloud provider (like Ring or Nest) for analysis presents a massive privacy risk and consumes an enormous amount of internet bandwidth. 

By running Frigate in your home lab:
- **100% Local Privacy:** The video streams never leave your local area network (LAN).
- **No Subscription Fees:** Cloud providers charge monthly fees for object detection and cloud storage. Frigate provides vastly superior detection capabilities completely for free.
- **Event-Driven Security:** Frigate integrates seamlessly with Home Assistant via MQTT. You can create complex automations, such as: *If Frigate detects a 'person' in the 'backyard' zone after 10:00 PM, turn on the floodlights, lock the back door, and cast the camera feed to the living room TV.*

---

### Real-World Deployment Scenarios

The architecture behind Frigate is a perfect microcosm of how enterprise computer vision pipelines are structured in the real world.

1. **Retail Analytics:** Major retailers use identical local-inference pipelines to track customer foot traffic, monitor checkout lines, and detect shoplifting in real-time without sending terabytes of video to the cloud.
2. **Autonomous Vehicles:** The concept of using a TPU to run inference on live camera feeds is exactly how self-driving cars (like Tesla or Waymo) process their surroundings in milliseconds.
3. **Smart Cities:** Traffic management systems use this exact architecture to count vehicles, identify license plates (ALPR), and adjust traffic light timing based on real-time intersection congestion.

---

### Configuration Snippet: Defining Zones and Objects

Configuring Frigate involves defining your cameras, mapping out physical "zones" using X/Y coordinates, and explicitly telling the AI what objects to track.

Here is a snippet from a `frigate.yml` configuration file:

```yaml
mqtt:
  # Connect to the local MQTT broker
  host: 192.168.1.50

detectors:
  # Utilize the Google Coral USB accelerator
  coral:
    type: edgetpu
    device: usb

cameras:
  front_porch:
    ffmpeg:
      inputs:
        # The main 4K stream (saved to disk)
        - path: rtsp://viewer:password@192.168.1.101:554/cam/realmonitor?channel=1&subtype=0
          roles:
            - record
        # The low-res sub-stream (used for AI detection)
        - path: rtsp://viewer:password@192.168.1.101:554/cam/realmonitor?channel=1&subtype=1
          roles:
            - detect
    detect:
      width: 640
      height: 480
      fps: 5
    objects:
      # Only track humans and packages on this camera
      track:
        - person
        - amazon_package
    zones:
      # Define a specific polygon on the camera feed
      steps:
        coordinates: 100,640 100,500 400,500 400,640
    record:
      # Only keep the 4K recording if an object is detected
      events:
        retain:
          default: 14 # Keep for 14 days
```

---

### Educational Value for IT Students

Frigate is a fantastic, capstone-level entry point into practical machine learning and video engineering. Deploying it teaches students:

- **AI Hardware Acceleration:** Students learn the monumental difference between CPU, GPU, and TPU architectures, understanding why dedicated matrix-math processors (like the Google Coral) are required for real-time inference.
- **Video Streaming Protocols:** The project forces a deep dive into RTSP, H.264/H.265 compression algorithms, bitrates, and keyframes. 
- **FFmpeg Mastery:** Students gain hands-on experience with FFmpeg (the industry-standard multimedia framework) to demux, transcode, and route video streams.
- **MQTT Event Busses:** Integrating Frigate with Home Assistant teaches the publish/subscribe messaging pattern, a critical concept in modern microservice architecture.
