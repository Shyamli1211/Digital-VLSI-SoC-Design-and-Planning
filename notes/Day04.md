# Day 04 – Pre-layout timing analysis and importance of good clock tree

### Timing modelling using delay tables

# Lecture 55 – Lab Steps to Convert Grid Info to Track Info
This lab focuses on converting grid information (manufacturing grid, placement grid) into routing track information used during PnR.

**Key Steps:**
1. Identify grid pitch in both X and Y directions from tech files.
2. Map routing track definitions for horizontal and vertical layers.
3. Verify alignment between cell pins and routing tracks.
4. Ensure compatibility between placement grid and routing grid to avoid routing violations.

---

## Lecture 56 – Understanding Tracks in Physical Design
Tracks are predefined routing paths that help maintain uniform routing and avoid design rule violations.

- **Horizontal and Vertical Tracks**: Defined for alternate metal layers.
- **Track Pitch**: Distance between two adjacent tracks.
- **Purpose**: Helps routers decide legal routing paths and ensures pin accessibility.

---

## Lecture 57 – Track and Pin Alignment
Pin alignment is critical for routability:
- Standard cell pins must be aligned to routing tracks.
- Misalignment causes extra vias and detours, increasing delay.
- Ensure library cells follow consistent pin-to-track mapping.

---

## Lecture 58 – Preferred Routing Directions
- Even-numbered metal layers usually have **horizontal** preferred routing.
- Odd-numbered metal layers usually have **vertical** preferred routing.
- Following preferred directions reduces congestion and improves DRC compliance.

---

## Lecture 59 – LEF Files and Track Information
**LEF (Library Exchange Format)** files store:
- Cell dimensions.
- Pin locations.
- Track grid definitions.
This information guides placement and routing tools.

---

## Lecture 60 – Routing Resources and Track Utilization
- **Routing Resource**: Available tracks for a given area.
- **Track Utilization**: Percentage of used tracks after routing.
- High utilization may cause congestion, leading to DRC violations.

---

## Lecture 61 – Impact of Track Information on Routing
- Well-defined tracks improve routing quality and reduce congestion.
- Misaligned tracks increase wire length and delay.
- Proper track setup ensures predictable routing behavior.

---

## Timing analysis with ideal clocks using openSTA

## Lecture 62 – Summary of Track Concepts
- Tracks are essential for organized routing.
- Correct pitch, direction, and alignment improve overall chip performance.
- LEF/DEF files play a key role in defining track info for tools.

---

## Lecture 63 – Placement Overview
Placement arranges standard cells within the floorplan after macros are placed.

**Goals:**
- Minimize wire length.
- Ensure legal placement.
- Leave sufficient space for routing and power.

**Stages:**
1. **Global Placement** – Rough arrangement.
2. **Detailed Placement** – Fine-tuning for legality and performance.

---

## Lecture 64 – Placement Constraints
- **Keep-Out Regions** – No cell placement allowed.
- **Cell Padding** – Extra spacing between cells.
- **Critical Path Placement** – Place time-sensitive cells closer.
- **Blockages** – Reserved areas for routing or future changes.

---

## Lecture 65 – Timing-Driven Placement
- Identify **critical paths**.
- Reduce wire delay by placing related cells closer.
- Balance timing closure with routability.

---

## Lecture 66 – Power-Aware Placement
- Shorter wires for high-activity nets.
- Spread high-power cells to avoid hot spots.
- Place clock-gating cells near registers.

---
## Clock tree synthesis TritonCTS and signal integrity

## Lecture 67 – Congestion-Aware Placement
- Analyze congestion maps after placement.
- Spread cells in high-density areas.
- Reserve routing channels and adjust macro spacing.

---

## Lecture 68 – Placement Algorithms
- **Simulated Annealing** – Iterative swap optimization.
- **Force-Directed** – Cells as masses, nets as springs.
- **Analytical** – Mathematical optimization for wire length and constraints.

---

## Lecture 69 – Placement Verification
- **DRC Check** – No overlaps.
- **Timing Analysis** – Ensure performance targets.
- **Congestion Analysis** – Avoid bottlenecks.
- **Power Analysis** – Voltage drop checks.

---

## Lecture 70 – Clock Tree Synthesis (CTS) Basics
CTS builds a balanced clock network:
- Minimize **skew**.
- Minimize **latency**.
- Balance load distribution.

---
## Timing analysis with real clocks using openSTA 

## Lecture 71 – Clock Skew and Latency
- **Skew**: Difference in clock arrival times.
  - Positive / Negative skew impacts timing differently.
- **Latency**: Delay from clock source to register.

---

## Lecture 72 – CTS Design Considerations
- Choose proper **topology** (H-tree, mesh, spine).
- Insert buffers to balance skew.
- Isolate clock nets from noise.

---

## Lecture 73 – CTS Inputs
- Post-placement netlist.
- Timing constraints (SDC).
- Library files for buffers/inverters.
- CTS options for skew and latency targets.

---

## Lecture 74 – CTS Implementation
1. Identify clock sources/sinks.
2. Insert buffers/inverters.
3. Route clock nets using preferred layers.
4. Run clock-specific DRC.

---

## Lecture 75 – Post-CTS Optimization
- Re-run STA.
- Fix hold violations.
- Optimize routing for skew.
- Check clock network power.

---



