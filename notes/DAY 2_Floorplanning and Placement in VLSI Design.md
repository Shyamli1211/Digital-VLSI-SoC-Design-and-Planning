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
