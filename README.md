# STM32 DC Motor Control using RC Joystick

> STM32-based embedded motor control system using RC receiver input, PWM generation, Timer Input Capture, and TB6612 motor driver.

---

# Project Overview

This project implements real-time single-direction DC motor speed control using an STM32F407 Discovery board and RC joystick input.

The STM32 reads PWM signals from the RC receiver using Timer Input Capture mode and generates PWM output signals to control the speed of a DC motor through the TB6612 motor driver.

This project demonstrates practical embedded systems concepts including:
- PWM generation
- Timer Input Capture
- GPIO interfacing
- Motor driver interfacing
- Real-time embedded motor control using STM32 HAL

---

# Features

- RC joystick-based motor speed control
- PWM signal generation using STM32 timers
- Timer Input Capture implementation
- TB6612 motor driver interfacing
- Real-time embedded motor control
- STM32 HAL driver programming
- STM32CubeIDE project structure
- Single-direction PWM motor control

---

# Hardware Components

| Component | Description |
|---|---|
| STM32F407VGTx Discovery Board | Main microcontroller |
| TB6612 Motor Driver | DC motor driver |
| RC Transmitter | User joystick control |
| RC Receiver | PWM signal receiver |
| DC Motor | Motor load |
| 12V DC Adapter | Motor power supply |
| Jumper Wires | Hardware connections |

---

# System Block Diagram

```text
RC Transmitter
       ↓
RC Receiver
       ↓
STM32F407 Discovery Board
       ↓
TB6612 Motor Driver
       ↓
DC Motor
```

---

# Exact Hardware Connections

## 1. RC Receiver to STM32

| RC Receiver Pin | STM32 Pin | Peripheral Function |
|---|---|---|
| Signal | PC6 | TIM3_CH1 Input Capture |
| VCC | 5V | Power Supply |
| GND | GND | Common Ground |

### Description

The RC receiver generates PWM pulses according to joystick movement.

STM32 uses:
- TIM3
- Channel 1
- Input Capture Interrupt Mode

to measure pulse width from the RC receiver.

---

# 2. STM32 to TB6612 Motor Driver

| STM32 Pin | TB6612 Pin | Function |
|---|---|---|
| PA15 | PWMA | PWM Speed Control |
| PB0 | AIN1 | Phase / Direction Control |
| GND | GND | Common Ground |

### Timer Mapping

| STM32 Timer | Channel | Purpose |
|---|---|---|
| TIM2 | CH1 | PWM Generation |
| TIM3 | CH1 | RC Input Capture |

### Description

STM32 generates PWM using:
- TIM2
- Channel 1

The PWM duty cycle changes according to joystick position from the RC transmitter.

---

# 3. TB6612 to DC Motor

| TB6612 Pin | Motor Connection |
|---|---|
| A01 | Motor Terminal 1 |
| A02 | Motor Terminal 2 |

---

# 4. Power Supply Connections

| Device | Supply |
|---|---|
| TB6612 VM | 12V DC Adapter |
| STM32F407 Discovery | USB Power |
| RC Receiver | 5V |
| All GND Pins | Common Ground |

---

# Important Notes

- All grounds must be connected together.
- TB6612 motor supply is powered using a 12V DC adapter.
- STM32 and RC receiver share common ground with the motor driver.
- PWM output controls motor speed.
- Current implementation supports single-direction motor control.
- AIN2 and STBY pins are not controlled through STM32 GPIO in the current implementation.

---

# STM32 Peripheral Configuration

| Peripheral | Purpose |
|---|---|
| TIM2 CH1 | PWM Generation |
| TIM3 CH1 | Input Capture |
| GPIO | Motor Control |
| Interrupts | RC Signal Processing |

---

# Timer Configuration

## TIM2 (PWM Generation)

| Parameter | Value |
|---|---|
| Prescaler | 167 |
| Period | 999 |
| PWM Mode | PWM Mode 1 |

### Purpose
Used for:
- Motor speed control
- PWM generation to TB6612

---

## TIM3 (Input Capture)

| Parameter | Value |
|---|---|
| Prescaler | 167 |
| Period | 65535 |
| Input Polarity | Both Edge |

### Purpose
Used for:
- RC PWM signal measurement
- Joystick pulse width calculation

---

# Software Used

- STM32CubeIDE
- STM32CubeMX
- Embedded C
- STM32 HAL Drivers

---

# Working Principle

1. RC transmitter sends joystick commands.
2. RC receiver outputs PWM pulses.
3. STM32 TIM3 Input Capture measures pulse width.
4. Pulse width determines motor speed.
5. TIM2 generates PWM output on PA15.
6. TB6612 drives the DC motor according to PWM duty cycle.

---

# Project Structure

```bash
Core/
├── Inc/
└── Src/

Drivers/

MOTOR_CONTROL_PWM_JOYSTICK.ioc

README.md
```

---

# Applications

- RC vehicle systems
- Robotics
- Embedded motor control
- Industrial automation
- Educational STM32 projects

---

# Learning Outcomes

Through this project, I learned:

- STM32 timer configuration
- PWM generation
- Timer Input Capture
- Interrupt handling
- Motor driver interfacing
- Embedded C programming
- STM32 HAL driver usage
- Real-time embedded systems development

---

# Future Improvements

- Bidirectional motor control
- AIN2 and STBY GPIO integration
- PID speed control
- Encoder feedback integration
- FreeRTOS integration
- OLED display monitoring
- Wireless telemetry

---

# Repository Description

```text
STM32-based DC motor speed control using RC joystick, PWM generation, Timer Input Capture, and TB6612 motor driver.
```

---

# Recommended GitHub Topics

```text
stm32
stm32f4
embedded-systems
motor-control
pwm
timer-input-capture
embedded-c
tb6612
rc-control
hal-drivers
```

---

# Author

## Om Manekar
ECE Student | Embedded Systems Enthusiast

---
