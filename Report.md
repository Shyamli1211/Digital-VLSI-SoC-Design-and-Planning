# VLSI Physical Design Report – Day 1 to Day 5

---
## Day 1 – Inception of Open-Source EDA, OpenLANE, Sky130 PDK

### Theory Highlights:
- Overview of open-source EDA tools ecosystem: importance, advantages over commercial tools, and community-driven development.
- Introduction to OpenLANE: an automated RTL-to-GDSII flow integrating various open-source tools such as Yosys, OpenSTA, TritonRoute, Magic, and others.
- Role and structure of Skywater SKY130 Process Design Kit (PDK): overview of process technology, design rules, and how PDK enables fabrication of ASICs.
- Understanding the full chip design flow: from RTL description, synthesis, floorplanning, placement and routing, signoff checks, to final GDSII generation.
- Importance of standard cell libraries (e.g., sky130_fd_sc_hd) in ASIC design for ensuring timing, power, and area optimization.
- Introduction to Docker containerization for environment setup, ensuring reproducibility and consistency across different platforms.

### Lab Snapshot:
- Setting up the OpenLANE environment on a Linux system using Docker, including mounting volumes and setting environment variables.
- Executing the OpenLANE flow command:
  ```bash
  ./flow.tcl -design spm -tag openlane_test -overwrite
<img width="1920" height="1080" alt="Screenshot (105)" src="https://github.com/user-attachments/assets/cadcdf13-65df-4020-bb9e-338342ffc3da" />

<img width="1920" height="1080" alt="Screenshot (107)" src="https://github.com/user-attachments/assets/02a511fe-ecbf-44f9-8c6d-cc6f6e1b0673" />

## Day 2 – Floorplanning & Library Cells
**Theory Highlights:**
- Good vs bad floorplans: core/die area, aspect ratio, utilization factor.
- Macro placement strategies and I/O pin planning.
- Power planning with VDD/VSS rings and decoupling caps.

**Lab Snapshot:**
- `run_floorplan` command.
- Viewing floorplan in Magic (`magic -T sky130A.tech...`).
- Using `S`, `V`, and `Z` keys to navigate and inspect the layout.
<img width="1864" height="952" alt="day 2 vlsi pic" src="https://github.com/user-attachments/assets/364ae1a4-eb86-4b9b-860c-a7cf5d53d284" />

---

## Day 3 – Cell Design & Characterization Flow
**Theory Highlights:**
- Designing and simulating standard cells (inverter) in Magic + ngspice.
- Performing DRC, LVS, and SPICE-based timing analysis.
- Understanding rise/fall transitions and delays.

**Lab Snapshot:**
- Clone cell design repo and run Magic layout.
- Use `extract all` / `ext2spice` to generate netlist.
- Perform and plot timing simulations.

---

## Day 4 – Timing Analysis & Clock Tree Synthesis (CTS)
**Theory Highlights:**
- Delay tables: modeling gate delay with input slew and load.
- Concepts: setup time, hold time, clock jitter & uncertainty.
- CTS using buffer trees: skew, latency, topology considerations.

**Lab Snapshot:**
- Generate `tracks.info`, copy LEF, run `run_synthesis` & `run_floorplan`.
- Configure synthesis (`SYNTH_SIZING`, `MAX_FANOUT`) to improve slack.
- Perform STA via OpenSTA (`pre_sta.conf`, `my_base.sdc`).

---

## Day 5 – Routing, DRC & Final RTL2GDS Steps
**Theory Highlights:**
- Routing types: global vs detailed; overview of routing algorithms (Lee’s, Steiner).
- Design Rule Checking (DRC) and importance of compliance.
- Power Distribution Network planning and routing.

**Lab Snapshot:**
- Maze routing command demos (e.g., `TritonRoute`).
- Running DRC and checking violations.
- Building PDN using power straps connected to standard cells.

---

**End of Report**
