[[Computer Architecture]]

---

# Computer Architecture - Week 2: Combinational Logic

**Instructor:** Dr. Desoky Abdelqawy
**Department:** Computer and Artificial Intelligent Computer Science, Spring 2025
**References:**

* Prof. Onur Mutlu, ETH Zürich, Spring 2023 [Link](https://safari.ethz.ch/digitaltechnik/spring2023/doku.php?id=schedule)
* Prof. Chris Terman, MIT, Spring 2017 [Link](https://ocw.mit.edu/courses/6-004-computation-structures-spring-2017/)

---

## Hardware vs Software

* Understanding both HW & SW improves design and system efficiency.
* The course emphasizes **HW/SW interface** and **microarchitecture**.
* Focus on trade-offs affecting software performance.

---

## Fundamentals of Computing

**Key Components of a Computer:**

1. **Computation** – processing units
2. **Communication** – I/O and data transfer
3. **Storage/Memory** – program and data storage

**Microarchitecture Breakdown:**

* Processing: Control (sequencing) + Datapath
* Memory (program/data)
* Input/Output (I/O)

**Transformation Hierarchy:**
Problem → Algorithm → Program/Language → System SW → HW/SW Interface → Microarchitecture → Logic → Devices → Electrons

---

## Combinational Logic

**Learning Objectives:**

* Transistors and logic gates
* Boolean algebra fundamentals
* Designing combinational logic circuits
* Mapping Boolean equations to hardware

**Types of Systems:**

| System Type     | Examples     | Characteristics                                 |
| --------------- | ------------ | ----------------------------------------------- |
| General Purpose | CPUs, GPUs   | Flexible, easy to program, moderate efficiency  |
| Special Purpose | FPGAs, ASICs | High efficiency, hard to program, task-specific |

**Performance vs. Programming Time:**

* Microprocessors: minutes to program, lower peak performance
* FPGAs: days to program, flexible prototyping
* ASICs: months to program, maximum performance

---

## Transistors

* Computers built from **MOS transistors**: n-type and p-type
* n-type: closes circuit with high voltage
* p-type: closes circuit with low voltage
* Example devices: Intel 4004 (2,300 transistors) → Apple M2 Max (67B transistors)

**MOS Transistor Structure:**

* Gate, Source, Drain
* Combine conductors, insulators, semiconductors

---

## Logic Gates & CMOS Technology

* **Logic gates** implement Boolean functions using MOS transistors.
* **CMOS (Complementary MOS)** uses nMOS + pMOS.

  * pMOS: pulls output high
  * nMOS: pulls output low

**Basic Gates:**

* **NOT (Inverter):** Y = ¬A
* **NAND:** Y = ¬(A ⋅ B)
* **AND / NOR / OR:** Built using combinations of CMOS gates

**General CMOS Structure:**

* Pull-up network (pMOS)
* Pull-down network (nMOS)
* Only one network active at a time to prevent short circuits

**Latency Considerations:**

* Series transistors → slower
* Parallel transistors → faster

**Power Consumption:**

* Dynamic: ( P = C \cdot V^2 \cdot f )
* Static: ( P = V \cdot I_{leakage} )

---

## Boolean Algebra

**Purpose:** Represent and simplify logic functions.

**Operations:**

* AND (⋅), OR (+), NOT (¬)
* Laws: Commutative, Associative, Distributive, Identity, Complement
* DeMorgan’s Law:

  * ¬(A + B) = ¬A ⋅ ¬B
  * ¬(A ⋅ B) = ¬A + ¬B

**Use Cases:**

* Logic simplification
* Automated design (EDA/CAD tools)
* Canonical representations:

  * Sum of Products (SOP)
  * Product of Sums (POS)

---

## Combinational vs Sequential Logic

* **Combinational:** Memoryless, output depends only on current inputs
* **Sequential:** Has memory, output depends on current and past inputs

---

## Moore’s Law & Modern Computing

* Transistor counts double roughly every 2 years.
* Innovations include: smaller transistors, new materials (Hafnium Oxide, Copper), EUV lithography, FinFET, GAA transistors.
* Enables billions of transistors per chip, supporting complex microarchitectures.

---

## Labs

* **Objective:** Build a microprocessor on FPGA
* Hands-on exploration of microprocessor, FPGA, and ASIC design concepts.

---

## Recommended Reading

* Moore, “Cramming more components onto integrated circuits,” *Electronics Magazine*, 1965
* Harris & Harris, Sections 1.6–1.8

---

## Tags

#computer-architecture #week2 #combinational-logic #boolean-algebra #transistors #CMOS #logic-gates #FPGA #ASIC #MooresLaw #hardware-software #digital-design

---

