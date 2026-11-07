\# Experiment: Human-Machine Interface using Matrix Keypad, LEDs, and Seven-Segment Display



\## Objective

To design and implement an embedded HMI on the AT89S52 microcontroller where matrix keypad inputs dynamically drive seven-segment visual feedback and specialized LED operating modes\[cite: 5].



\## Hardware Connections

\* \*\*Matrix Keypad:\*\* Connected to Port 3 (`P3`).

\* \*\*Seven-Segment Display:\*\* Connected to Port 2 (`P2`).

\* \*\*LEDs (LED1 - LED4):\*\* Connected to Port 1 pins `P1.0` through `P1.3`.



\## Functional Mapping

\* \*\*Key 1:\*\* LED1 ON | Display `1`\[cite: 5]

\* \*\*Key 2:\*\* LED2 ON | Display `2`\[cite: 5]

\* \*\*Key 3:\*\* LED3 ON | Display `3`\[cite: 5]

\* \*\*Key 4:\*\* LED4 ON | Display `4`\[cite: 5]

\* \*\*Key 5:\*\* Running LED Pattern | Display `5`\[cite: 5]

\* \*\*Key 6:\*\* Alternate LEDs (`1010 ⇄ 0101`) | Display `6`\[cite: 5]

\* \*\*Key 7:\*\* Binary Counter (`0-15`) | Display `7`\[cite: 5]

\* \*\*Key 8:\*\* All LEDs Blink | Display `8`\[cite: 5]

\* \*\*Key 9:\*\* All LEDs OFF | Display `9`\[cite: 5]

\* \*\*Key 0:\*\* Reset System | Display `0`\[cite: 5]



\## Files Included

\* `cat4\_hmi.c` - Bare-metal Embedded C source file with all required functions.

\* `circuit.png` - Circuit schematic diagram.

\* `STARTUP.A51` - Standard 8051 startup configuration file.

