<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=00599C&height=200&section=header&text=RISC-V%20Processor&fontSize=70&fontColor=ffffff&animation=fadeIn" width="100%" />
</div>

<div align="center">
  <h3>32-bit 5-Stage Pipelined RISC-V Processor</h3>
  <h4>RV32I Instruction Set Architecture | Verilog HDL Implementation</h4>
</div>

<div align="center">
  <img src="https://img.shields.io/badge/Status-Completed-success?style=for-the-badge" alt="Status" />
  <img src="https://img.shields.io/badge/Verilog-19A974?style=for-the-badge" alt="Verilog" />
  <img src="https://img.shields.io/badge/RISC--V-283272?style=for-the-badge" alt="RISC-V" />
  <img src="https://img.shields.io/badge/ModelSim-FF6B6B?style=for-the-badge" alt="ModelSim" />
  <img src="https://img.shields.io/badge/RV32I-9C27B0?style=for-the-badge" alt="RV32I" />
  <img src="https://img.shields.io/badge/Academic_Project-1E90FF?style=for-the-badge" alt="Academic" />
</div>

---

## Overview

A complete **32-bit, 5-stage pipelined RISC-V processor** implementing the **RV32I instruction set architecture**, designed and implemented in **Verilog HDL**. The processor features the classic instruction pipeline stages (IF, ID, EX, MEM, WB) with comprehensive hazard detection and forwarding mechanisms to minimize pipeline stalls due to data and control hazards.

This project supports **25+ RISC-V instructions** across all major instruction types and demonstrates real-world CPU architecture concepts including instruction-level parallelism, hazard handling, and branch resolution.

---

## Abstract

This project presents the design and implementation of a 32-bit, 5-stage pipelined RISC-V processor conforming to the RV32I ISA. The processor integrates the classic instruction pipeline stages: Instruction Fetch (IF), Instruction Decode (ID), Execute (EX), Memory Access (MEM), and Write Back (WB). To support efficient instruction-level parallelism, the design includes hazard detection and forwarding mechanisms.

Each pipeline stage is modularized and interconnected using dedicated registers, ensuring clean signal propagation and functional separation. The processor was validated using ModelSim simulation with comprehensive test programs.

---

## Project Highlights

- Complete 5-stage pipelined architecture (IF, ID, EX, MEM, WB)
- Implements 25+ RISC-V instructions across all major types
- Hazard Detection Unit for load-use hazards
- Forwarding Unit for data hazard resolution
- Branch hazard handling with pipeline flush mechanism
- Modular Verilog HDL design with separate components
- ModelSim simulation and waveform verification
- CPI analysis and performance evaluation
- Scalable foundation for advanced CPU features

---

## Pipeline Architecture

### Five Pipeline Stages

| Stage | Name | Function |
|-------|------|----------|
| **IF** | Instruction Fetch | Fetches instruction from memory using PC |
| **ID** | Instruction Decode | Decodes instruction and reads register values |
| **EX** | Execute | Performs ALU operations and computes branch targets |
| **MEM** | Memory Access | Performs load/store operations |
| **WB** | Write Back | Writes results back to register file |

### Pipeline Flow

```
Instruction Memory
        |
        v
[ IF ] --> IF/ID Register
        |
        v
[ ID ] --> ID/EX Register
        |
        v
[ EX ] --> EX/MEM Register
        |
        v
[ MEM ] --> MEM/WB Register
        |
        v
[ WB ]
        |
        v
   Register File
```

---

## Supported Instructions

The processor implements **25+ instructions** across all major RISC-V instruction types:

### R-type (Register-Register)
| Instruction | Description |
|-------------|-------------|
| `add` | Addition |
| `sub` | Subtraction |
| `and` | Bitwise AND |
| `or` | Bitwise OR |
| `xor` | Bitwise XOR |
| `sll` | Shift Left Logical |
| `srl` | Shift Right Logical |
| `sra` | Shift Right Arithmetic |
| `slt` | Set Less Than |

### I-type (Immediate)
| Instruction | Description |
|-------------|-------------|
| `addi` | Add Immediate |
| `ori` | OR Immediate |
| `xori` | XOR Immediate |
| `andi` | AND Immediate |
| `slli` | Shift Left Logical Immediate |
| `srli` | Shift Right Logical Immediate |
| `srai` | Shift Right Arithmetic Immediate |
| `slti` | Set Less Than Immediate |

### Load/Store
| Instruction | Description |
|-------------|-------------|
| `lw` | Load Word |
| `lh` | Load Half-word |
| `lb` | Load Byte |
| `sw` | Store Word |
| `sh` | Store Half-word |
| `sb` | Store Byte |

### Branch and Jump
| Instruction | Description |
|-------------|-------------|
| `beq` | Branch if Equal |
| `bne` | Branch if Not Equal |
| `jal` | Jump and Link |

### U-type (Upper Immediate)
| Instruction | Description |
|-------------|-------------|
| `lui` | Load Upper Immediate |
| `auipc` | Add Upper Immediate to PC |

---

## RISC-V Instruction Formats

| Format | Description | Use Cases |
|--------|-------------|-----------|
| **R-type** | Register-register operations | add, sub, and, or, xor |
| **I-type** | Immediate and load operations | addi, lw, jalr |
| **S-type** | Store operations | sw, sh, sb |
| **B-type** | Conditional branches | beq, bne, blt |
| **U-type** | Upper immediate operations | lui, auipc |
| **J-type** | Jump operations | jal |

---

## Tech Stack

**Hardware Description Language:**
- Verilog HDL

**Simulation Tools:**
- ModelSim (waveform analysis and verification)
- VCD file generation for waveform inspection

**Documentation:**
- Microsoft Word for project report
- Markdown for repository documentation

---

## Project Structure

```
32-bit-5-Stage-Pipelined-RISC-V-Processor/
│
├── Verilog Code               # Complete Verilog HDL implementation
├── Project Report.docx        # Detailed academic report
├── Simulation Waveforms.pdf   # ModelSim waveform analysis
└── README.md                  # Project documentation
```

---

## Key Components

The processor consists of **18+ modular components**:

### Stage 1 (IF)
- **Program Counter (PC)** — Maintains current instruction address
- **PC Adder** — Computes next sequential PC (PC + 4)
- **PC Mux** — Selects between sequential PC or branch target
- **Instruction Memory** — Stores program instructions
- **IF/ID Pipeline Register** — Buffers instruction and PC

### Stage 2 (ID)
- **Register File** — 32 general-purpose registers
- **Control Unit** — Generates control signals from opcode
- **Immediate Generator** — Sign-extends immediate values
- **Hazard Detection Unit** — Detects load-use hazards
- **Hazard Control Mux** — Gates control signals during stalls
- **ID/EX Pipeline Register** — Propagates data to EX stage

### Stage 3 (EX)
- **ALU** — Performs arithmetic and logic operations
- **ALU Control** — Determines ALU operation type
- **ALU Input Muxes** — Handle data forwarding
- **Forwarding Unit** — Resolves data hazards
- **Branch Adder** — Computes branch target address
- **EX/MEM Pipeline Register** — Stores results for MEM stage

### Stage 4 (MEM)
- **Data Memory** — Word-aligned memory for load/store
- **Branch Decision Logic** — Determines branch outcomes
- **MEM/WB Pipeline Register** — Buffers data for write-back

### Stage 5 (WB)
- **Writeback Mux** — Selects between memory data or ALU result
- Connects back to Register File for final write

---

## Hazard Handling

### Data Hazards (RAW — Read After Write)

**Forwarding Unit:**
- Detects matches between source registers in EX stage and destination registers in EX/MEM and MEM/WB stages
- Forwards data to ALU inputs to avoid stalls

**Forwarding Priority:**

| Priority | Source | Forward Signal |
|----------|--------|----------------|
| Highest | EX/MEM stage | `fwd = 2'b10` |
| Lower | MEM/WB stage | `fwd = 2'b01` |
| Default | Register File | `fwd = 2'b00` |

### Load-Use Hazards

**Hazard Detection Unit:**
- Cannot be resolved by forwarding alone
- Detects when next instruction needs data from a load instruction
- Inserts pipeline stall (bubble) for one cycle
- Disables PC update and IF/ID register write

### Control Hazards (Branches)

**Branch Resolution in MEM Stage:**
- Branch outcome determined using zero flag
- If branch taken: pipeline flush triggered
- IF/ID and ID/EX registers cleared
- Prevents incorrect instruction execution

---

## Design Methodology

### Bottom-Up Design Approach

1. **Modular Design** — Each component implemented as standalone module
2. **Stepwise Integration** — Pipeline stages integrated incrementally
3. **Verification at Each Stage** — Individual modules tested before integration
4. **Top-Level Module** — Final integration in `RISCV_top` module

### Verification Strategy

- Comprehensive testbench (`RISCV_top_tb`)
- Clock and reset signal simulation
- Instruction execution monitoring
- VCD waveform generation for ModelSim analysis
- Console output via `$display` statements

---

## Performance Analysis

### Test Program Overview

A comprehensive test program with **29 instructions** was designed to validate:

- ALU operations (R-type and I-type)
- Memory access (load/store)
- Control flow (branches and jumps)
- Forwarding and hazard handling
- Pipeline behavior under various scenarios

### CPI Calculation

| Instruction Type | Count | Cycles per Instruction |
|------------------|-------|------------------------|
| R-type | 13 | 1 |
| I-type | 4 | 1 |
| Load | 2 | 5 |
| Store | 3 | 4 |
| Branch | 4 | 3 |
| Jump | 3 | 1 |

**Total Instructions:** 29  
**Total Clock Cycles:** 38  
**CPI:** 1.31

### Performance Metrics

| Metric | Value |
|--------|-------|
| Total Instructions Executed | 29 |
| Total Clock Cycles | 38 |
| Cycles Per Instruction (CPI) | 1.31 |
| Maximum Frequency | 4 GHz (theoretical) |
| Clock Period | 250 ps |

---

## Test Program Examples

### Basic Arithmetic (R-type)
```assembly
add x13, x16, x25      # x13 = x16 + x25
sub x5, x8, x3         # x5 = x8 - x3
and x1, x2, x3         # x1 = x2 & x3
or x4, x3, x5          # x4 = x3 | x5
xor x4, x3, x5         # x4 = x3 ^ x5
```

### Immediate Operations (I-type)
```assembly
addi x22, x21, 2       # x22 = x21 + 2
ori x9, x8, 3          # x9 = x8 | 3
slli x4, x3, 6         # x4 = x3 << 6
slti x5, x3, 9         # x5 = (x3 < 9) ? 1 : 0
```

### Memory Access (Load/Store)
```assembly
lw x8, 15(x2)          # Load word from memory[x2 + 15]
sw x14, 12(x6)         # Store word x14 to memory[x6 + 12]
lb x9, 5(x3)           # Load byte from memory[x3 + 5]
```

### Control Flow (Branch/Jump)
```assembly
beq x9, x9, 12         # Branch if equal
bne x9, x9, 14         # Branch if not equal
jal x1, 20             # Jump and link
lui x3, 40             # Load upper immediate
auipc x5, 20           # Add upper immediate to PC
```

### Forwarding/Hazard Test
```assembly
add x3, x2, x3         # EX stage produces result
sub x11, x3, x4        # Forwarded EX -> EX
and x12, x11, x5       # Forwarded MEM -> EX
```

---

## Installation and Setup

### Prerequisites

- ModelSim (or any Verilog simulator)
- Text editor or HDL IDE
- Basic understanding of digital design and Verilog HDL

### Running the Simulation

1. Clone the repository:

```bash
git clone https://github.com/MuhammadYasir85a/32-bit-5-Stage-Pipelined-RISC-V-Processor.git
cd 32-bit-5-Stage-Pipelined-RISC-V-Processor
```

2. Open ModelSim and navigate to the project directory

3. Compile the Verilog files:

```
vlog Verilog_Code.v
```

4. Simulate the testbench:

```
vsim RISCV_top_tb
run -all
```

5. View waveforms in ModelSim's waveform viewer

6. Refer to `Simulation Waveforms.pdf` for expected output examples

---

## Key Findings

| Scenario | Verification Result |
|----------|---------------------|
| ALU and Pipeline Flow | R-type execution verified in EX stage |
| Load-Use Hazard | Hazard detected and pipeline stalled correctly |
| Branch Misprediction | Branch target calculated and pipeline flushed |
| Data Forwarding | Operands forwarded successfully from MEM and WB |
| Memory Operations | Load/store operations executed correctly |

---

## Future Enhancements

- Branch prediction implementation (static or dynamic)
- Exception handling and interrupt support
- Control and Status Registers (CSR) support
- Cache integration (L1 instruction and data cache)
- Out-of-order execution
- Support for RV32M (multiplication/division extension)
- Floating-point unit (RV32F extension)
- Multi-core extension
- Performance counter integration
- Debug interface for hardware debugging

---

## Learning Outcomes

Through this project, the following concepts were mastered:

- RISC-V instruction set architecture
- Pipelined processor design principles
- Hazard detection and forwarding techniques
- Verilog HDL programming and best practices
- Hardware simulation using ModelSim
- Waveform analysis and debugging
- CPU performance metrics (CPI, frequency)
- Modular hardware design methodology
- Testbench creation and verification

---

## Documentation

The repository includes comprehensive documentation:

### 1. Project Report.docx
Complete academic report covering:
- Detailed design methodology
- All component descriptions
- Pipeline architecture explanation
- Hazard handling strategies
- Test program analysis
- CPI calculations and performance metrics
- Conclusions and future work

### 2. Simulation Waveforms.pdf
ModelSim simulation waveforms showing:
- Pipeline stage execution
- Signal propagation
- Hazard detection in action
- Branch resolution
- Memory operations

### 3. Verilog Code
Complete implementation of all modules:
- Pipeline stages
- Pipeline registers
- Hazard handling units
- Control logic
- Memory modules

---

## Project Status

**Status:** Completed

All design objectives achieved with successful simulation and verification.

---

## Academic Information

| Field | Detail |
|-------|--------|
| Course | Computer Organization and Architecture |
| Institution | Namal University Mianwali |
| Department | Computer Science |
| Project Type | Academic Hardware Design Project |

---

## Author

**Muhammad Yasir**

Computer Science Undergraduate at Namal University Mianwali  
Aspiring AI and Computer Vision Engineer

<div>
  <a href="https://www.linkedin.com/in/muhammad-yasir-6a9500343/">
    <img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" />
  </a>
  <a href="mailto:muhammadyasir85a@gmail.com">
    <img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" />
  </a>
  <a href="https://github.com/MuhammadYasir85a">
    <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" />
  </a>
</div>

---

## Acknowledgments

- **Namal University Mianwali** for academic support and resources
- **Department of Computer Science** for guidance throughout the project
- **RISC-V International** for the open-source ISA specification
- **ModelSim** team for excellent simulation tools
- Computer architecture textbooks and academic resources

---

## References

- "Computer Organization and Design: The Hardware/Software Interface" by Patterson and Hennessy
- "RISC-V Instruction Set Manual, Volume I: User-Level ISA"
- IEEE papers on pipelined processor design
- RISC-V International official documentation

---

## License

This project is licensed under the **MIT License**.

This is an academic project. The code and documentation are freely available for educational purposes with proper attribution.

---

<div align="center">
  <i>"From RTL to running instructions — a journey through pipelined processor design."</i>
</div>

<br/>

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=00599C&height=100&section=footer" width="100%" />
</div>
