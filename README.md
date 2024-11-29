# 32Bit-ALU_Synthesis

## Aim:

Synthesize 32 Bit ALU design using Constraints and analyse area and Power reports.

## Tool Required:

Functional Simulation: Incisive Simulator (ncvlog, ncelab, ncsim)

Synthesis: Genus

### Step 1: Getting Started

Synthesis requires three files as follows,

◦ Liberty Files (.lib)

◦ Verilog/VHDL Files (.v or .vhdl or .vhd)

Step 2 : Creating an SDC File

•	In your terminal type “gedit input_constraints.sdc” to create an SDC File if you do not have one.
•	The SDC File must contain the following commands;

create_clock -name clk -period 2 -waveform {0 1} [get_ports "clk"] 
set_clock_transition -rise 0.1 [get_clocks "clk"] 
set_clock_transition -fall 0.1 [get_clocks "clk"] 
set_clock_uncertainty 0.01 [get_ports "clk"]
set_input_delay -max 0.8 [get_ports "rst"] -clock [get_clocks "clk"] 
set_output_delay -max 0.8 [get_ports "count"] -clock [get_clocks "clk"]
 
i→ Creates a Clock named “clk” with Time Period 2ns and On Time from t=0 to t=1. 
ii, iii → Sets Clock Rise and Fall time to 100ps.
iv → Sets Clock Uncertainty to 10ps.

v, vi → Sets the maximum limit for I/O port delay to 1ps.

### Step 3 : Performing Synthesis

The Liberty files are present in the library path,

• The Available technology nodes are 180nm ,90nm and 45nm.

• In the terminal, initialise the tools with the following commands if a new terminal is being
used.

◦ csh

◦ source /cadence/install/cshrc

• The tool used for Synthesis is “Genus”. Hence, type “genus -gui” to open the tool.

• Genus Script file with .tcl file Extension commands are executed one by one to synthesize the netlist.

#### Synthesis RTL Schematic :
![image](https://github.com/user-attachments/assets/6ed5040f-516d-4c65-94a1-224e03ed12a4)

#### Area report:
![image](https://github.com/user-attachments/assets/331528f0-f6b4-45a3-ab9a-7d00196ad03e)

#### Power Report:
![image](https://github.com/user-attachments/assets/c30e9715-6500-4b89-8a9b-553d2a4a7a47)

#### Result: 

The generic netlist of 32 bit ALU  has been created, and area, power reports have been tabulated and generated using Genus.
