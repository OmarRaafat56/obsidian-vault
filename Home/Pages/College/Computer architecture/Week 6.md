[[Computer Architecture]]

Obsidian Summary: Week 6
Microarchitecture Fundamentals
#ISA #computer-architecture 
## 1. ISA vs. Microarchitecture

    ISA (Instruction Set Architecture): The abstract "contract" between software and hardware. Includes opcodes, registers, and memory addressing.

    Microarchitecture (uArch): The specific hardware implementation of the ISA.

        Analogy: ISA is the gas pedal/steering wheel; uArch is the engine under the hood.

        Multiple uArchs can implement the same ISA (e.g., Intel i7 vs. AMD Ryzen both run x86).
___

## 2. Design Points & Tradeoffs

Computer architecture is the "science and art" of balancing:

    Performance: Throughput and Latency.

    Cost: Area and complexity.

    Power: Battery life and thermal limits.
___

## 3. Execution Models
Feature	Single-Cycle	Multi-Cycle
CPI	Always 1	Varies by instruction (>1)
Clock Speed	Slow (limited by slowest instruction)	Fast (limited by slowest stage)
Hardware	Simple, but inefficient	Complex (requires FSM/State)
Resources	Everything used at once	Resources reused across cycles