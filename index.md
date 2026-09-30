---
layout: default
title: Benton Weizenegger
---

# Benton Weizenegger
Computer Engineer | Embedded Systems | FPGA/RTL | Physical Systems

I like work where software eventually has to make something real happen.

My path has gone from asphalt crews and framing houses to computer engineering, embedded hardware, FPGA work, and production systems. The common thread is learning unfamiliar systems quickly, getting close to how they actually behave, and making them work.

**Links**
- [GitHub](https://github.com/bweiz)
- [LinkedIn](https://www.linkedin.com/in/benton-weizenegger-0246b0175/)
- [Projects](/projects/)
- [Email](mailto:ben.weizenegger@gmail.com)

---

## Featured Engineering Work

### STM32 -> FPGA Event / Timestamp System

A current hardware/software project built around an STM32H723 and DE10-Nano FPGA.

- Bare-metal C on the STM32H723: startup and linker flow, GPIO, timers, interrupts/NVIC, and register-level bring-up using OpenOCD and GDB.
- Event path into the FPGA with clock-domain synchronization, 64-bit timestamping, FIFO buffering, and SystemVerilog testbench validation.
- Built to make timing behavior observable and testable across the MCU/FPGA boundary.

[Repo](https://github.com/bweiz/STM32_Vision) | [Details](/projects/#stm32-fpga-event-timing)

---

### Security Dashcam - Raspberry Pi 5 Multi-Camera System

Senior capstone focused on multi-camera embedded vision and real-world system constraints.

- Raspberry Pi 5 with two MIPI CSI cameras and one USB camera, plus GPIO-controlled IR lighting.
- Motion detection on reduced-resolution luminance frames using filtering and connected components.
- 720p/10 fps streaming path with camera, compute, bandwidth, lighting, and mode-transition tradeoffs.

[Repo](https://github.com/bweiz/Security-Dash-Camera) | [Details](/projects/#security-dashcam)

---

### FPGA + Embedded Linux - DE10-Nano

Hardware/software co-design from RTL through Linux.

- Built a memory-mapped RGB PWM peripheral in FPGA fabric.
- Integrated the peripheral into the SoC address map and wrote a Linux platform/misc driver with sysfs control.
- Debugged across RTL, memory mapping, Linux driver behavior, and physical hardware.

[Repo](https://github.com/bweiz/FPGAS_Classwork) | [Details](/projects/#fpga-embedded-linux)

---

### ESP32-S3 + Edge Vision Bring-Up

Firmware-first bring-up work between an ESP32-S3 and Grove Vision AI V2 module.

- Structured the firmware around explicit board configuration, I2C transport, device transport, and metrics.
- Worked through GPIO, bus configuration, addressing, and I2C response failures rather than hiding the hardware behind a high-level library.

[Repo](https://github.com/bweiz/vision-node-esp32) | [Details](/projects/#esp32-edge-vision)

---

## More Systems Work

### Ibex RISC-V Validation

Built and simulated an Ibex RV32IMC simple system, cross-compiled test software, and inspected ELF layout, disassembly, instruction execution, memory initialization, and memory-mapped peripherals from reset through program termination.

---

## Background

- **B.S. Computer Engineering**, Montana State University - December 2025
- **Lead Lab Assistant, Microprocessor Hardware/Software Systems** - MSP430 assembly/C, UART, I2C, GPIO, and register-level debugging
- Before and during engineering school, worked in **asphalt paving and residential framing**, including equipment operation, crew leadership, and running independent framing work

That background is a big part of how I approach engineering: understand the physical system, learn what I do not know quickly, and debug from evidence instead of assumptions.

---

## Tools I Use

**Languages:** C, C++, Python, Rust, Java, SystemVerilog/VHDL  
**Embedded / Hardware:** STM32, MSP430, ESP32-S3, DE10-Nano, RISC-V, GPIO, UART, I2C, memory-mapped I/O  
**Linux / Debugging:** Linux, OpenOCD, GDB, kernel drivers, Git, tmux, Neovim  
**Imaging:** OpenCV, Picamera2, libcamera, V4L2, FFmpeg, GStreamer

---

## Contact

- [ben.weizenegger@gmail.com](mailto:ben.weizenegger@gmail.com)
- Vancouver, WA
