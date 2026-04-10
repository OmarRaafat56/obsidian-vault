[[Computer Architecture]]


---

# Computer Architecture Week 4 – Hardware Description Languages & Verilog

**Instructor:** Dr. Desoky Abdelqawy
**Department:** Faculty of Computer and Artificial Intelligence, Computer Science
**Semester:** Spring 2025

**Sources:**

* Prof. Onur Mutlu, ETH Zürich, Spring 2023 – [Link](https://safari.ethz.ch/digitaltechnik/spring2023/doku.php?id=schedule)
* Prof. Chris Terman, MIT, Spring 2017 – [Link](https://ocw.mit.edu/courses/6-004-computation-structures-spring-2017/)

---

## Agenda

* Hardware Description Languages (HDLs)
* Implementing Combinational Logic (Verilog)
* Implementing Sequential Logic (Verilog)
* Slides provide tutorial material useful for labs

---

## Readings (This Week)

* **HDLs and Verilog:** H&H Chapter 4 (full)
* **Timing and Verification:** H&H 2.9, 3.5, start of Chapter 5

---

## HDLs & Verilog Overview

### Historical Chip Examples (Transistor Growth)

| Year | Chip            | Specs                                                              | Transistors |
| ---- | --------------- | ------------------------------------------------------------------ | ----------- |
| 2017 | Intel Kaby Lake | 4 cores, 8 threads, 14–19 stage pipeline, 3.9 GHz                  | 1.75B       |
| 2021 | Apple M1        | 4 High-Perf + 4 Efficient cores, 8-core GPU, 16-core Neural Engine | 16B         |
| 2022 | Apple M1 Ultra  | 16 High-Perf + 4 Efficient cores, 64-core GPU                      | 114B        |
| 2019 | Cerebras WSE    | Largest ML accelerator, 400,000 cores                              | 1.2T        |
| 2021 | Cerebras WSE-2  | 850,000 cores                                                      | 2.6T        |

* Memory chips have far more transistors than compute chips.
* Transistor count has grown ~1,000,000× in ~47 years.

---

### Why HDLs?

HDLs help manage hardware complexity by allowing:

* **Description** of complex designs
* **Simulation** (functional and timing)
* **Synthesis** to actual hardware
* **Error-free design path** from concept → implementation

**Popular HDLs:**

* Verilog (1984, IEEE 1364, US popular)
* VHDL (1981, IEEE 1076, Europe popular)

**Key Idea:** Learning one HDL makes learning others easier; mapping between them is usually mechanical.

---

## Key HDL Concepts

### Hierarchical Design

* **Top-down:** Define top-level module → break into submodules → leaf cells (gates).
* **Bottom-up:** Start with available building blocks → combine into larger modules → top-level module.
* **Hierarchy** reduces complexity, analogous to functions/methods in programming.

### Module Definition in Verilog

```verilog
module example (a, b, c, y);
  input a, b, c;
  output y;
  // circuit description here
endmodule
```

* Ports: `input`, `output`, optionally multi-bit `[MSB:LSB]`.
* Multi-bit example:

```verilog
input [31:0] a; // 32-bit input
output [15:8] b1; // bits 15..8
```

### Bit Manipulation

* **Bit slicing:** `assign shortbus = longbus[12:5];`
* **Concatenation:** `assign y = {a[2], a[1], a[0], a[0]};`
* **Duplication:** `assign x = {4{a[0]}};`

---

## Two Main HDL Styles

### 1. Structural (Gate-Level)

* Module body contains gate-level description and module instances.
* Hierarchical connection of modules/gates.
* Example: 2-input MUX

```verilog
module mux2(input d0, d1, input s, output y);
  wire ns, y1, y2;
  not g1(ns, s);
  and g2(y1, d0, ns);
  and g3(y2, d1, s);
  or g4(y, y1, y2);
endmodule
```

### 2. Behavioral

* Module body describes functionality using logical/mathematical operators.
* Higher abstraction; multiple possible gate-level realizations.
* Example: 3-input AND-OR

```verilog
assign y = ~a & ~b & ~c | a & ~b & ~c | a & ~b & c;
```

---

## Operators in Verilog

* **Bitwise:** `&`, `|`, `^`, `~`
* **Reduction:** `&a` → AND all bits
* **Conditional (ternary):** `assign y = s ? d1 : d0;`
* **Numbers:** `N’Bxx` e.g., `8'b0000_0001`, `12'hFA3`
* **Floating/High-Z (tri-state):** `assign y = en ? a : 4'bz;`

---

## Example: 4-bit Comparator

### Gate-Level Implementation

```verilog
module compare(input a0,a1,a2,a3, b0,b1,b2,b3, output eq);
  wire c0,c1,c2,c3,c01,c23;
  MyXnor i0(.A(a0), .B(b0), .Z(c0));
  MyXnor i1(.A(a1), .B(b1), .Z(c1));
  MyXnor i2(.A(a2), .B(b2), .Z(c2));
  MyXnor i3(.A(a3), .B(b3), .Z(c3));
  assign c01 = c0 & c1;
  assign c23 = c2 & c3;
  assign eq = c01 & c23;
endmodule
```

### Higher-Level Implementation

```verilog
module compare(input [3:0] a, input [3:0] b, output eq);
  assign eq = (a == b) ? 1 : 0;
endmodule
```

* Parameterized modules allow reusability:

```verilog
module mux2 #(parameter width=8)(input [width-1:0] d0,d1, input s, output [width-1:0] y);
  assign y = s ? d1 : d0;
endmodule
```

---

## Synthesis & Simulation

* **Synthesis:** Converts HDL → netlist of gates & wires; optimizations applied but not guaranteed optimal.
* **Simulation:** Verifies functionality and timing without physical circuit.

---

## Good Practices

* Consistent naming style, e.g., `MSB → LSB` for buses.
* One module per file; file name = module name.
* Always remember Verilog describes **hardware**, not software logic.

---

## Summary (Combinational Logic)

* Structural & behavioral modeling
* Basic combinational logic: AND, OR, XOR, multiplexers
* Multi-bit buses, constants, tri-state buffers
* Reusable & parameterized modules

---

## Tags

#ComputerArchitecture #HDL #Verilog #DigitalDesign #CombinationalLogic #SequentialLogic #HardwareSynthesis #BehavioralModeling #StructuralModeling #FPGA #VHDL

---

