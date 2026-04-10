[[Computer Architecture]]

Computer Architecture: Week 1 - Introduction
Course Overview

    Instructor: Dr. Desoky Abdelqawy (Faculty of Computer and AI, Cairo University).

    Materials: Based on international curricula from ETH Zürich (Prof. Onur Mutlu) and MIT (Prof. Chris Terman).

    Textbooks: * Digital Design and Computer Architecture by Harris & Harris.

        Introduction to Computing Systems by Yale Patt & Sanjay Patel.

## 1. What is Computer Architecture?

Computer Architecture is the science and art of:

    Designing and Interconnecting hardware components.

    Designing the Hardware/Software Interface (ISA).

    Meeting Goals: Functionality, performance, energy efficiency, cost, and security.

The Transformation Hierarchy (The Stack)

To solve a problem, we navigate several layers:

    Problem → Algorithm → Program/Language → Runtime System (VM/OS) → ISA (Architecture) → Microarchitecture → Logic → Circuits → Electrons.

## 2. Current Trends and Challenges

The computing landscape has changed drastically in the last decade due to several factors:
The "Data Bottleneck"

    Data-Intensive Workloads: AI, Machine Learning, Genomics, and In-memory databases are overwhelmed by data.

    Energy Inefficiency: Moving data from DRAM to the CPU consumes significantly more energy than actual computation.

        Example: A memory access can consume 6400x the energy of a simple integer addition.

Modern Architecture Goals

    Performance & Energy Efficiency

    Sustainability

    Security & Privacy (Hardware-level protection)

    Reliability & Safety

## 3. Innovative Computing Paradigms

To overcome traditional bottlenecks, several new designs are being explored:

    Processing In Memory (PIM): Moving computation into the memory chips (DRAM) to reduce data movement (e.g., UPMEM, Samsung FIM/AxDIMM).

    Accelerators: Domain-specific hardware like:

        Google TPU (Tensor Processing Unit): Specialized for Machine Learning.

        Tesla FSD: Full Self-Driving computer for real-time AI.

        Cerebras Wafer Scale Engine: The largest ML chip with 850,000 cores.

    Heterogeneous Systems: Combining CPUs, GPUs, FPGAs, and specialized accelerators on a single chip (e.g., Apple M1 Max/Ultra).

## 4. Design Principles & Tradeoffs

Computer Architecture is about evaluating tradeoffs. Similar to architectural design in buildings (e.g., comparing two train stations), hardware design is evaluated based on:

    Functionality & Reliability

    Aesthetics & Space

    Expandability & Cost

    Performance Metrics

## 5. Course Logistics & Evaluation
Evaluation Criteria

    Final Exam: 60%

    Midterm: 20%

    Labs & Assignments: 20%

Strict Cheating Policy

    Zero Tolerance: Copying code, using LLMs/AI for assignments, or unauthorized collaboration will result in faculty-level disciplinary action.

Key Topics to be Covered

    Digital Design & Logic (Gates, Combinational/Sequential Circuits).

    Hardware Description Languages (HDL).

    ISA & Microarchitecture (Pipelining).

    Memory Organization & Caches.

    Optional: GPUs, SIMD, and Virtual Memory.

Tags

#ComputerArchitecture #DigitalDesign #PIM #MachineLearning #TPU #EnergyEfficiency #ISA #CS_Education