# Project 1: Standard-Cell Design, Technology Mapping & Physical Implementation of a RISC-V SoC

> Sky130 PDK-Based Standard-Cell Design and RTL-to-GDSII Implementation of the PicoRV32a RISC-V Processor

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Tool](https://img.shields.io/badge/Tool-OpenLANE-blue)
![PDK](https://img.shields.io/badge/PDK-Sky130-orange)
![Technology](https://img.shields.io/badge/Technology-130nm%20CMOS-purple)
![Language](https://img.shields.io/badge/Language-Verilog%20HDL-purple)
![Program](https://img.shields.io/badge/Program-NASSCOM%20FutureSkills%20Prime-red)
![License](https://img.shields.io/badge/License-Apache%202.0-blue)

## 🔍 Overview

- Complete **RTL-to-GDSII physical implementation** of the **PicoRV32a RISC-V processor** using the **OpenLANE** automated EDA flow and the **Google SkyWater 130nm (Sky130) CMOS PDK**.
- Explores the relationship between RTL synthesis, standard-cell technology mapping and physical implementation, covering the digital IC implementation flow from Verilog RTL to layout generation.
- A key component is the **custom standard-cell design and integration (sky130_vsdinv)**, involving transistor-level layout, SPICE simulation, LEF extraction and integration into the Sky130-based implementation flow.
- Physical implementation includes floorplanning, placement, timing optimisation through engineering change orders (ECOs), clock tree synthesis, power distribution, detailed routing, post-route parasitic extraction and timing analysis.

## 🛠️ Tools & Technology Stack

| Category | Tool / Technology |
|---|---|
| Physical Design Flow | OpenLANE |
| Process Design Kit | Google SkyWater Sky130 (sky130A) |
| Technology | 130nm CMOS |
| Design | PicoRV32a RISC-V Processor |
| RTL Synthesis | Yosys + ABC |
| Standard-Cell Mapping | ABC + Sky130 Standard-Cell Library |
| Static Timing Analysis | OpenSTA |
| Placement & Physical Design | OpenROAD, RePlAce |
| Clock Tree Synthesis | TritonCTS |
| Routing | FastRoute, TritonRoute |
| Layout Design & DRC | Magic VLSI |
| Parasitic Extraction | SPEF Extractor |
| SPICE Simulation | Ngspice |
| Layout Versus Schematic | Netgen |
| Hardware Description Language | Verilog HDL |
| Operating System | Ubuntu Linux |

## ⚙️ Complete Design Flow

| Stage | Tool | Description | Status |
|---|---|---|---|
| RTL Synthesis | Yosys + ABC | RTL synthesis and technology mapping to Sky130 standard cells | ✅ Complete |
| Floorplan & Power | OpenROAD | Die and core definition, utilisation planning and IO placement | ✅ Complete |
| Placement | OpenROAD | Standard-cell placement and congestion optimisation | ✅ Complete |
| Custom Standard-Cell Design | Magic, Ngspice | sky130_vsdinv layout, SPICE simulation and LEF extraction | ✅ Complete |
| Timing Optimisation | OpenSTA | Timing analysis, synthesis tuning and cell-sizing ECOs | ✅ Complete |
| Clock Tree Synthesis | TritonCTS | Clock-tree construction, buffer insertion and skew optimisation | ✅ Complete |
| Power Distribution | OpenROAD | Power distribution network with rings, straps and cell rails | ✅ Complete |
| Routing | FastRoute, TritonRoute | Global and detailed signal routing | ✅ Complete |
| Parasitic Extraction | SPEF Extractor | Post-route RC parasitic extraction | ✅ Complete |
| Post-Route Timing Analysis | OpenSTA | Timing evaluation using extracted parasitics and propagated clock information | ✅ Complete |
| GDSII Generation | Magic | Layout stream-out and physical verification | ✅ Complete |

## 📊 Key Results

| Metric | Value |
|---|---|
| Design | PicoRV32a RISC-V Processor |
| Process Technology | 130nm CMOS (Sky130 PDK) |
| Clock Period | 24.73 ns |
| Clock Frequency | 40.44 MHz |
| Total Standard Cells | 17,108 |
| Flip-Flop Count | 1,613 (9.43%) |
| Chip Area | 181,510.33 µm² |
| Die Area | 731.18 × 741.90 µm |
| Core Area | 719.90 × 718.08 µm |
| Metal Layers | 6 — li1, met1, met2, met3, met4, met5 |
| Custom Standard Cell | sky130_vsdinv (Custom Inverter) |
| Post-Synthesis WNS | 0.00 ns |
| Post-Synthesis TNS | 0.00 ns |
| Post-Route WNS | 0.00 ns |
| Post-Route TNS | 0.00 ns |
| Routing Runtime | 25 minutes 21 seconds |
| DRC Violations | 0 |
| LVS Status | Clean |
| GDSII | Generated — DRC/LVS-verified layout |

## 📁 Repository Structure

```text
📁 Project-1-Standard-Cell-Design-Technology-Mapping-and-Physical-Implementation-of-RISC-V-SoC
├── 📁 01 : Synthesis          → RTL synthesis, technology mapping and netlist
├── 📁 02 : Floorplan          → Floorplan, IO placement and Magic layout
├── 📁 03 : Placement          → Standard-cell placement and congestion optimisation
├── 📁 04 : Custom cell        → sky130_vsdinv design, SPICE simulation and LEF
├── 📁 05 : Timing closure     → Timing analysis, slack optimisation and ECO
├── 📁 06 : CTS                → Clock tree synthesis and verification
├── 📁 07 : PDN                → Power distribution network implementation
├── 📁 08 : Routing            → Global and detailed routing
├── 📁 09 : GDSII              → SPEF extraction and final GDSII generation
└── 📄 README.md
```

## 📝 Stage Details

**01 — RTL Synthesis & Technology Mapping** &nbsp;|&nbsp; `Yosys` `ABC` `OpenSTA`

Verilog RTL synthesised using **Yosys**, with **ABC technology mapping** to the Sky130 standard-cell library. OpenLANE environment initialised and design hierarchy verified. Synthesis reports analysed to evaluate mapped cell utilisation, area and initial timing characteristics. The resulting gate-level netlist served as the input for subsequent physical implementation.

> 📁 [View Implementation Results](./01%20:%20Synthesis)

**02 — Floorplan & Physical Design Setup** &nbsp;|&nbsp; `OpenROAD` `Magic`

Die dimensions, core area and utilisation defined according to the physical design configuration. Standard-cell rows generated and aligned with Sky130 routing tracks. IO pins placed and verified. The resulting floorplan inspected in **Magic** to examine row orientation, spacing and pin accessibility.

> 📁 [View Implementation Results](./02%20:%20Floorplan)

**03 — Standard-Cell Placement** &nbsp;|&nbsp; `OpenROAD` `RePlAce`

Congestion-aware global placement performed using **RePlAce**. Sky130 standard cells placed and legalised within the defined core area. Placement density and routing resource availability evaluated before proceeding to clock tree synthesis and subsequent physical implementation stages.

> 📁 [View Implementation Results](./03%20:%20Placement)

**04 — Custom Standard-Cell Design & Integration** &nbsp;|&nbsp; `Magic` `Ngspice` `Sky130`

Custom inverter cell **sky130_vsdinv** designed from scratch in **Magic**, following Sky130 design-rule requirements. Transistor-level layout created, and the corresponding SPICE netlist extracted and simulated using **Ngspice**. Cell timing characterised using Sky130 Liberty files. LEF extracted and integrated into the OpenLANE flow, with the custom cell verified during post-synthesis and post-CTS implementation.

> 📁 [View Implementation Results](./04%20:%20Custom%20cell)

**05 — Timing Analysis & Optimisation** &nbsp;|&nbsp; `OpenSTA` `ECO`

Timing violations and critical paths analysed using **OpenSTA**. Synthesis configuration parameters, including `SYNTH_STRATEGY`, `SYNTH_BUFFERING` and `SYNTH_SIZING`, adjusted to improve timing behaviour. Engineering change orders (ECOs), including cell upsizing on critical paths, applied to address timing constraints. WNS and TNS evaluated throughout the optimisation process.

> 📁 [View Implementation Results](./05%20:%20Timing%20closure)

**06 — Clock Tree Synthesis** &nbsp;|&nbsp; `TritonCTS` `OpenSTA`

Clock tree constructed using **TritonCTS**, with clock buffers inserted to distribute the clock signal across sequential elements. Buffer drive strengths evaluated to understand their impact on clock slew, skew, area and power. Propagated clock information incorporated into timing analysis, with post-CTS hold timing verified.

> 📁 [View Implementation Results](./06%20:%20CTS)

**07 — Power Distribution Network** &nbsp;|&nbsp; `OpenROAD` `Magic`

Power distribution network generated using `gen_pdn`. Power rings, straps and standard-cell power rails implemented across the design. Via connectivity examined at strap intersections, and custom inverter power-rail connectivity inspected in **Magic** before signal routing.

> 📁 [View Implementation Results](./07%20:%20PDN)

**08 — Global & Detailed Routing** &nbsp;|&nbsp; `FastRoute` `TritonRoute`

Global routing performed using **FastRoute** to plan interconnections across the routing grid. Detailed routing completed using **TritonRoute**, generating physical metal interconnects and vias. Iterative routing and optimisation passes performed to achieve zero reported routing violations.

> 📁 [View Implementation Results](./08%20:%20Routing)

**09 — Parasitic Extraction & GDSII Generation** &nbsp;|&nbsp; `SPEF Extractor` `OpenSTA` `Magic` `Netgen`

Post-route parasitic extraction performed using **SPEF Extractor**, generating resistance and capacitance information for routed nets. Post-route timing analysis executed using the extracted parasitics and propagated clock information to evaluate setup and hold timing. Final layout streamed out in **GDSII format using Magic**, with physical verification results showing zero DRC violations and a clean LVS result using Netgen.

> 📁 [View Implementation Results](./09%20:%20GDSII)

## 📚 References

| **Category** | **Reference** |
|:---|:---|
| **Custom Standard-Cell Design** | [vsdstdcelldesign by Nickson Jose](https://github.com/nickson-jose/vsdstdcelldesign) |
| **Process Design Kit** | [Google SkyWater Sky130 PDK](https://github.com/google/skywater-pdk) |
| **Physical Design Flow** | [OpenLANE by efabless](https://github.com/efabless/openlane) |

## 📄 License

This project is licensed under the **Apache License 2.0** — as used by the OpenLANE flow developed by [efabless corporation](https://github.com/efabless/openlane).

## 🤝 Connect

| **Author** | Preetham SK |
|:---|:---|
| **Program** | NASSCOM FutureSkills Prime — VSD (VLSI System Design) |
| **LinkedIn** | [linkedin.com/in/preethamsk16](https://www.linkedin.com/in/preethamsk16) |
| **GitHub** | [github.com/PreethamSK163](https://github.com/PreethamSK163) |
| **Portfolio** | [preethamsk163.github.io](https://preethamsk163.github.io) |
| **Email** | skpreetham16@gmail.com |
