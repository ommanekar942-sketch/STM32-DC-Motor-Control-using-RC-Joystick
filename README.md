# STM32 DC Motor Control using RC Joystick

A real-time embedded systems project using STM32 to control the speed and direction of a DC motor using an RC transmitter and receiver.

This project demonstrates PWM generation, Timer Input Capture, motor driver interfacing, and real-time motor control using STM32 HAL drivers and STM32CubeIDE.

---

# Project Overview

The main objective of this project is to:

- Read PWM signals from an RC receiver
- Control DC motor speed using PWM
- Control motor direction using GPIO
- Interface STM32 with the TB6612 motor driver
- Implement real-time embedded motor control

The joystick movement from the RC transmitter controls the motor speed and direction dynamically.

---

# Components Used

- STM32 Development Board
- TB6612 Motor Driver
- RC Transmitter
- RC Receiver
- DC Motor
- 12V DC Adapter
- Jumper Wires

---

# System Block Diagram

RC Transmitter → RC Receiver → STM32 → TB6612 Motor Driver → DC Motor

---

# Hardware Connections

## 1. RC Receiver to STM32

| RC Receiver Pin | STM32 Pin | Description |
|---|---|---|
| Signal | Timer Input Capture Pin | PWM signal from receiver |
| VCC | 5V | Power supply |
| GND | GND | Common ground |

The STM32 reads PWM pulse widths from the RC receiver using Timer Input Capture mode.

---

## 2. STM32 to TB6612 Motor Driver

| STM32 Pin | TB6612 Pin | Function |
|---|---|---|
| PWM Output Pin | PWMA | Motor speed control |
| GPIO Output | AIN1 | Motor direction control |
| GPIO Output | AIN2 | Motor direction control |
| GPIO Output | STBY | Enable driver |
| GND | GND | Common ground |

PWM is generated using STM32 timers to control motor speed.

---

## 3. TB6612 to DC Motor

| TB6612 Pin | Motor Connection |
|---|---|
| A01 | Motor Terminal 1 |
| A02 | Motor Terminal 2 |

---

## 4. Power Supply Connections

| Power Source | Connection |
|---|---|
| 12V DC Adapter | TB6612 VM Pin |
| GND | Common Ground |
| STM32 | USB / External 5V |

### Important Notes

- All grounds must be connected together.
- TB6612 motor supply is powered using a 12V DC adapter.
- STM32 and RC receiver share common ground with the motor driver.

---

# STM32 Peripherals Used

- GPIO
- TIM PWM Mode
- TIM Input Capture Mode
- Interrupts

---

# Software Used

- STM32CubeIDE
- STM32CubeMX
- Embedded C
- STM32 HAL Drivers

---

# Working Principle

1. The RC transmitter sends control signals.
2. The RC receiver outputs PWM signals.
3. STM32 measures pulse width using Timer Input Capture.
4. Based on joystick position:
   - Motor speed is controlled using PWM
   - Motor direction is controlled using GPIO pins
5. TB6612 drives the DC motor accordingly.

---

# Features

- Real-time motor speed control
- Direction control
- PWM-based motor driving
- RC joystick interface
- STM32 timer applications
- Embedded C implementation using HAL drivers

---
