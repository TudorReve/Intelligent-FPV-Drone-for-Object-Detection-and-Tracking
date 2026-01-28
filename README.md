# 🚁 FPV Drone + Object Recognition (Raspberry Pi 5 + OAK-D Lite)

A 5-inch FPV drone built from individual components (all soldering + electronic connections done by me), configured and tuned in **Betaflight**.  
To overcome analog VTX quality limits for my objectives, I integrated a **Raspberry Pi 5** and an **OAK-D Lite** camera to stream a **digital video feed** to a laptop.  
I also designed and 3D-printed landing legs for increased ground clearance and a dedicated Raspberry Pi mounting bracket.

On top of the video pipeline, I trained a **YOLO** model on a dedicated dataset to detect **cars** and **people**, and I’m working on **real-time position estimation** for detected objects using drone telemetry (GPS, altitude, camera angle, drone position, gyroscope data).  
Future goal: **automate drone movement** to track detected objects.

---

## 📌 Table of Contents
- [FPV Drone](#-fpv-drone)
  - [Components](#components)
  - [Construction](#construction)
  - [Firmware](#firmware)
- [Object Recognition](#-object-recognition)
  - [Raspberry Pi + Camera](#raspberry-pi--camera)
  - [YOLO Model](#yolo-model)
  - [Distance & Position Estimation](#distance--position-estimation)
- [Roadmap](#-roadmap)
- [Repo Structure](#-repo-structure)

---

# 🚁 FPV Drone

## Components
**Past**
- (ex: Frame, FC, ESC, motors, VTX analog, receiver, antennas, battery, etc.)

**Present**
- 5-inch FPV build
- Analog video transmission (current limitation)
- Added: Raspberry Pi 5 + OAK-D Lite digital feed pipeline
- 3D printed landing legs + RPi mount

**Future**
- (ex: upgraded digital link / better latency/quality, custom telemetry integration, autonomous modes)

➡️ Details: `docs/fpv-drone/components.md`

## Construction
- Full manual soldering and electronic connections
- Mechanical mounting + vibration considerations
- Custom 3D printed parts:
  - Landing legs for ground clearance
  - Raspberry Pi mounting bracket

➡️ Details: `docs/fpv-drone/construction.md`

## Firmware
- Configured and programmed in **Betaflight**
- (ex: receiver setup, modes, rates, PID tuning notes, filters, OSD)

➡️ Details: `docs/fpv-drone/firmware.md`

---

# 🧠 Object Recognition

## Raspberry Pi + Camera
- Raspberry Pi 5 on-board compute
- OAK-D Lite camera
- Digital video transmission to laptop (describe protocol/latency/bandwidth here)
- (optional) telemetry sync plan with video frames

➡️ Details: `docs/object-recognition/rpi-camera.md`

## YOLO Model
- Trained on dedicated dataset for:
  - 🚗 Cars
  - 🧍 People
- Training pipeline + evaluation
- Inference pipeline intended for real-time use

➡️ Details: `docs/object-recognition/yolo-model.md`

## Distance & Position Estimation
Goal: estimate detected object positions in real time using:
- GPS coordinates
- Altitude
- Camera angle
- Drone position
- Gyroscope data

Planned outputs:
- Object geolocation estimate (lat/lon)
- Relative distance + bearing from drone
- Tracking-ready state for autonomous movement

➡️ Details: `docs/object-recognition/distance-estimation.md`

---

## 🛠 Roadmap
- [ ] Improve digital video feed stability/quality (latency + compression)
- [ ] Telemetry ↔ video frame time synchronization
- [ ] YOLO model iteration + dataset expansion
- [ ] Real-time object position estimation
- [ ] Object tracking (Kalman/ByteTrack etc.)
- [ ] Autonomous movement to follow objects (high-level control loop)

---

## 📁 Repo Structure
- `docs/` – documentation (what/how/why)
- `hardware/` – wiring diagrams, STL/CAD
- `firmware/` – Betaflight dumps, configs
- `vision/` – dataset, training, inference
- `scripts/` – helper scripts (logging, conversion, evaluation)
