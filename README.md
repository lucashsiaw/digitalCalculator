# digitalCalculator
# Digital Calculator (Side Project)

This is a digital logic side project that implements a Q4.4 calculator
supporting addition, subtraction, multiplication, and division.

The goal of this project is to turn what I learned in my logic circuit course into practical skills,
and better understand concepts like differences between adder and the operation 
of finite state machines (FSMs).

---

## Overview

- The calculator operates on binary data internally.
- Addition and subtraction are implemented as single-cycle operations.
- Multiplication and division are implemented as multi-cycle operations
  controlled by a finite state machine (FSM).
- A shared adder is reused across all operations to reduce hardware complexity.
- Decimal-to-binary converter for input encoding
- Binary-to-decimal converter for output display
---

## Supported Operations

| Operation | Notes |
|---------|------|
| Addition | Single-cycle using a ripple carry adder |
| Subtraction | Single-cycle using two’s complement |
| Multiplication | Multi-cycle shift-and-add |
| Division | Multi-cycle restoring division |

---

## Architecture

The system is divided into two main parts:

- **Datapath**: registers, shifters, counters, converters, and a shared adder
- **Controller**: an FSM that sequences the operations

Decimal-to-binary and binary-to-decimal converters are included
to support human-readable input and output.

---

## Tools

- Logisim Evolution — datapath and FSM design
- LTspice — carry lookahead adder (CLA) timing analysis

---

## Current Progress

- [ ] 1-bit full adder
- [ ] 4-bit ripple carry adder
- [ ] FSM-controlled multiplication
- [ ] FSM-controlled division
- [ ] CLA timing comparison
# Digital Calculator (Side Project)

A digital logic calculator implemented in Logisim Evolution, which is Q4.4(unsigned) fixed-point arithmetic 
with keypad input and multi-cycle execution control.

This project is a personal side project to turn concepts from my logic circuit course into 
practical circuit design skills, especially datapath design, control (FSM).

# Final Goal:
Core Functions

Fixed-point format: Q4.4

# Operations:
Addition / Subtraction
Multiplication (multi-cycle)
Division (multi-cycle)
Input / Output
input via keypad (decimal digits + operators)
Internal binary computation
Human-friendly output display (binary-to-decimal / display logic)
Hardware Architecture
Datapath
Registers (operand/result)
Shifters
Counter(s)
Shared adder (reused across operations)

High-Level Architecture


# Tools

Logisim Evolution — datapath, control logic, simulation

# Milestones / Progress

## Milestone 1 — Keypad Encoding & Control Decode ✅

18-key keypad input stage (one-hot buttons)
Priority encoder generates a compact 5-bit key code key[4:0]
Decoded into control flags:

isDigit
isAdd, isMinus, isMul, isDiv
isPoint, isBackspace, isEqual, isAC

Verified with LED(s) in Logisim 

Milestone 2 — Number Entry Path (Digit Accumulation) ⏳

Build input buffer / register for the current number

Implement decimal digit accumulation logic:

value = value * 10 + digit (fixed-point handling to be defined)

Define handling of decimal point and backspace

Milestone 3 — Datapath Core (Shared Adder + Registers) ⏳

Operand/result registers

Shared adder/subtractor block

Basic add/sub execution path

Milestone 4 — Multi-cycle MUL (Shift-and-Add) ⏳

Iterative multiply using shifter + shared adder

FSM sequencing and done signaling

Milestone 5 — Multi-cycle DIV (Restoring Division) ⏳

Restoring division datapath

FSM sequencing and done signaling

Milestone 6 — Output Display ⏳

Binary-to-decimal conversion / display interface
