\# Experiment: Timer-Based LED Pattern Generator and Button Interrupt Controller



\## Objective

To design and implement a register-level GPIO controller on the AT89S52 microcontroller featuring a four-state LED control system driven by push-button inputs using polling delay loops and switch debouncing.



\## Hardware Connections

\* \*\*LED 1 to LED 4:\*\* Connected to Port 1 pins `P1.0` through `P1.3` via 220Ω current-limiting resistors.

\* \*\*Push-Button:\*\* Connected to pin `P3.2` configured as a digital input with a pull-up resistor.



\## Operating Modes

1\. \*\*Initial State (Mode 0):\*\* All LEDs OFF (`0000`).

2\. \*\*Mode 1:\*\* Running LED pattern (`LED1 → LED2 → LED3 → LED4`).

3\. \*\*Mode 2:\*\* Binary counter (`0000` to `1111`).

4\. \*\*Mode 3:\*\* Alternating pattern (`1010 ⇄ 0101`).

5\. \*\*Mode 4:\*\* All-LED flash (`1111 ⇄ 0000`).



\## Files Included

\* `cat3\_led\_modes.c` - Bare-metal Embedded C source file.

\* `circuit.png` - Schematic diagram of the LED array and push-button wiring.

\* `STARTUP.A51` - Standard 8051 startup configuration file.

