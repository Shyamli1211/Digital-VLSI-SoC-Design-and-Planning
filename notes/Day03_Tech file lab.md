# Day 03 – Lectures 31 to 54

## 31 – IO Placer Revision
**Overview:**  
Revision of IO placer concepts used in ASIC physical design. Focuses on placing input/output pins optimally to minimize routing complexity and delay.

**Key Points:**
- IO placer assigns pin locations on the periphery of the chip/block.
- Proper placement improves timing performance and reduces wirelength.
- Placement decisions consider:
  - Signal direction (input, output, bidirectional)
  - Net connectivity
  - Clock distribution
  - Power/ground pad placement
- Tools like OpenROAD or custom placement scripts can be used for IO optimization.

---

## 32 – SPICE Deck Creation for CMOS Inverter
**Overview:**  
Creating the SPICE netlist (simulation deck) for a CMOS inverter for pre-layout simulation.

**Process:**
1. Define transistor models (PMOS, NMOS) with correct parameters (W/L ratio, model files).
2. Connect PMOS source to VDD, NMOS source to GND.
3. Connect PMOS and NMOS drains together as the output node.
4. Apply input stimulus (square wave, DC sweep).
5. Set simulation commands for DC, transient, and AC analysis.

**Outcome:**  
A `.sp` file ready for simulation to evaluate inverter characteristics such as switching threshold and propagation delay.

---

## 33 – SPICE Simulation Lab for CMOS Inverter
**Overview:**  
Hands-on simulation of the CMOS inverter using ngspice or similar tools.

**Steps:**
- Load the SPICE deck created in Lecture 32.
- Run transient analysis (`.tran`) to observe input/output waveforms.
- Verify the inverter’s switching point and check for logic inversion.
- Measure rise time, fall time, and propagation delay from the output waveform.

**Outcome:**  
Understanding the dynamic behavior of a CMOS inverter before fabrication.

---

## 34 – Switching Threshold (Vm)
**Overview:**  
Switching Threshold (Vm) is the input voltage at which the output voltage is exactly VDD/2.

**Importance:**
- Determines the noise margin of the inverter.
- A balanced CMOS inverter typically has Vm ≈ VDD/2 when PMOS and NMOS are sized for equal drive strengths.

**Calculation:**  
Vm can be obtained from the VTC (Voltage Transfer Characteristic) curve using `.dc` sweep analysis in SPICE.

---

## 35 – Static and Dynamic Simulation of CMOS Inverter
**Static Simulation:**
- DC analysis to obtain VTC curve.
- Determines logic levels, switching threshold, and noise margins.

**Dynamic Simulation:**
- Transient analysis to measure delay and slew rate.
- Observes how the inverter responds to changing input signals.

**Purpose:**  
Combines both views to fully characterize the inverter’s performance.

---

## 36 – Lab: Steps to Git Clone `vsdstdcelldesign`
**Objective:**  
Set up the design environment by cloning the standard cell design repository.

**Steps:**
1. Open terminal.
2. Use command:
   ```bash
   git clone https://github.com/<username>/vsdstdcelldesign.git

   - Navigate into the repo with `cd vsdstdcelldesign` to access design files.

## 37 - Creation of active regions
- Define specific silicon areas for transistor fabrication.
- Isolation ensures no unwanted current flows between devices.

## 38 - Formation of N-well and P-well
- **N-well** for PMOS, doped with donor impurities.
- **P-well** for NMOS, doped with acceptor impurities.

## 39 - Formation of gate terminal
- Grow thin oxide layer as dielectric.
- Deposit and pattern polysilicon to form the MOSFET gate.

## 40 - Lightly Doped Drain (LDD) formation
- Adds a lightly doped region near drain to reduce hot-carrier effects.
- Improves device reliability.

## 41 - Source and drain formation
- Implant high-concentration dopants for source/drain regions.
- Annealing activates dopants and repairs crystal damage.

## 42 - Local interconnect formation
- Deposit and pattern conductive layer for short-range connections.
- Saves routing space in higher metal layers.

## 43 - Higher-level metal layer formation
- Add multiple metal layers for main circuit routing.
- Use vias to connect between layers.

## 44 - Passivation layer formation
- Apply protective coating to prevent damage and contamination.
- Etch openings to expose bond pads.

## 45 - Bond pad formation
- Create large metal pads for external chip connections.
- Used in wire bonding or flip-chip methods.

## 46 - Packaging and final testing
- Dice wafer into chips, package them, and run tests.
- Ensure chips meet design specifications before shipment.
## 47 - Introduction to Magic Tool
- Open-source VLSI layout editor.
- Used for viewing, creating, and editing physical designs.
- Supports CIF, GDSII formats for chip layouts.

## 48 - Installing and running Magic
- Install using package managers (e.g., `sudo apt install magic`).
- Launch with the `magic` command in terminal.
- Load layout files for visualization.

## 49 - Loading standard cell layouts
- Standard cells are pre-designed logic gates.
- Magic can import `.mag` or `.gds` cell layouts.
- Allows inspection and modification.

## 50 - Design Rule Check (DRC)
- Ensures layout meets fabrication constraints.
- Checks spacing, width, and overlaps.
- Prevents manufacturing defects.

## 51 - Extracting layout information
- Generate netlist and device parameters from layout.
- Output used for verification and simulation.
- Helps compare layout with schematic.

## 52 - Layout vs Schematic (LVS) check
- Compares extracted netlist with original schematic.
- Confirms functional equivalence.
- Detects missing or extra connections.

## 53 - Parasitic Extraction (PEX)
- Calculates parasitic capacitance and resistance in layout.
- Used to refine timing and power analysis.
- Critical for post-layout simulation accuracy.

## 54 - Preparing layout for fabrication
- Export layout in GDSII format.
- Final DRC and LVS checks before submission.
- Ensures design is fabrication-ready.

