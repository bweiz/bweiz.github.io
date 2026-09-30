---
layout: default
title: Projects
permalink: /projects/
---

# Projects

These are the projects that best show how I work across hardware and software boundaries. I care less about staying inside one layer than understanding enough of the whole system to make its behavior explainable, testable, and useful.

## Table of Contents
- [STM32 + FPGA Event Timing](#stm32-fpga-event-timing)
- [Security Dashcam](#security-dashcam)
- [FPGA + Embedded Linux](#fpga-embedded-linux)
- [Ibex RISC-V Validation](#ibex-risc-v-validation)
- [ESP32 Edge Vision](#esp32-edge-vision)
- [MSP430 Options Visualizer](#msp430-options-visualizer)

---

## STM32 + FPGA Event Timing
<a id="stm32-fpga-event-timing"></a>

**Focus:** bare-metal firmware, interrupts, MCU/FPGA integration, clock-domain crossing, event timing, verification  
**Tech:** STM32H723ZG, DE10-Nano, C, CMSIS, OpenOCD, GDB, SystemVerilog  
**Repo:** [STM32_Vision](https://github.com/bweiz/STM32_Vision)

### Goal

Build an event path where an STM32 generates a hardware event and the FPGA captures that event with a timestamp, creating a foundation for deterministic timing and later sensor/vision integration.

### STM32 side

- Brought up an STM32H723 from bare metal using an ARM GCC toolchain, custom startup code, linker script, CMSIS headers, OpenOCD, and GDB.
- Configured GPIO directly through RCC and GPIO registers.
- Configured TIM2 and the NVIC for interrupt-driven timing behavior.
- Used hardware behavior and debugger state to validate bring-up rather than relying only on successful compilation.

### FPGA side

- Synchronized the asynchronous event input into the FPGA clock domain.
- Captured events against a 64-bit running timestamp/counter.
- Buffered captured timestamps in a FIFO.
- Built a SystemVerilog testbench that exercises normal operation and edge cases around event timing, reset, reads, and FIFO behavior.

### What this project is teaching me

The interesting part is the boundary between systems. A pulse that is trivial inside one clock domain becomes a timing and synchronization problem once it crosses into another device. That forces the firmware, digital design, timing assumptions, and verification strategy to agree.

---

## Security Dashcam
<a id="security-dashcam"></a>

**Focus:** multi-camera video, embedded vision, motion-triggered behavior, resource tradeoffs  
**Tech:** Raspberry Pi 5, 2x MIPI CSI cameras, USB UVC camera, Python, OpenCV, Picamera2/libcamera, V4L2, FFmpeg/GStreamer  
**Repo:** [Security-Dash-Camera](https://github.com/bweiz/Security-Dash-Camera)

### Goal

Build the processing subsystem for a practical multi-camera dashcam that could move between lower-compute monitoring and active processing/streaming modes.

### What I built / owned

- Integrated two MIPI cameras and one USB camera on a Raspberry Pi 5.
- Added GPIO-controlled IR lighting for low-light operation.
- Implemented a lightweight motion path using reduced-resolution luminance frames, Gaussian filtering, thresholding, and connected-component analysis.
- Tuned separate day/night motion thresholds around actual camera behavior.
- Built a 720p/10 fps streaming path while balancing camera bandwidth, processing load, and system responsiveness.

### What I learned

Camera systems are a good example of why end-to-end understanding matters. Image quality, bus bandwidth, processing load, latency, lighting, and state transitions all affect the behavior the user sees.

---

## FPGA + Embedded Linux
<a id="fpga-embedded-linux"></a>

**Focus:** RTL, memory-mapped peripherals, Linux drivers, hardware/software integration  
**Tech:** DE10-Nano SoC FPGA, VHDL/RTL, Platform Designer, Avalon-MM style mapping, C, Linux kernel interfaces  
**Repo:** [FPGAS_Classwork](https://github.com/bweiz/FPGAS_Classwork)

### Goal

Build a custom FPGA peripheral and make it usable from Linux, not just demonstrate the RTL in isolation.

### What I built / owned

- Built an RGB PWM/control peripheral in FPGA fabric.
- Exposed control through memory-mapped registers in the SoC address space.
- Integrated the peripheral through Platform Designer.
- Wrote Linux platform/misc-driver code and exposed control through sysfs.
- Used memory-mapped writes and hardware observation to validate the entire path from user space to physical output.

### Why it matters

This project forced me to debug across several layers at once: RTL, address mapping, Linux device binding, driver code, and actual hardware behavior.

---

## Ibex RISC-V Validation
<a id="ibex-risc-v-validation"></a>

**Focus:** processor execution, binaries, memory layout, simulation, low-level validation  
**Tech:** Ibex RISC-V, RV32IMC, GCC toolchain, ELF/disassembly, simulation traces

### What I worked through

- Built and simulated an Ibex simple system.
- Cross-compiled an RV32IMC test program.
- Inspected the ELF and disassembly to connect C-level intent to machine-level execution.
- Traced execution from reset through program termination.
- Worked with RAM and memory-mapped peripheral regions to understand how software interacts with the simulated SoC.

### Why I built it

I wanted a better mental model of what happens after source code is compiled: how instructions are linked into memory, where the processor starts, how peripherals appear in the address space, and how to verify that behavior from traces instead of treating the toolchain as a black box.

---

## ESP32 Edge Vision
<a id="esp32-edge-vision"></a>

**Focus:** firmware bring-up, I2C, device communication, hardware debugging  
**Tech:** XIAO ESP32-S3 Sense, ESP-IDF, Grove Vision AI V2, I2C  
**Repo:** [vision-node-esp32](https://github.com/bweiz/vision-node-esp32)

### Goal

Bring up communication between an ESP32-S3 host and a Grove Vision AI V2 module in layers, starting with proving the physical transport before building higher-level inference behavior.

### Approach

- Structured the project around explicit board configuration, I2C transport, Grove Vision transport, and application metrics.
- Started at the bus level: wiring, GPIO selection, clock rate, expected device address, and actual ACK/NACK behavior.
- Kept higher-level inference parsing out of the first milestone so failures could be isolated instead of hidden by a larger framework.

The project is intentionally unfinished in the useful sense: it documents what is verified, what is assumed, and what still needs hardware-level validation.

---

## MSP430 Options Visualizer
<a id="msp430-options-visualizer"></a>

**Focus:** embedded UI, math, peripheral integration  
**Tech:** MSP430, C, keypad/encoder, LCD, I2C LED bar  
**Repo:** [msp430-black-scholes-visualizer](https://github.com/bweiz/msp430-black-scholes-visualizer)

### Goal

Create a microcontroller-based options pricing deviation visualizer:

- capture user-entered option parameters and market price,
- compute a Black-Scholes theoretical price,
- display the resulting deviation through an LCD and LED bar.

### What I built / owned

- Keypad and rotary-encoder input flow.
- Firmware path from parameter capture through pricing calculation.
- LCD messaging and I2C-controlled LED bar output.

---

## More Work

My GitHub also includes smaller experiments in embedded C, FPGA work, market systems, and systems-level learning:

- [GitHub Profile](https://github.com/bweiz)
- [embedded-C-foundations](https://github.com/bweiz/embedded-C-foundations)
