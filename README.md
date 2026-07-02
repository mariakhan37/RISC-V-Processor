RISC-V Processor
A fully functional RISC-V processor designed in Verilog HDL and deployed on a Basys-3 FPGA. 

What it does:
This processor executes a custom RISC-V instruction set. You write programs in assembly, encode them into a .mem file, and the processor runs them — outputting results on the Basys-3's 7-segment display and LED bank.

Three programs are included:
1) Countdown: Reads a value from switches, displays it on LEDs, and counts down to zero using a function call with proper stack management
Waiting for switch input
<img width="501" height="287" alt="image" src="https://github.com/user-attachments/assets/53364210-873a-428d-9667-cc6acbf8e1ae" />

Countdown execution in progress
<img width="465" height="296" alt="image" src="https://github.com/user-attachments/assets/c1b17709-68a7-4a88-b7a3-7d6a7ba9f384" />

Updated countdown output on the 7-segment display
<img width="645" height="376" alt="image" src="https://github.com/user-attachments/assets/a9ec3ccb-6f7d-4162-ae9a-3116a94fd036" />

2) Instruction Demo: Tests SLTI, SRA, and BLT instructions with known values and verifies output on LEDs
    Executing instruction BLT
    <img width="587" height="343" alt="image" src="https://github.com/user-attachments/assets/8d2cac61-4693-4e2e-94ee-2b4510ee3deb" />

3) Fibonacci: Generates the first 6 Fibonacci numbers (0, 1, 1, 2, 3, 5) and displays them in binary on the LED bank
   For n=6 (0,1,1,2,3,5) in binary shown on LEDS
   <img width="553" height="322" alt="image" src="https://github.com/user-attachments/assets/9174eaac-3c76-4609-901e-7c65dbb45822" />
   <img width="670" height="390" alt="image" src="https://github.com/user-attachments/assets/0bdcefc8-8fdc-4ace-b810-0a7abeff4922" />
   <img width="660" height="395" alt="image" src="https://github.com/user-attachments/assets/78739827-9c2b-4b9b-b2c6-455da1ad2ba4" />
   <img width="760" height="450" alt="image" src="https://github.com/user-attachments/assets/c1435e7b-b01a-4751-b4f5-16ea2d84f8e5" />

Supported Instructions

Type        Instructions
Arithmetic     ADD ADDI, SRA, SRAI
Memory         LW, SW
Comparison     SLTI
Branch         BEQ, BLT
Jump           JAL, JALR

Key modules:
TopLevelProcessor.v — top-level module wiring everything together
TopLevelProcessor_fpga.v — FPGA wrapper with clock divider and 7-segment display
InstructionMemory.v — loads program from .mem file
SevenSegment.v — time-multiplexed 4-digit display driver
project_tb.v — testbench for simulation

