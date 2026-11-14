# Foundations of Internet of Things (FIoT) — Laboratory Assignments

**Continuous Assessment Tasks | CAT 2–CAT 15**

A collection of weekly FIoT laboratory implementations using **8051** and **STM32** microcontrollers.

<p>
  <img src="https://img.shields.io/badge/Platforms-8051%20%7C%20STM32-0052CC?style=for-the-badge" alt="Platforms: 8051 and STM32">
  <img src="https://img.shields.io/badge/Language-Embedded%20C-00599C?style=for-the-badge&logo=c&logoColor=white" alt="Language: Embedded C">
  <img src="https://img.shields.io/badge/Tools-Keil%20%7C%20STM32CubeMX-brightgreen?style=for-the-badge" alt="Tools: Keil and STM32CubeMX">
  <img src="https://img.shields.io/badge/Topics-UART%20%7C%20I2C%20%7C%20Wi--Fi%20%7C%20MQTT-orange?style=for-the-badge" alt="Topics: UART, I2C, Wi-Fi and MQTT">
</p>

---

## About This Repository

This repository contains the programs and supporting files for the **Foundations of Internet of Things (FIoT) Laboratory** continuous assessment tasks.

The assignments are organised into two main folders:

- **`8051/`** — CAT 2 to CAT 7
- **`STM32/`** — CAT 8 to CAT 15

Depending on the task, the folders include Embedded C source files, Keil project files, STM32CubeMX configuration files (`.ioc`), circuit diagrams, task-level README files and other project resources.

## Repository Information

| Field | Details |
|---|---|
| Course | Foundations of Internet of Things (FIoT) Laboratory |
| Student | Niranjan G |
| Registration Number | `25011102067` |
| Programme | B.Tech Computer Science and Engineering (IoT) |
| Platforms | 8051 and STM32 |
| Main Tools | Keil µVision, STM32CubeMX |
| Repository | [25011102067_FIOT_LAB](https://github.com/Niranjan-Gobinath/25011102067_FIOT_LAB) |

## Repository Structure

```text
25011102067_FIOT_LAB/
├── 8051/
│   ├── CAT2/
│   ├── CAT3/
│   ├── CAT4/
│   ├── CAT5/
│   ├── CAT6/
│   └── CAT7/
├── STM32/
│   ├── CAT8/
│   ├── CAT9/
│   ├── CAT10/
│   ├── CAT11/
│   ├── CAT12/
│   ├── CAT13/
│   ├── CAT14/
│   └── CAT15/
└── README.md
```

Each CAT folder may contain separate task folders and its own README with task-specific details.

---

## Assignment Index

### 8051 Microcontroller — CAT 2 to CAT 7

| CAT | Experiment / Main Topic | Key Concepts |
|---|---|---|
| [CAT 2](./8051/CAT2/) | LED Blinking | GPIO, port manipulation, software delay |
| [CAT 3](./8051/CAT3/) | Timer and Button-Based LED Controller | Timers, button input, LED patterns, debouncing |
| [CAT 4](./8051/CAT4/) | Matrix Keypad and 7-Segment Display | Keypad scanning, display interfacing, LED control |
| [CAT 5](./8051/CAT5/) | Timer, PWM and Signal Generation | Timer interrupts, software PWM, square-wave generation |
| [CAT 6](./8051/CAT6/) | UART Serial Communication | Serial transmission, reception and character echo |
| [CAT 7](./8051/CAT7/) | LCD Interfacing and Keypad-Based Movement | 16×2 LCD, 4-bit mode, cursor positioning, keypad input |

### STM32 Microcontrollers — CAT 8 to CAT 15

| CAT | Experiment / Main Topic | Key Concepts |
|---|---|---|
| [CAT 8](./STM32/CAT8/) | GPIO and Switch-Controlled LED | GPIO input/output, button handling, press detection |
| [CAT 9](./STM32/CAT9/) | UART-Based LED Control | UART communication, command reception and processing |
| [CAT 10](./STM32/CAT10/) | STM32–ESP8266 Communication | UART interface, AT commands, Wi-Fi connection |
| [CAT 11](./STM32/CAT11/) | HTTP Web Server | ESP8266 communication, HTTP requests, TCP server |
| [CAT 12](./STM32/CAT12/) | BME280 Sensor Interfacing | I²C communication, temperature, humidity and pressure |
| [CAT 13](./STM32/CAT13/) | MQTT Sensor Data Publishing | BME280, ESP8266, MQTT communication |
| [CAT 14](./STM32/CAT14/) | Cloud MQTT Telemetry | Cloud broker communication, JSON payloads, MQTT topics |
| [CAT 15](./STM32/CAT15/) | ToF Sensor and IoT Dashboard | VL53L0X, I²C, MQTT, Node-RED dashboard |

---

## Tools and Technologies

The tools and technologies used across the assignments include:

- **Programming:** Embedded C
- **8051 development:** Keil µVision with the C51 toolchain
- **STM32 development:** STM32CubeMX, Keil MDK-ARM and STM32 HAL
- **Communication interfaces:** UART and I²C
- **Wireless connectivity:** ESP8266 AT commands
- **IoT messaging:** MQTT
- **Web communication:** HTTP
- **Visualisation:** Node-RED
- **Simulation and circuit documentation:** Proteus and circuit diagrams, where included in the task folders

The exact hardware, software setup and procedure may differ between assignments. Refer to the README inside each CAT folder for task-specific information.

## How to Use This Repository

1. Open the folder for the required microcontroller: `8051/` or `STM32/`.
2. Select the relevant CAT folder.
3. Open its README, if available, to understand the task and required setup.
4. Open the corresponding project in Keil µVision or STM32CubeMX, as applicable.
5. Review the source code and hardware connections before building or running the project.

**Note:** Project files and compiled outputs are included only where available in the respective task folders. Hardware pin connections and configuration details should be checked against the documentation for that particular task.

## Academic Note

This repository is maintained as a record of my FIoT laboratory continuous assessment work. It is intended for academic reference, learning and review.

**Author:** Niranjan G  
**Registration Number:** `25011102067`  
**GitHub:** [@Niranjan-Gobinath](https://github.com/Niranjan-Gobinath)
