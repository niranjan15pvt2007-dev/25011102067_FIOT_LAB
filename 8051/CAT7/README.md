\# Experiment CAT-7: 16×2 Character LCD Driver Development and Dynamic Display Control



\## 📋 Overview \& Objectives

This repository directory contains the implementation for \*\*Continuous Lab Evaluation-7 (CAT-7)\*\* under the \*25CS2741 Fundamentals of Internet of Things + Lab\* course\[cite: 13]. The objective is to design, develop, and test a low-level, non-blocking Embedded C 4-bit LCD driver for the \*\*AT89S52\*\* microcontroller using the \*\*HD44780\*\* controller specifications, progressing from basic character rendering to real-time dynamic updates and interactive matrix keypad navigation\[cite: 13].



\---



\## 🛠️ Hardware \& Pin Configuration

\* \*\*Microcontroller:\*\* AT89S52 (8051 family)\[cite: 13]

\* \*\*Clock Source:\*\* 11.0592 MHz Crystal Oscillator\[cite: 13]

\* \*\*Display Interface:\*\* 16×2 Character LCD (HD44780 Driver, operating in \*\*4-bit mode\*\*)\[cite: 13, 14]

\* \*\*Input Device:\*\* 4×4 Matrix Keypad (connected to Port 1)\[cite: 13]



\### Pin Mapping Table

| Peripheral Pin | AT89S52 Port Pin | Description |

| :--- | :--- | :--- |

| \*\*RS\*\* (Register Select) | `P2.0` | Selects Instruction Register (0) or Data Register (1)\[cite: 15] |

| \*\*EN\*\* (Enable) | `P2.1` | Strobe signal to latch data/commands into the LCD |

| \*\*D4\*\* | `P2.4` | Data Bit 4 (Lower/Upper Nibble)\[cite: 13, 14] |

| \*\*D5\*\* | `P2.5` | Data Bit 5 (Lower/Upper Nibble)\[cite: 13, 14] |

| \*\*D6\*\* | `P2.6` | Data Bit 6 (Lower/Upper Nibble)\[cite: 13, 14] |

| \*\*D7\*\* | `P2.7` | Data Bit 7 (Lower/Upper Nibble)\[cite: 13, 14] |

| \*\*Keypad Rows\*\* | `P1.0 - P1.3` | Row scanning lines for 4×4 keypad\[cite: 13] |

| \*\*Keypad Columns\*\* | `P1.4 - P1.7` | Column reading lines for 4×4 keypad\[cite: 13] |



\---



\## 📂 Sub-Task Directory Structure \& Implementations



\### 1. `TASK7A\_LCD\_Init\_Display/`

\* \*\*Source File:\*\* `task7a\_lcd.c`

\* \*\*Schematic:\*\* `circuit.png`

\* \*\*Description:\*\* 

&#x20; \* Derives command sequences directly from the HD44780 datasheet to initialize the display in 4-bit, 2-line mode ($5\\times8$ font matrix)\[cite: 13, 15].

&#x20; \* Implements low-level driver primitives: `lcd\_init()`, `lcd\_cmd()`, and `lcd\_data()`\[cite: 13].

&#x20; \* Demonstrates character rendering and string printing across both rows of the 16×2 display\[cite: 13].



\### 2. `TASK7B\_Cursor\_Dynamic\_Update/`

\* \*\*Source File:\*\* `task7b\_lcd.c`

\* \*\*Schematic:\*\* `circuit.png`

\* \*\*Description:\*\* 

&#x20; \* Extends the driver with explicit cursor positioning (`lcd\_goto(row, column)`) and string output (`lcd\_puts`)\[cite: 13].

&#x20; \* Implements `lcd\_print\_number()` to dynamically format and render real-time integer counter values on the screen without flicker\[cite: 13].



\### 3. `TASK7C\_Keypad\_Character\_Movement/`

\* \*\*Source File:\*\* `task7c\_keypad\_lcd.c`

\* \*\*Schematic:\*\* `circuit.png`

\* \*\*Description:\*\* 

&#x20; \* Combines the 4-bit LCD driver with a 4×4 matrix keypad scanning algorithm to create an interactive application\[cite: 13].

&#x20; \* Maps directional controls to specific keys:

&#x20;   \* \*\*Key `2`:\*\* Move Up ($row = 1$)\[cite: 13]

&#x20;   \* \*\*Key `8`:\*\* Move Down ($row = 2$)\[cite: 13]

&#x20;   \* \*\*Key `4`:\*\* Move Left ($col--$)\[cite: 13]

&#x20;   \* \*\*Key `6`:\*\* Move Right ($col++$)\[cite: 13]

&#x20; \* Real-time repositioning of a custom character (`'X'`) across DDRAM addresses.



\---



\## 🚀 Compilation \& Execution Instructions

1\. Open \*\*Keil µVision\*\* and load the respective project target for the desired sub-task.

2\. Ensure the target frequency is configured to \*\*11.0592 MHz\*\* in project settings.

3\. Build the source code (`F7` or click \*\*Build Target\*\*) to generate the `.hex` file.

4\. Flash the `.hex` file onto the AT89S52 development board or simulate it via Wokwi/Proteus using the accompanying `circuit.png` reference diagram.

