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
