# Day 04 – Pre-layout timing analysis and importance of good clock tree

Timing modelling using delay tables

Day 04 – Lectures 55 to 62
Lecture 55 – Lab Steps to Convert Grid Info to Track Info
This lab focuses on converting grid information into track information for routing.
Steps:

Open the design in the layout tool.

Identify grid definitions for routing layers.

Use the tool command to extract track patterns from grid data.

Verify track pitch and offset for each metal layer.

Lecture 56 – Floorplanning Basics
Floorplanning is the process of defining the physical layout of a chip before placement and routing.
Key objectives:

Arrange blocks and macros efficiently to meet performance, power, and area goals.

Ensure enough space for routing, clock distribution, and power delivery.

Plan I/O pad locations based on signal and power needs.

Lecture 57 – Core and Die Area
Die Area – The total size of the chip, including core and I/O ring.

Core Area – The central region where standard cells and macros are placed.
Relation:

Die area ≥ Core area + I/O and power ring.

Larger die area increases cost but may be necessary for performance or routing.

Lecture 58 – Aspect Ratio in Floorplanning
Aspect Ratio (AR) = Core Height / Core Width.

AR = 1 → Square core, generally preferred for balanced routing.

AR > 1 → Tall and narrow core.

AR < 1 → Wide and short core.
Impact:

AR affects wire length, congestion, and timing.

Certain designs favor non-square shapes for specific routing advantages.

Lecture 59 – Utilization Factor
Utilization Factor = (Area occupied by standard cells) / (Total core area).

Typical range: 60%–80%.

Higher utilization → Smaller die size but risk of routing congestion.

Lower utilization → Easier routing but larger die and higher cost.

Lecture 60 – Core to Die Margin
Margin between core boundary and die edge allows space for:

I/O pads

Power/ground rings

ESD protection structures

Proper margin ensures electrical and mechanical stability of the chip.

Lecture 61 – Pre-Placement Considerations
Before starting placement:

Finalize floorplan dimensions and aspect ratio.

Ensure power grid and I/O locations are fixed.

Place macros in optimal positions with proper spacing.

Reserve channels for high-fanout nets like clock and reset.

Lecture 62 – Macro Placement Guidelines
Place large macros near the core boundary to ease routing.

Group macros with heavy interconnects close to reduce wire length.

Avoid placing macros in the center to prevent routing blockages.

Maintain keep-out zones around macros for buffer insertion and routing.






