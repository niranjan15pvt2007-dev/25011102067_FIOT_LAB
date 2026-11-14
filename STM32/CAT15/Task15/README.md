# EXPERIMENT 15: IoT Weather Station using STM32, BME280, MQTT, and Node-RED

**Course Code / Title:** Computer Architecture & IoT Laboratory / Foundations of IoT  
**Institution:** Shiv Nadar University  

---

## 1. Objective
To design, implement, and deploy an end-to-end IoT weather monitoring station utilizing an **STM32 Nucleo-F401RE** microcontroller, a **BME280** environmental sensor communicating via I2C, an **ESP8266 Wemos** Wi-Fi module over UART AT commands for MQTT telemetry, and a local **Node-RED** dashboard integrated with the OpenWeather API for real-time comparison, trend analysis, and environmental recommendations.

---

## 2. System Architecture & Flow

The system captures physical environmental parameters locally via the microcontroller and transmits them securely over an MQTT broker to a local dashboard, where they are benchmarked against live meteorological records.

```mermaid
flowchart LR
    A[BME280 Sensor] -- I2C --> B[STM32 Nucleo-F401RE]
    B -- UART AT Commands --> C[Wemos ESP8266]
    C -- Wi-Fi / MQTT Publish --> D[(MQTT Broker)]
    D -- Subscribe --> E[Node-RED Dashboard]
    F[OpenWeather API] -- HTTP (10 min) --> E
    E --> G[Live Comparison & Analytics]

3. Hardware Requirements & Specifications
Component	Specifications / Role
STM32 Nucleo-F401RE	Main processing unit (ARM Cortex-M4 core, 84 MHz)
BME280 Module	High-precision temperature, humidity, and barometric pressure sensor (I2C interface)
Wemos (ESP8266) Wi-Fi Module	Wireless transceiver running Espressif AT firmware (115200 baud)
Peripherals & Interconnections	Breadboard, jumper wires, USB cables for programming and virtual COM debugging

4. Pin Configuration & Wiring Diagram
From (Source)	To (Destination)	Description
BME280 VCC / GND	3.3V / GND	Sensor Power Supply
BME280 SCL	PB6 (D10)	I2C Clock Line
BME280 SDA	PB7 (CN7 pin 21)	I2C Data Line
STM32 PA9 (USART1 TX, D8)	Wemos RX	Serial Communication (TX to RX)
STM32 PA10 (USART1 RX, D2)	Wemos TX	Serial Communication (RX to TX)
Wemos GND	STM32 GND	Common Ground Reference
Wemos Power	5V / 3.3V Pin	Power rail connection
Note: USART2 (PA2/PA3) is dedicated to debug logging via the ST-Link virtual COM port at 115200 baud.

5. Software Requirements & Toolchain
Keil µVision (MDK-ARM): Configured with ARM Compiler 6, Keil::STM32F4xx_DFP, and ARM::CMSIS software packs.

STM32CubeMX: Used for low-level peripheral configuration (if pinout modifications are required).

Node.js (LTS) & Node-RED: Hosting environment for data visualization workflows.

Node-RED Palette: node-red-dashboard (classic UI package served at /ui).

External Services: Free OpenWeather API key (registered via openweathermap.org).

Testing Tools: Serial terminal (PuTTY / Tera Term) and MQTTX client.

6. Implementation & Setup Guide
Step 1: Wi-Fi Module Preparation
Flash the Wemos ESP8266 with standard Espressif AT firmware. Verify operational readiness by opening a serial terminal at 115200 baud, transmitting AT, and confirming an OK response.

Step 2: Firmware Configuration
Open Core/Src/main.c within your workspace and configure the following parameters:

Local Wi-Fi SSID and Password (strictly 2.4 GHz network).

Target MQTT broker endpoint and unique topic identifier (e.g., snu/weather/bme280).

Step 3: Build and Flash
Open the project workspace file MDK-ARM/IOT_project.uvprojx inside Keil µVision.

Navigate to Project → Rebuild all target files (verify zero compilation errors).

Connect the STM32 Nucleo board via USB and press F8 to flash the binary.

Open a serial monitor on the ST-Link COM port (115200 baud, 8N1) and press the hardware reset button to observe initialization sequences.

Step 4: MQTT Verification
Verify telemetry ingestion from a command line utility:

Bash
mosquitto_sub -h broker.emqx.io -t <your-topic>
Expected JSON Payload Structure:

JSON
{"temperature": 28.45, "pressure": 1007.32, "humidity": 62.10}
Step 5: Node-RED Dashboard Configuration
Initialize Node-RED (node-red) and navigate to http://localhost:1880.

Go to Menu → Manage palette → Install and verify node-red-dashboard is active.

Import the workflow file node-red-weather-flow.json.

Configure the STM32 BME280 MQTT node with the matching topic string.

Edit the IoT Weather Station tab environment variables:

OWM_API_KEY: Your personal OpenWeather API key.

OWM_CITY: Target location code (e.g., Chennai,IN).

Click Deploy and open the user interface at http://localhost:1880/ui.

7. Configuration Summary Reference
Setting Category	Target File / Module	Default Parameter
Wi-Fi Credentials	Core/Src/main.c	User-defined SSID / Password
MQTT Broker Endpoint	Core/Src/main.c & Node-RED Node	broker.emqx.io:1883
Publish Frequency	Core/Src/main.c Main Loop	Every ~5 seconds
OpenWeather Parameters	Node-RED Tab Environment	City Code & API Key
Refresh Interval	Node-RED Inject Node	Every 10 minutes

8. Troubleshooting Guide
Symptom / Error	Root Cause Analysis & Corrective Action
No output on serial terminal	Verify correct ST-Link COM port selection and baud rate (115200).
"BME280 NOT DETECTED!"	Check I2C pin wiring (SDA/SCL), power rails, and ensure the module is a true BME280 (BMP280 variants lack humidity registers).
Execution halts after BME280 init	Inspect Wemos AT firmware version, verify RX/TX crossover, and confirm common ground.
Freezes at "MQTT CONNECT packet sent!"	In ESP8266_sendMessage (ESPLib.c), remove conflicting HAL_UART_AbortReceive_IT and HAL_UART_Receive_IT function calls if operating in pure publishing mode.
Dashboard nodes display red dashed warnings	Install missing packages via Node-RED palette manager (node-red-dashboard).
OpenWeather Error 401	API key is inactive or invalid; validate key functionality directly in a browser.

9. Important Notes & Observations
Pressure Delta: The local BME280 reports raw station pressure, whereas meteorological services like OpenWeather report sea-level adjusted pressure, creating a minor numerical offset.

Thermal Footprint: Indoor sensor placement near microcontrollers or warm boards can cause local temperature readings to run slightly higher than ambient outdoor readings reported by OpenWeather.

Public Broker Limitations: The default public broker (broker.emqx.io) is unauthenticated and shared globally. For robust deployments, migrate to a private or secured MQTT broker.

CubeMX Regeneration: Always wrap custom user code block inclusions (#include "bme280.h", #include "ESPLib.h") inside designated USER CODE blocks to prevent auto-generation overwrites.

10. Authors & Project Contributors
Niranjan G 

V VeeraVishvwajith