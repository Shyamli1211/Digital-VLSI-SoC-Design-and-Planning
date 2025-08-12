# VLSI Physical Design Report – Day 1 to Day 5

---

## Day 1 – Inception of Open-Source EDA, OpenLANE, Sky130 PDK
**Theory Highlights:**
- Overview of open-source tools (OpenLANE, Magic, ngspice, OpenSTA).
- Introduction to Skywater SKY130 PDK and its role.
- Understanding RTL-to-GDSII SoC design flow.

**Lab Snapshot:**
- Environment setup and tool familiarity.
- Basic commands to launch OpenLANE flow (`prep -design`, `run_synthesis`).

---

## Day 2 – Floorplanning & Library Cells
**Theory Highlights:**
- Good vs bad floorplans: core/die area, aspect ratio, utilization factor.
- Macro placement strategies and I/O pin planning.
- Power planning with VDD/VSS rings and decoupling caps.

**Lab Snapshot:**
- `run_floorplan` command.
- Viewing floorplan in Magic (`magic -T sky130A.tech...`).
- Using `S`, `V`, and `Z` keys to navigate and inspect the layout.

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
