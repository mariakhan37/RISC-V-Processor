# RISC-V Processor

A fully functional RISC-V processor designed in Verilog HDL and deployed on a Basys-3 FPGA.

---

## What it does

This processor executes a custom RISC-V instruction set. You write programs in assembly, encode them into a `.mem` file, and the processor runs them — outputting results on the Basys-3's 7-segment display and LED bank.

Three programs are included:

### 1. Countdown
Reads a value from switches, displays it on LEDs, and counts down to zero using a function call with proper stack management.

*Waiting for switch input*
<img width="501" alt="Waiting for switch input" src="https://github.com/user-attachments/assets/53364210-873a-428d-9667-cc6acbf8e1ae" />

*Countdown running on 7-segment display*
<img width="465" alt="Countdown execution" src="https://github.com/user-attachments/assets/c1b17709-68a7-4a88-b7a3-7d6a7ba9f384" />

---

### 2. Instruction Demo
Tests SLTI, SRA, and BLT instructions with known values and verifies output on LEDs.

*BLT branch taken — LED output confirms correct result*
<img width="587" alt="BLT instruction" src="https://github.com/user-attachments/assets/8d2cac61-4693-4e2e-94ee-2b4510ee3deb" />

---

### 3. Fibonacci
Generates the first 5 Fibonacci numbers (0, 1, 1, 2, 3) and displays each in binary on the LED bank.

*n=1: output = 0*
<img width="553" alt="Fibonacci 0" src="https://github.com/user-attachments/assets/9174eaac-3c76-4609-901e-7c65dbb45822" />

*n=2: output = 1*
<img width="533" alt="Fibonacci 1" src="https://github.com/user-attachments/assets/0bdcefc8-8fdc-4ace-b810-0a7abeff4922" />

*n=3: output = 1*
<img width="726" height="470" alt="image" src="https://github.com/user-attachments/assets/fc15348a-080a-40e4-90e3-217833a4f4f6" />

*n=4: output = 2*
<img width="533" alt="Fibonacci 1" src="https://github.com/user-attachments/assets/78739827-9c2b-4b9b-b2c6-455da1ad2ba4" />

*n=4: output = 3*
<img width="533" alt="Fibonacci 2" src="https://github.com/user-attachments/assets/c1435e7b-b01a-4751-b4f5-16ea2d84f8e5" />
---

## Supported Instructions

| Type | Instructions |
|------|-------------|
| Arithmetic | ADD, ADDI, SRA, SRAI |
| Memory | LW, SW |
| Comparison | SLTI |
| Branch | BEQ, BLT |
| Jump | JAL, JALR |

---

## Key Modules

| File | Description |
|------|-------------|
| `TopLevelProcessor.v` | Top-level module wiring everything together |
| `TopLevelProcessor_fpga.v` | FPGA wrapper with clock divider and 7-segment display |
| `InstructionMemory.v` | Loads program from `.mem` file at synthesis |
| `SevenSegment.v` | Time-multiplexed 4-digit display driver |
| `project_tb.v` | Testbench for simulation |

---

## How to Run
**On the FPGA (Basys-3):**
1. Set `TopLevelProcessor_fpga.v` as synthesis top
2. Add the constraint file (`.xdc`)
3. Run synthesis → implementation → generate bitstream → program board
4. Flip switches to set input value and observe output on 7-segment display and LEDs

---

## Built with

- Verilog HDL
- Xilinx Vivado 2024
- Basys-3 FPGA (Artix-7)
