---
layout: default
title: Projects
permalink: /projects/
---

# Projects

A curated set of my most relevant engineering work. For each project I include the goal, constraints, architecture, what I built, and links to code + documentation.

## Table of Contents
- [Security Dashcam](#security-dashcam)
- [FPGA + Embedded Linux](#fpga-embedded-linux)
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
  - health/performance logging (system telemetry)
- Implemented per-camera recording:
  - each camera saved as a separate video file with camera-identified naming
- Planned/implemented timestamp overlay support for stored footage

### Architecture (high level)
- **Parked Mode:** lowest power approach, then motion verification
- **Full Processing Mode:** continuous recording from 3 cameras + periodic motion checks to decide whether to continue recording
- **Two outputs:** high-quality stream for storage + lower-quality stream for live app streaming (on demand)

### What I learned
- Designing reliable state transitions matters as much as code (mode switching, timeouts, failure handling)
- Video systems are tradeoffs: CPU/GPU load, bitrate, latency, quality, robustness

---

## FPGA + Embedded Linux
<a id="fpga-embedded-linux"></a>

**Focus:** hardware/software co-design, RTL blocks, Linux interfacing, memory-mapped control  
**Tech:** DE10-Nano (SoC FPGA), RTL (VHDL/Verilog), Avalon-MM mapping, Linux device tree + drivers, C/Python tooling  
**Repo:** [FPGAS_Classwork](https://github.com/bweiz/FPGAS_Classwork)

### Goal
Build FPGA-based peripherals and control paths that feel “real”:
- custom RTL modules accessible from Linux,
- clean register maps,
- drivers/user-space interfaces proving end-to-end integration.

### What I built / owned
- RTL blocks (PWM-style control, register interfaces)
- Memory-mapped control (Avalon-MM style register reads/writes)
- Linux integration:
  - device-tree nodes (binding)
  - platform-driver patterns (sysfs / misc device style)
  - user-space test utilities + scripts

### Why this matters (what it demonstrates)
- I can design the hardware **and** make it usable from software
- I understand integration: address maps, driver binding, verification, documentation

---

## MSP430 Options Deviation Visualizer
<a id="msp430-options-visualizer"></a>

**Focus:** embedded UI + math + peripherals integration  
**Tech:** MSP430, keypad/encoder, LCD + LED bar over I2C, C firmware  
**Repo:** [msp430-black-scholes-visualizer](https://github.com/bweiz/msp430-black-scholes-visualizer)

### Goal
Create a microcontroller-based “pricing deviation” visualizer:
- user inputs option parameters + market price,
- firmware computes theoretical price (Black–Scholes based),
- device displays the deviation visually (LCD + LED bar).

### What I built / owned
- Input system: keypad + rotary encoder
- Compute path: parameter capture → Black–Scholes call price → deviation
- Output/UI: LCD messaging + LED bar mapping (I2C master → I2C slave)

---

## More Work
<a id="more-work"></a>

If you want more depth beyond the featured projects:
- [GitHub Profile](https://github.com/bweiz)
- [Security-Dash-Camera](https://github.com/bweiz/Security-Dash-Camera)
- [FPGAS_Classwork](https://github.com/bweiz/FPGAS_Classwork)
- [msp430-black-scholes-visualizer](https://github.com/bweiz/msp430-black-scholes-visualizer)

