SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

AIM: 
 To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE.

APPARATUS REQUIRED:
Xilinx 14.7
Spartan6 FPGA

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
STEP:1  Start  the Xilinx navigator, Select and Name the New project.
STEP:2  Select the device family, device, package and speed.       
STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       
STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.
STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.

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
![image](https://github.com/Mohanasankaran/VLSI-LAB-EXP-2/assets/161284142/32970e9e-2140-4911-b6c4-dea5f2e5d576)


RESULT


