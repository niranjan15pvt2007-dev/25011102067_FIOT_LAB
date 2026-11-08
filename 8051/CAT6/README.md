\# Experiment: UART Driver and Serial Debugging



\## Objective

To develop a basic UART driver for the AT89S52 microcontroller, configuring it for 9600-8-N-1 asynchronous serial communication via a USB-to-TTL interface to demonstrate character transmission and interactive echoing using PuTTY\[cite: 11].



\## Sub-Task Organization \& Implementations



\### 1. TASKA\_UART\_Transmission

\* \*\*Description:\*\* Configures Timer 1 in Mode 2 and UART in Mode 1 (`9600-8-N-1`) using an 11.0592 MHz crystal.

\* \*\*Functionality:\*\* Continuously transmits the string `"Hello from 8051"` to a PC terminal via PuTTY\[cite: 11].

\* \*\*Files:\*\* `taska\_uart\_tx.c`, `circuit.png`



\### 2. TASKB\_UART\_Echo

\* \*\*Description:\*\* Makes the serial link interactive by monitoring reception flags.

\* \*\*Functionality:\*\* Receives characters typed into the PuTTY terminal and immediately echoes them back (e.g., typing `ABC123` returns `ABC123`)\[cite: 11, 12, 13].

\* \*\*Files:\*\* `taskb\_uart\_echo.c`, `circuit.png`



\## Hardware Specifications \& Pin Configuration

\* \*\*Microcontroller:\*\* AT89S52 (11.0592 MHz Crystal)\[cite: 11, 13]

\* \*\*Baud Rate:\*\* 9600 bps (Timer 1, Mode 2 auto-reload, `TH1 = 0xFD`)

\* \*\*Serial Pins:\*\* 

&#x20; \* `P3.0 (RXD)` - Connected to USB-to-TTL TX

&#x20; \* `P3.1 (TXD)` - Connected to USB-to-TTL RX

