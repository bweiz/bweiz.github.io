---
layout: default
title: Projects
---

# Projects

A curated set of my most relevant engineering work. For each project I include: the goal, constraints, architecture, what I built, and links to code + documentation.

## Table of Contents
- [Security Dashcam](#security-dashcam)
- [FPGA + Embedded Linux](#fpga--embedded-linux)
- [MSP430 Options Deviation Visualizer](#msp430-options-visualizer)
- [More Work](#more-work)

---

## Security Dashcam
<a id="security-dashcam"></a>

**Focus:** multi-camera video pipeline, motion-triggered behavior, real-world embedded constraints  
**Tech:** Raspberry Pi 5, MIPI-CSI + USB cameras, Python, Linux tooling, encoding/streaming pipeline  
**Repo:** [Security-Dash-Camera](https://github.com/bweiz/Security-Dash-Camera)

### Goal
Build a practical, vehicle-compatible dashcam system that can:
- record locally at high quality,
- optionally stream to a mobile app when requested,
- handle motion-triggered recording modes reliably.

### Constraints / Requirements (design drivers)
- Multi-camera input (front MIPI, front USB, rear MIPI)
- End-to-end pipeline thinking: capture → process → encode → store/stream
- Latency/bitrate targets for live streaming (project-driven)
- Power-aware “parked mode” concept with motion-triggered escalation

### What I built / owned
- Designed a multi-stage processing flow:
  - lightweight motion check (pre-filter) → verify → full processing mode
- Built prototype scripts for:
  - motion detection logic (frame differencing style)
  - recording-on-motion behavior
  - health/performance logging (e.g., system telemetry)
- Implemented per-camera recording:
  - each camera is saved as a separate video file with camera-identified naming
- Planned/implemented timestamp overlay support for stored footage


### Architecture (high level)
- **Parked Mode:** lowest power approach, then motion verification
- **Full Processing Mode:** continuous recording from 3 cameras + periodic motion checks to decide whether to continue recording
- **Two outputs:** high-quality stream for storage + lower-quality stream for live app streaming (on demand)

### Proof / Artifacts (add as you build them)
- Repo docs: [Architecture / docs folder](https://github.com/bweiz/Security-Dash-Camera/tree/main/docs)
- Scripts: [scripts/](https://github.com/bweiz/Security-Dash-Camera/tree/main/scripts)
- (Optional) Add later:
  - pipeline diagram image: `/assets/img/dashcam_pipeline.png`
  - short demo clip or GIF: `/assets/img/dashcam_demo.gif`

### What I learned
- Designing reliable state transitions matters as much as code (mode switching, timeouts, failure handling)
- Video systems are about tradeoffs: CPU/GPU load, bitrate, latency, quality, and robustness

---

## FPGA + Embedded Linux
<a id="fpga--embedded-linux"></a>

**Focus:** hardware/software co-design, RTL blocks, Linux interfacing, memory-mapped control  
**Tech:** DE10-Nano (SoC FPGA), RTL (VHDL/Verilog), Avalon-MM style mapping, Linux device tree + drivers, C/Python tooling  
**Repo:** [FPGAS_Classwork](https://github.com/bweiz/FPGAS_Classwork)

### Goal
Build FPGA-based peripherals and control paths that feel “real”:
- custom RTL modules accessible from Linux,
- clean register maps,
- drivers/user-space interfaces to prove end-to-end integration.

### What I built / owned
- RTL blocks (ex: PWM-style control, register interfaces)
- Memory-mapped control (Avalon-MM style register reads/writes)
- Linux-side integration approach:
  - device-tree compatible nodes (for binding)
  - driver patterns (platform driver / sysfs / misc device style interfaces)
  - user-space test utilities + scripts

### Why this matters (what it demonstrates)
- I can design the hardware **and** make it usable from software
- I understand practical integration: address maps, driver binding, verification, and documentation

### Proof / Artifacts (add over time)
- Repo: [FPGAS_Classwork](https://github.com/bweiz/FPGAS_Classwork)
- (Optional) Add later:
  - register map screenshot/table
  - short “write register → observe LED behavior” demo video/GIF

---

## MSP430 Options Deviation Visualizer
<a id="msp430-options-visualizer"></a>

**Focus:** embedded UI + math + peripherals integration  
**Tech:** MSP430, keypad/encoder/potentiometer, LCD/LED bar/RGB LED, C firmware

### Goal
Create a microcontroller-based “pricing deviation” visualizer:
- user inputs option parameters + market price,
- firmware computes theoretical price (Black–Scholes based),
- device displays the deviation visually (LED/LCD feedback).

### What I built / owned
- Input system design: keypad + rotary encoder + pot + confirm/reset button
- Compute path: parameter capture → pricing → deviation mapping
- Output/UI: LCD messaging + LED bar + RGB LED to show magnitude/direction

### Proof / Artifacts (add later)
- (Optional) Add:
  - block diagram of UI flow
  - photos of the working prototype
  - short demo GIF/video

---

## More Work
<a id="more-work"></a>

If you want more depth beyond the featured projects:
- [GitHub Profile](https://github.com/bweiz)
- [Security-Dash-Camera](https://github.com/bweiz/Security-Dash-Camera)
- [FPGAS_Classwork](https://github.com/bweiz/FPGAS_Classwork)

