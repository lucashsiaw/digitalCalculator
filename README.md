# digitalCalculator
# Digital Calculator (FSM-based, Multi-cycle)

This project documents the step-by-step design of a digital calculator
implemented using digital logic circuits.
The calculator supports multi-cycle multiplication and division using
a finite state machine (FSM), and single-cycle addition and subtraction
using a shared adder.

---

## Project Motivation

I want to turn what I learned in my logic circuit course into practical skills,
and better understand concepts like differences between adder and the operation 
of finite state machines (FSMs).

Key goals:
- Understand how adders work
- Compare Ripple Carry Adder (RCA) and Carry Lookahead Adder (CLA)
- Implement multiplication and division using iterative algorithms
- Design a controller using FSM to manage multi-cycle operations
  in terms of structure and propagation delay

---

## High-Level Architecture

The calculator is divided into two main components:

### 1. Datapath
- Registers for operands and intermediate results
- A shared adder used for:
  - Addition
  - Subtraction (by two’s complement)
  - Multiplication (shift-and-add)
  - Division (restoring division)
- Shifters and counters
- Decimal-to-binary converter for input encoding
- Binary-to-decimal converter for output display

### 2. Controller (FSM)
- Controls the sequence of operations
- Manages multi-cycle execution for multiplication and division
- Selects arithmetic modes (ADD / SUB / MUL / DIV)

---

## Supported Operations

| Operation | Implementation | Cycle Type |
|---------|---------------|------------|
| Addition | Ripple Carry Adder | Single-cycle |
| Subtraction | Adder + 2’s complement | Single-cycle |
| Multiplication | Shift-and-add algorithm | Multi-cycle (FSM) |
| Division | Restoring division algorithm | Multi-cycle (FSM) |

---

## Adder Design Choices

### Ripple Carry Adder (RCA)
- Simple and modular design using cascaded full adders
- Easy to verify and debug
- Used as the baseline adder for the calculator datapath

### Carry Lookahead Adder (CLA)
- Computes carry signals in parallel using propagate/generate logic
- Reduces propagation delay compared to RCA
- Implemented and analyzed separately using LTspice

---

## State Machine Design

The controller is implemented as a finite state machine (FSM).

### Top-Level States
- `IDLE` – waiting for input
- `LOAD` – load operands into registers
- `DISPATCH` – select operation type
- `EXECUTE` – perform arithmetic operation
- `DONE` – output result

### Multiplication Sub-FSM
- `MUL_INIT`
- `MUL_CHECK_BIT`
- `MUL_ADD`
- `MUL_SHIFT`
- `MUL_COUNT`
- `MUL_DONE`

### Division Sub-FSM
- `DIV_INIT`
- `DIV_SHIFT`
- `DIV_SUB`
- `DIV_CHECK`
- `DIV_RESTORE`
- `DIV_COUNT`
- `DIV_DONE`

---

## Tools Used

- **Logisim Evolution**
  - Datapath design
  - FSM-based controller
  - Functional verification
- **LTspice**
  - Carry Lookahead Adder (CLA) implementation
  - Propagation delay and timing analysis

---

## Verification Strategy

- Module-level verification:
  - Full adder truth table validation
  - Adder correctness testing
- System-level verification:
  - Arithmetic test cases (e.g., 3×5, 7−2, 15÷3)
- Timing verification:
  - RCA vs CLA propagation delay comparison in LTspice

---

## Project Structure (Planned)

digitalCalculator/
├── README.md
├── circuits/ # Logisim circuit files (.circ)
├── docs/ # Design notes and FSM descriptions
├── images/ # Circuit diagrams and waveforms
└── ltspice/ # LTspice schematics and simulations

yaml
複製程式碼

---

## Current Status

- [ ] 1-bit Full Adder
- [ ] 4-bit Ripple Carry Adder
- [ ] FSM Controller (Top-Level)
- [ ] Multiplication (Shift-and-Add)
- [ ] Division (Restoring Division)
- [ ] CLA Implementation (LTspice)
- [ ] RCA vs CLA Delay Comparison
