# Day 2: Floorplanning and Placement in VLSI Design

---

## 12. Utilization Factor and Aspect Ratio

### **Utilization Factor (UF)**
- **Definition:** The ratio of the total area occupied by standard cells to the total available core area in the chip.
- **Formula:**  
  `UF = (Total Standard Cell Area / Total Core Area) × 100%`
- **Purpose:** Indicates how efficiently the chip area is being used.
- **Typical Values:** 60–80% (Too high → routing congestion, Too low → wasted silicon area).
- **Impact:**
  - Higher UF → smaller chip size, but may cause heat and congestion issues.
  - Lower UF → better routing space but larger die size.

**Example:**  
If core area = 1000 μm² and total cell area = 700 μm², then:  
UF = (700 / 1000) × 100% = **70%**.

---

### **Aspect Ratio (AR)**
- **Definition:** Ratio of core height to core width.  
  `AR = Core Height / Core Width`
- **Preferred AR:** 1 (square-shaped core).
- **Effect:**  
  - AR ≈ 1 → balanced routing paths.  
  - AR ≠ 1 → elongated routing in one direction, may cause delay issues.

---

## 13. Concept of Pre-Placed Cells
- **Pre-Placed Cells** are large functional blocks fixed at specific chip locations **before** automated placement runs.
- Examples:
  - SRAM Macros
  - PLL (Phase-Locked Loop)
  - IO pads
- **Reasons for Pre-Placement:**
  1. Reduce routing complexity.
  2. Meet timing constraints for high-speed components.
  3. Ensure direct connection to power and clock lines.
- **Placement Strategy:**
  - Place near the periphery for IO-heavy blocks.
  - Place centrally for high-interaction blocks.

---

## 14. Decoupling Capacitors (Decaps)
- **Function:** Act as local charge reservoirs to stabilize supply voltage.
- **Why Needed:**  
  When many transistors switch simultaneously, the demand for current increases abruptly → causes IR drop. Decaps release stored charge instantly.
- **Placement:** Near high-switching logic clusters.
- **Impact on Performance:** Reduces voltage droop → prevents timing violations.

---

## 15. Power Planning
- **Objective:** Deliver stable VDD and GND across the chip.
- **Elements:**
  1. **Power Rings:** Thick metal loops around core.
  2. **Power Stripes:** Vertical and horizontal lines carrying power inside.
  3. **Power Pads:** Entry points for power from the package.
- **Design Rules:**
  - Minimize IR drop (voltage drop due to resistance).
  - Provide multiple supply points to avoid hotspots.

---

## 16. Pin Placement and Logical Cell Placement Blockage
- **Pin Placement:**  
  - Determine optimal I/O pin positions to minimize routing length.
  - Group related pins together for better data flow.
- **Placement Blockages:**
  - **Hard Blockages:** Completely block standard cell placement.
  - **Soft Blockages:** Allow certain types of cells (e.g., buffers) only.

---

## 17. Steps to Run Floorplan using OpenLANE
1. **Set Floorplan Variables**:
   - `FP_CORE_UTIL` → Utilization Factor.
   - `FP_ASPECT_RATIO` → Aspect Ratio.
   - `FP_IO_MODE` → IO pin distribution mode.
2. **Run Floorplan Command:**
   ```tcl
   run_floorplan


## 18. Review Floorplan Files and Steps to View Floorplan
- **DEF (Design Exchange Format)**: Stores complete chip floorplan information including placement, routing, and macros.
- **LEF (Library Exchange Format)**: Contains abstract information about cells such as size, pin location, and metal layer usage.
- **Steps to View in Magic**:
  1. Open terminal and navigate to the design folder.
  2. Run:
     ```bash
     magic -T <tech_file>.tech <design>.mag &
     ```
  3. Verify macro locations, I/O positions, and power rails.

---

## 19. Review Floorplan Layout in Magic
- Visually check:
  - **Macro Placement** – Ensure large blocks like SRAM and PLL are placed as per constraints.
  - **Pin Placement** – Verify correct positioning to minimize routing.
  - **Power Distribution** – Confirm power stripes and rings are properly connected.
- **Goal:** Detect design rule violations early before placement.

---

## 20. Netlist Binding and Initial Place Design
- **Netlist Binding:** Mapping of the synthesized logical netlist to actual physical standard cell instances.
- **Initial Placement:** Early stage where the placer assigns approximate locations to all cells based on connectivity.
- **Objective:** Reduce wire length and maintain signal timing.





## 21. Placement Optimization using Estimated Wire-Length and Capacitance
- **Why:** Long wires increase capacitance → slower signals & higher power.
- **How:**
  - Placer estimates wire length between connected cells.
  - Uses algorithms to rearrange cells to minimize both wire length and load capacitance.
- **Result:** Better performance, lower power consumption.

---

## 22. Final Placement Optimization
- After initial placement, the tool performs:
  - **Timing Optimization** – Fixes setup/hold violations.
  - **Congestion Optimization** – Relieves routing hotspots.
  - **Thermal Optimization** – Spreads heat-generating cells.
- **Outcome:** Ready for clock tree synthesis (CTS) stage.

---

## 23. Need for Libraries and Characterization
- **Libraries Required:**
  - `.lib` – Timing, power, and functional data of cells.
  - `.lef` – Physical dimensions and pin locations.
- **Characterization:** Process of measuring timing, power, and leakage for each cell at multiple process, voltage, and temperature (PVT) corners.
- **Importance:** Ensures design tools have accurate data for placement, routing, and timing closure.

---

## 24. Congestion-Aware Placement using RePlAce
- **RePlAce** is a global placement algorithm that spreads cells evenly to reduce routing congestion.
- Works in iterative passes:
  1. Initial rough placement.
  2. Evaluate congestion maps.
  3. Spread cells in dense areas.
- **Benefit:** Ensures routability without increasing chip size unnecessarily.

---

## 25. Inputs for Cell Design Flow
- **Process Design Kit (PDK)** – Contains design rules, layer definitions, and SPICE models.
- **Library Models** – Standard cells, IO cells, and macros.
- **Timing Constraints** – Setup and hold requirements from the designer.
- **Power Targets** – Maximum power allowed for the chip.

---

## 26. Circuit Design Step
- **Objective:** Design the transistor-level schematic for each standard cell.
- **Steps:**
  1. Draw circuit in schematic editor.
  2. Run SPICE simulation to verify functionality and timing.
  3. Optimize for power, area, and speed.
- **Outcome:** A verified circuit ready for layout design.

---

## 27. Layout Design Step
- **Purpose:** Create physical mask layout for fabrication.
- **Key Checks:**
  - **DRC (Design Rule Check)** – Ensures layout follows manufacturing rules.
  - **LVS (Layout vs. Schematic)** – Confirms layout matches the schematic.
- **Final Output:** GDSII file for fabrication.

---

## 28. Typical Characterization Flow
1. **Stimulus Creation:** Apply a variety of input patterns to cells.
2. **SPICE Simulation:** Run across different PVT corners.
3. **Data Extraction:** Measure delays, power, and transition times.
4. **.lib File Generation:** Store extracted data in library format for EDA tools.

---

## 29. Timing Threshold Definitions
- **Purpose:** Define measurement points for timing analysis.
- **Common Thresholds:**
  - **20% of VDD:** Starting point for rise time measurement.
  - **50% of VDD:** Used for delay measurement (input-to-output).
  - **80% of VDD:** Ending point for rise time measurement.
- **Reason:** Provides a consistent reference for delay and transition calculations.

---

## 30. Propagation Delay and Transition Time
- **Propagation Delay (t_pd):**
  - Time taken for the output to change after the input reaches 50% of VDD.
  - Measured from **50% input** → **50% output** voltage level.
- **Transition Time (Slew Rate):**
  - Time taken for the output to change from 20% to 80% (rise) or 80% to 20% (fall) of VDD.
- **Impact:** Both parameters are critical for meeting setup/hold timing in digital circuits.

---





