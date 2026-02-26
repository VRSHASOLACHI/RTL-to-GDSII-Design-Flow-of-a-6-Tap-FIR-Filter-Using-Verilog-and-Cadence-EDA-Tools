# RTL-to-GDSII-Design-Flow-of-a-6-Tap-FIR-Filter-Using-Verilog-and-Cadence-EDA-Tools
This project focuses on the complete ASIC design and implementation of an 8-bit, 6-tap Finite Impulse Response (FIR) filter using Verilog HDL and industry-standard Cadence EDA tools. 

# FIR Filter Implementation (ASIC Flow)

## Project Overview
This project presents the design, verification, synthesis, and physical implementation of an 8-bit, 6-tap FIR (Finite Impulse Response) filter using Verilog HDL and a complete ASIC design flow.  
The implementation spans from RTL design and simulation to place & route, timing closure, and power analysis using Cadence EDA tools.

---

## Objectives
- Design and implement a 6-tap FIR filter using Verilog  
- Perform RTL functional verification  
- Synthesize the design using Cadence Genus  
- Carry out floorplanning, placement, and routing using Cadence Innovus  
- Perform timing, power, and rail analysis  
- Verify functionality using pre-layout and post-layout simulations  

---

## Tools & Platforms Used
- Cadence Genus – RTL Synthesis  
- Cadence NCLaunch – Simulation  
- Cadence Innovus – Place & Route  
- Cadence Stylus / QRC – Physical verification & parasitic extraction  
- EDA Playground (Icarus Verilog) – Functional simulation  

---

## FIR Filter Architecture
The FIR filter is implemented in direct form, consisting of:
- Delay elements (D flip-flops)  
- Constant coefficient multipliers  
- Adder tree (MAC structure)  

### FIR Equation
y[n] = h0·x[n] + h1·x[n−1] + h2·x[n−2] + h3·x[n−3] + h4·x[n−4] + h5·x[n−5]

### Coefficients Used
h = {3, 4, 5, 4, 3, 3}


---

## Functional Operation
- Input samples are stored in a shift register  
- Each delayed sample is multiplied by a fixed coefficient  
- Products are accumulated to generate the output  
- Multiply–accumulate (MAC) logic is implemented using shift-and-add  

---

## Manual Verification
Manual convolution calculations were performed to validate the FIR equation and confirm correctness of simulation outputs for multiple input samples.

---

## RTL Design (Verilog)
- 8-bit input data  
- 16-bit output to accommodate accumulation  
- Modular design consisting of:
  - FIR filter module  
  - 8-bit D flip-flop delay modules  

RTL functionality was verified using Icarus Verilog and Cadence NCLaunch.

---

## Functional Simulation
### Observations
- Correct propagation of input samples through delay registers  
- Output reflects the weighted sum of current and delayed inputs  
- Internal tap values (d1–d5) were verified  

Functional correctness was confirmed.

---

## Synthesis Results (Cadence Genus)
- Technology: GPDK 90nm  
- Positive timing slack of 37,740 ps  
- Design meets all timing constraints  
- Area optimized during synthesis  

### Area
- Total area: 703.152 units  

### Power Analysis
- Dynamic, leakage, and internal power components analyzed  
- Contributions from registers, logic, clock, and memory considered  

---

## Physical Design (Cadence Innovus)

### Power Planning
- VDD/VSS power stripes inserted  
- Ensured uniform power distribution and minimized IR drop  

### Placement & Optimization
- Timing-driven placement using place_opt_design  
- No congestion issues observed  
- No setup or hold violations  

### Routing
- Routing rule table applied  
- DRC-clean routing achieved  
- Full connectivity verified  

---

## Timing Closure
### Setup & Hold Analysis
- Positive setup slack  
- Positive hold slack  
- No violating paths  
- Timing closure successfully achieved  

---

## Power & Rail Analysis
- Power integrity validated  
- IR drop and electromigration checks performed  
- Power delivery network meets reliability requirements  

---

## Filler Cell Insertion
- Filler cells inserted to:
  - Maintain well continuity  
  - Avoid DRC violations  
  - Ensure power rail connectivity  

---

## Final Results
- Functional correctness verified at RTL and post-layout stages  
- Timing closure achieved with positive slack  
- Clean routing with zero DRC violations  
- Robust power integrity confirmed  

---

## Conclusion
This project demonstrates a complete ASIC implementation flow for a 6-tap FIR filter, covering RTL design, synthesis, place and route, and sign-off checks.  
The design meets functional, timing, and physical constraints and serves as a strong reference for VLSI front-end and back-end integration.

---

## References
1. Design and Implementation of 6-Tap FIR Filter Using MAC for Low Power Applications,  
   International Journal for Research in Applied Science & Engineering Technology (IJRASET),  
   Volume 10, Issue VI, June 2022  
2. Cadence Genus and Innovus User Documentation  
