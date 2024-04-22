SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

AIM: 
 To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Vivado software.

APPARATUS REQUIRED:
Vivado™ ML 2023.2

**LOGIC DIAGRAM**

ENCODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)


DECODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b)


MULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/427f75b2-8e67-44b9-ac45-a66651787436)


DEMULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/1c45a7fc-08ac-4f76-87f2-c084e7150557)


MAGNITUDE COMPARATOR

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2)


  
PROCEDURE:
Open Vivado: Launch Xilinx Vivado software on your computer.

Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.

VERILOG CODE
1.
DECODER 3TO8:
```
module decoder_8(a,b,c,y);
input a,b,c; 
output[7:0]y; 
and gl(y[0],(~a),(~b),(~c)); 
and g2(y[1],(~a),(~b),(c)); 
and g3(y[2],(~a),(b),(~c));
and g4(y[3],(~a),(b),(c));
and g5(y[4],(a),(~b),(~c));
and g6(y[5],(a), (~b), (c));
and g7(y[6], (a), (b), (~c)); 
and g8(y[7], (a), (b), (c));
endmodule
```
OUTPUT:
SIMULATION:
![image](https://github.com/Mohanasankaran/VLSI-LAB-EXP-2/assets/161284142/fc413541-851d-424f-8bcd-28cb3d8d9744)
ELABORATED DESIGN:
![image](https://github.com/Mohanasankaran/VLSI-LAB-EXP-2/assets/161284142/334a77d8-a0f1-46ce-9606-2d86d7019570)

2.
DEMULTIPLEXER 1TO8:
```
module demux(in,s0,s1,s2,d0,d1,d2,d3,d4,d5,d6,d7);
input in,s0,s1,s2;
output d0,d1,d2,d3,d4,d5,d6,d7;
assign d0=(in & ~s2 & ~s1 &~s0),
d1=(in & ~s2 & ~s1 &s0),
d2=(in & ~s2 & s1 &~s0),
d3=(in & ~s2 & s1 &s0),
d4=(in & s2 & ~s1 &~s0),
d5=(in & s2 & ~s1 &s0),
d6=(in & s2 & s1 &~s0),
d7=(in & s2 & s1 &s0);
endmodule
```
OUTPUT:
SIMULATION:
![image](https://github.com/Mohanasankaran/VLSI-LAB-EXP-2/assets/161284142/b14987d3-15ff-492a-b043-2cd6b559bbe2)
ELABORATED DESIGN:
![image](https://github.com/Mohanasankaran/VLSI-LAB-EXP-2/assets/161284142/98d1e465-54fb-4a81-bc8a-ca85a7ed51ca)

3.
ENCODER 8TO3:
```
module encoder_8_to_3(a0,a1,a2,d0,d1,d2,d3,d4,d5,d6,d7);�input d0,d1,d2,d3,d4,d5,d6,d7;
output a0,a1,a2;
or g1(a0,d1,d3,d5,d7);
or g2(a1,d2,d3,d6,d7);
or g3(a2,d4,d5,d6,d7);
endmodule
```
OUTPUT:
SIMULATION:
![image](https://github.com/Mohanasankaran/VLSI-LAB-EXP-2/assets/161284142/b61d22e0-3925-471f-be48-ba2d8729166b)
ELABORATED DESIGN:
![image](https://github.com/Mohanasankaran/VLSI-LAB-EXP-2/assets/161284142/d71e6b2c-dfee-4d43-b311-bac2d2c37644)

4.
MAGNITUDE COMPARATOR:
```
module comparator(a,b,eq,lt,gt);
input [3:0] a,b;
output reg eq,lt,gt;
always @(a,b)
begin
 if (a==b)
 begin
  eq = 1'b1;
  lt = 1'b0;
  gt = 1'b0;
 end
 else if (a>b)
begin
  eq = 1'b0;
  lt = 1'b0;
  gt = 1'b1;
 end
 else
 begin
  eq = 1'b0;
  lt = 1'b1;
  gt = 1'b0;
 end
end 
endmodule
```
OUTPUT:
SIMULATION:
![image](https://github.com/Mohanasankaran/VLSI-LAB-EXP-2/assets/161284142/5b87e3d7-b420-49d4-9018-02c399457c6e)
ELABORATED DESIGN:
![image](https://github.com/Mohanasankaran/VLSI-LAB-EXP-2/assets/161284142/aae1897f-5a93-41f9-99ad-6cde7920539e)

5.
MULTIPLEXER 8TO1:
```
module mux(a,b,c,d,s0,s1,y);
input a,b,c,d,s0,s1;
output y;
assign y=s1 ?(s0?d:c):(s0?b:a);
endmodule
```
OUTPUT:
SIMULATION:
![image](https://github.com/Mohanasankaran/VLSI-LAB-EXP-2/assets/161284142/21efb47d-196c-48a5-ae8f-161e906a46e2)
ELABORATED DESIGN:

![image](https://github.com/Mohanasankaran/VLSI-LAB-EXP-2/assets/161284142/026c97ae-b5e4-4203-8cef-750ac4d79d0b)



RESULT
The Simulation and Synthesis Logic Gates,Adders and Subtractor is successfully verified using Vivado Software


