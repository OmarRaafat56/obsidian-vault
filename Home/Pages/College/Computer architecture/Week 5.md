[[Computer Architecture]]

Computer Architecture: Week 5 - Von Neumann Model & ISA
___
#ComputerArchitecture #computer-architecture #von-Neumann-model #memory #ISA 
## 1. The Von Neumann Model (1946)

The fundamental model for almost all general-purpose computers today. It is characterized by the Stored Program concept, where both instructions and data are stored in the same memory.
The 5 Key Components:

    Memory: Stores instructions (program) and data.

    Processing Unit: Performs arithmetic and logic (ALU) and contains temporary storage (Registers).

    Control Unit: The "conductor" that sequences the execution of instructions using the Program Counter (PC) and Instruction Register (IR).

    Input: Mechanisms to get data into the computer (Keyboard, Mouse).

    Output: Mechanisms to get data out (Monitor, Printer).
___

## 2. Memory Organization

Memory consists of uniquely identifiable locations called addresses.

    Address Space: The total number of locations (e.g., 216 for LC-3).

    Addressability: Number of bits per location (e.g., byte-addressable = 8 bits).

    Endianness: The order of bytes within a multi-byte word:

        Big Endian: MSB (Most Significant Byte) is at the lowest address.

        Little Endian: LSB (Least Significant Byte) is at the lowest address.

    Accessing Memory: * MAR (Memory Address Register): Holds the address to be accessed.

        MDR (Memory Data Register): Holds the data being read from or written to memory.
___

## 3. Instruction Set Architecture (ISA)

The ISA is the interface between software and hardware. It defines the "vocabulary" the computer understands.
Instruction Types

    Operate Instructions: Process data in the ALU (e.g., ADD, AND, NOT).

    Data Movement: Move data between memory and registers (e.g., LDR / LW for load, STR / SW for store).

    Control Instructions: Change the flow of the program (e.g., BR for branch, JMP for jump).

Instruction Formats (Examples)

    Opcode: Specifies the operation (e.g., 0001 for ADD in LC-3).

    Operands: Specify where the data comes from (Source) and goes to (Destination).

    Addressing Modes: How to find data (e.g., Register mode, Base+Offset).
___

## 4. The Instruction Cycle

The step-by-step process of executing a single instruction:

    FETCH: Get instruction from memory into the IR; increment PC.

    DECODE: Identify the opcode and generate control signals.

    EVALUATE ADDRESS: Calculate memory addresses if needed (e.g., for LDR).

    FETCH OPERANDS: Get source data from registers or memory.

    EXECUTE: Perform the operation in the ALU.

    STORE RESULT: Write the result back to the destination (register or memory).
___

Comparison: LC-3 vs. MIPS
Feature	LC-3	MIPS
Word Length	16-bit	32-bit
Registers	8 (R0−R7)	32 ($0−$31)
Memory	16-bit addressable	32-bit (byte-addressable)
Instruction Size	Fixed 16-bit	Fixed 32-bit