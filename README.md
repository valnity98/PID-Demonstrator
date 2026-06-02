# PID Demonstrator

**Hardware demonstrator for real-time PID control using an STM32F4 microcontroller**

Developed as part of the Master's course *Simulation and Control* (Mechatronics & Robotics, Frankfurt UAS, SoSe 2025). The demonstrator makes the dynamic behaviour of a closed-loop PID controller physically observable in real time — including overshoot, settling time, steady-state error, and the effect of individual gain tuning.

---

## System Overview

```
┌────────────────────────────────────────────────────┐
│                  PID Demonstrator                  │
│                                                    │
│  Setpoint ──► [PID Controller] ──► [DC Motor]      │
│  (Pot)        STM32F4-Discovery    + H-Bridge      │
│                     ▲                   │           │
│                     └─── [Sensor] ◄─────┘           │
│                          (Pot / Encoder)            │
│                                                    │
│  LCD display  ←  angle / speed / error             │
│  Serial port  ←  live data for plotting            │
└────────────────────────────────────────────────────┘
```

### Closed-Loop Components

| Block | Implementation |
|---|---|
| **Actuator** | DC motor — outputs mechanical angle or speed |
| **Sensor** | Potentiometer (position) or encoder (velocity) |
| **Controller** | STM32F4-Discovery running discrete-time PID in real time |
| **Setpoint input** | Potentiometer (manual) |
| **Gain adjustment** | Three dedicated potentiometers for Kp, Ki, Kd |
| **Visualisation** | LCD display + serial output (UART → PC plotter) |
| **Power supply** | Powerbank — fully portable operation |

---

## My Contribution: PCB Design

My primary contribution was the **design and layout of the custom PCB** that integrates all hardware components on a single board, plus a secondary contribution to **PID parameter tuning using the MATLAB PID Tuner**.

### PCB Features

| Block | Components |
|---|---|
| Power management | Powerbank interface, LDO regulators: 12 V, 6 V, 5 V, 3.3 V |
| Motor current sensing | Shunt resistor + INA138 current monitor |
| Motor driver | DRV8848 dual H-bridge |
| Gain potentiometers | Three 10 kΩ trimmers for Kp, Ki, Kd |
| Setpoint potentiometer | One 10 kΩ trimmer |
| LCD interface | 4-bit parallel header |
| MCU interface | Pin header for STM32F4-Discovery board |
| Serial output | UART header for live data streaming |

### PCB Layout

| Layer | Image |
|---|---|
| Top | ![Top layer](PID-Demo%20v92_T.png) |
| Bottom | ![Bottom layer](PID-Demo%20v92_B.png) |

### Schematic

![Schematic](Schaltplan-Demo.png)

### 3D Model

See [`PID-Demo v96.f3z`](PID-Demo%20v96.f3z) (Fusion 360 archive).

---

## PID Tuning

The PID parameters were initially estimated using the **MATLAB PID Tuner** on an identified plant model (step-response identification of the DC motor + load). The resulting gains were then verified and fine-adjusted on the physical hardware by observing the step response on the serial plotter.

---

## Observable Control Effects

| Effect | How to observe |
|---|---|
| Overshoot | Increase Kp — system overshoots setpoint |
| Oscillation | Increase Kd too far — derivative noise amplified |
| Integral windup | Set large reference step, observe slow wind-down |
| Steady-state error | Set Ki = 0 — residual offset remains |
| Settling time | Compare responses with/without derivative term |

---

## References

- Example build inspiration: [YouTube — PID Motor Control Demonstration](https://youtu.be/qKy98Cbcltw?si=HwGLJR-9h6Nvn7Rk)
- MATLAB PID Tuner documentation: [mathworks.com/help/control/ref/pidtuner-app.html](https://www.mathworks.com/help/control/ref/pidtuner-app.html)
- DRV8848 datasheet: Texas Instruments SLVSCK4
- INA138 datasheet: Texas Instruments SBOS165

---

## Contributors

- Mutasem Bader — PCB design, PID parameter tuning
- *Team members — STM32 firmware, system integration*
