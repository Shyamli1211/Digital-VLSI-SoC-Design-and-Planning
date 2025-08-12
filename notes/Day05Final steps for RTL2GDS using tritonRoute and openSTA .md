## Routing and design rule check(DRC) 

## Lecture 76 – Introduction to Maze Routing (Lee’s Algorithm)
Maze routing is a path-finding algorithm used in VLSI to determine the shortest path between two points in a routing grid.

**Key Ideas:**
- The chip layout is represented as a grid.
- The algorithm searches for a path from **source** to **destination** while avoiding obstacles.
- Works in two main phases:
  1. **Wave Propagation** – Expands in all directions until the target is reached.
  2. **Backtracking** – Traces the shortest path from target back to source.

**Advantages:**
- Guarantees finding a shortest path if it exists.
- Simple to implement.

**Limitations:**
- Computationally expensive for large designs.
- Does not consider timing or congestion directly.

---

## Lecture 77 – Lee’s Algorithm Conclusion
- Lee’s algorithm ensures **minimum path length** but is not the fastest for large chips.
- Variations and optimizations (Hadlock’s, A*) improve speed.
- Often used in EDA tools for **detailed routing** where precision is critical.

---

## Lecture 78 – Design Rule Check (DRC)
DRC verifies that the layout meets all **fabrication design rules** set by the foundry.

**Common Rules Checked:**
- **Minimum Width** of metal layers.
- **Spacing** between wires.
- **Via Enclosure** rules.
- **Minimum Area** requirements.

**Importance:**
- Prevents manufacturing defects.
- Ensures design reliability.
- A clean DRC report is mandatory before tape-out.

---
## Power Distribution Network and routing

## Lecture 79 – Lab Steps to Build Power Distribution Network
- Define power and ground net names.
- Create horizontal and vertical power straps.
- Ensure coverage for the entire chip.
- Verify strap width and spacing meet DRC rules.

---

## Lecture 80 – Lab Steps from Power Straps to Std Cell Power
- Connect power straps to standard cell rows.
- Verify connectivity with LVS.
- Ensure minimal IR drop across the network.

---

## Lecture 81 – Basics of Global and Detail Routing + TritonRoute Configuration
**Global Routing:**
- Divides the chip into routing tiles.
- Finds an approximate route for each net.
- Focuses on congestion minimization.

**Detailed Routing:**
- Assigns exact tracks and vias.
- Ensures all DRC rules are satisfied.
- Implements preferred routing directions.

**TritonRoute Configuration:**
- Define layer directions and spacing.
- Set routing effort levels.
- Enable DRC checking during routing.

---

