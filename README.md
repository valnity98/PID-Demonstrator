# PID Demonstrator

> ⚠️ **This project is no longer maintained.** The repository is archived for reference only.

**Custom PCB for a real-time PID control demonstrator based on the STM32F4 microcontroller.**

Developed as part of the Master's course *Simulation and Control* (Mechatronics & Robotics, Frankfurt UAS, SoSe 2025).

---

## PCB Design

Design and layout of the custom PCB that integrates all hardware components on a single board.

### PCB Features

| Block | Components |
|---|---|
| Power management | Powerbank interface, LDO regulators: 12 V, 6.5 V, 5.8 V, 5.1 V |
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
| Top | ![Top layer](PID-Demo%20v103_T.png) |
| Bottom | ![Bottom layer](PID-Demo%20v103_B.png) |

### Schematic

![Schematic](Schaltplan-Demo.png)

### 3D Model

See [`PID-Demo v103.f3z`](PID-Demo%20v103.f3z) (Fusion 360 archive).

---

## References

- DRV8848 datasheet: Texas Instruments SLVSCK4
- INA138 datasheet: Texas Instruments SBOS165

---

## License

Copyright (c) 2026 Mutasem Bader — All Rights Reserved.  
Viewing is permitted. Copying, modifying, or submitting as own work is strictly prohibited.  
See [LICENSE](LICENSE) for details.
