# Day 1: Lecture 0–11 Notes

---

## Lecture 0: Introduction to QFN-48 Package, Chip, Pads, Core, Die and IPs
![WhatsApp Image 2025-08-11 at 23 37 51_303c2936](https://github.com/user-attachments/assets/3aba94e3-a9eb-4138-a917-06a5ce62b0f5)


The **QFN-48 (Quad Flat No-lead, 48 pins)** package is a type of surface-mount integrated circuit package with 48 contact pads placed around the edges, but without protruding leads.  
Inside this package is the **chip** — the complete integrated circuit. Within the chip lies the **die**, a thin piece of semiconductor material (usually silicon) where the actual transistors and logic gates are fabricated.  

Key components:
- **Core** → Contains the main functional logic of the chip (e.g., processor core, control logic).
- **Pads** → Metal contact areas used to connect the internal circuitry to the package pins.
- **IPs (Intellectual Properties)** → Pre-designed and reusable functional blocks like UART, SPI controllers, memory interfaces, etc.

**Relevance:**  
The QFN-48 package is commonly used in ASIC projects because it is compact, provides good electrical performance, and supports automated PCB assembly.

---

## Lecture 1: Introduction to RISC-V
![Lecture 1 Screenshot](images/day1/Screenshot%20(63).png)

**RISC-V** is an **open-source Instruction Set Architecture (ISA)** — the fundamental set of commands that a processor understands and executes.  
Unlike proprietary ISAs such as ARM or x86, RISC-V is license-free, meaning:
- Anyone can design a processor implementing RISC-V without paying royalties.
- It is modular — the base instruction set can be extended with optional features (e.g., integer multiplication, floating point, vector operations).
- Supported by a rapidly growing open-source ecosystem.

**Why it matters:**  
For students and researchers, RISC-V enables learning and experimentation without legal or cost barriers. In industry, it offers flexibility to design customized processors optimized for specific applications.

---

## Lecture 2: From Software Applications to Hardware
![Lecture 2 Screenshot](images/day1/Screenshot%20(5).png)

The journey from a **software application** to **hardware execution** involves several layers:
1. **High-level code** (e.g., C, Python) → Written by developers.
2. **Compilation** → Translates high-level code to assembly instructions of the target ISA.
3. **Assembly to Machine Code** → Binary instructions the processor can execute.
4. **Hardware Execution** → The processor hardware implements these instructions through logic circuits.

In ASIC design, we often simulate this process:  
- High-level algorithms are described in **RTL (Register Transfer Level)** using languages like Verilog.
- RTL is **synthesized** into gate-level circuits, then physically implemented into a silicon layout.

---

## Lecture 3: Introduction to All Components of Open-Source Digital ASIC Design
![Lecture 3 Screenshot](images/day1/Screenshot%20(6).png)

An open-source ASIC design environment includes:
- **RTL Design Tools** → For writing hardware description (Verilog, VHDL).
- **Synthesis Tools** (e.g., Yosys) → Convert RTL into a gate-level netlist.
- **Placement & Routing Tools** (e.g., OpenROAD) → Arrange logic cells and connect them.
- **Verification Tools** → Simulate and check correctness.
- **PDK (Process Design Kit)** → Contains fabrication process details, standard cell libraries, and design rules.

**Benefit:**  
Using open-source tools (OpenLANE, Sky130 PDK) allows complete chip design without expensive proprietary software.

---

## Lecture 4: Simplified RTL to GDS Flow
![Lecture 4 Screenshot](images/day1/Screenshot%20(8).png)

**RTL to GDSII Flow**:
1. **RTL (Register Transfer Level)** → High-level hardware description.
2. **Logic Synthesis** → Converts RTL to a network of logic gates.
3. **Floorplanning** → Allocates space for different chip blocks.
4. **Placement** → Places standard cells on the chip floorplan.
5. **Clock Tree Synthesis (CTS)** → Ensures clock signals reach all registers with minimal skew.
6. **Routing** → Connects all signals physically.
7. **Sign-off** → Verifies timing, power, and physical design rules.
8. **GDSII Export** → Final layout file sent for fabrication.

---

## Lecture 5: Introduction to OpenLANE and Sky130 PDK
![Lecture 5 Screenshot](images/day1/Screenshot%20(56).png)

**OpenLANE** is a fully automated open-source RTL-to-GDS flow. It integrates multiple tools to handle synthesis, placement, routing, and verification.

**Sky130 PDK**:
- Developed by SkyWater Technology.
- 130nm process node (feature size of transistors).
- Contains standard cells, design rules, and SPICE models for simulation.
- Enables real-world fabrication compatibility.

**Impact:**  
Using Sky130 PDK with OpenLANE lets designers create chips that can actually be manufactured in a professional fab.

---

## Lecture 6: Detailed ASIC Design Flow in OpenLANE
![Lecture 6 Screenshot](images/day1/Screenshot%20(9).png)

The complete OpenLANE design process includes:
1. **Preparation** → Setting up design files and constraints.
2. **Synthesis** → RTL to gate-level netlist conversion.
3. **Floorplanning** → Defining chip dimensions and block placement.
4. **Placement** → Optimized arrangement of cells.
5. **CTS (Clock Tree Synthesis)** → Building an efficient clock network.
6. **Routing** → Physical connection of cells.
7. **Sign-off** → Checking design rule compliance, timing, and power.

---

## Lecture 7: OpenLANE Directory Structure in Detail
![Lecture 7 Screenshot](images/day1/Screenshot%20(59).png)

The OpenLANE directory is organized into:
- **`designs/`** → Contains user project source files.
- **`pdks/`** → Holds process design kits (e.g., Sky130).
- **`flow/`** → Core automation scripts.
- **`runs/`** → Stores all generated data and logs for each design run.

Understanding the structure is important for:
- Debugging failed runs.
- Customizing flow stages.
- Reusing configurations for multiple projects.

---

## Lecture 8: Design Preparation Step
![Lecture 8 Screenshot](images/day1/Screenshot%20(60).png)

Before synthesis, the design must be prepared:
- Import RTL files.
- Define constraints (timing, area, power).
- Set environment variables for PDK paths.
- Generate initial configuration files.

This step ensures all required inputs are ready for the synthesis stage.

---

## Lecture 9: Review Files After Design Preparation and Run Synthesis
![Lecture 9 Screenshot](images/day1/Screenshot%20(61).png)

Post-preparation review involves:
- Checking the generated netlists and configuration files.
- Ensuring clock definitions are correct.
- Verifying design parameters match specifications.

**Synthesis Stage**:
- Uses tools like **Yosys** to map RTL into standard cells.
- Produces a gate-level netlist ready for placement.

---

## Lecture 10: OpenLANE Project Git Link Description
![Lecture 10 Screenshot](images/day1/lecture10.png)

The OpenLANE GitHub repository contains:
- Source code for the flow.
- Example designs.
- Documentation and tutorials.
- Issue tracker for reporting and resolving problems.

Cloning and exploring the repo helps designers understand flow internals and customize it for their needs.

---

## Lecture 11: Steps to Execute Synthesis Results
![Lecture 11 Screenshot](images/day1/lecture11.png)

After synthesis:
1. Verify gate-level netlist functionality through simulation.
2. Check timing reports to ensure the design meets frequency goals.
3. Proceed to floorplanning if synthesis passes all checks.
4. Document synthesis logs for reproducibility.

This step bridges the logical and physical design phases, ensuring correctness before moving forward.
