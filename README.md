# VLSI-LAB-EXPERIMENTS
AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

APPARATUS REQUIRED: Xilinx 14.7 Spartan6 FPGA

PROCEDURE: STEP:1 Start the Xilinx navigator, Select and Name the New project. STEP:2 Select the device family, device, package and speed. STEP:3 Select new source in the New Project and select Verilog Module as the Source type. STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it. STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax. STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window. STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here. STEP:12 Load the Bit file into the SPARTAN 6 FPGA STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

Logic Diagram :

Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)



Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)



Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)



8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)



VERILOG CODE:

logic gates:
~~~
module logicgates(a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b);  
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
~~~
output:
![image](https://github.com/Gokuls2003/VLSI-LAB-EXP-1/assets/159005418/f2c10c00-7a6d-4949-b5a5-06ca9c943d48)


elaborated design:
![image](https://github.com/Gokuls2003/VLSI-LAB-EXP-1/assets/159005418/f7a7aa64-7ca7-49c4-a753-b157d06b7b67)



--------------------------------------------------------------------------------------------------------------------------------------------------------------------

half adder:
~~~
module half_adder(a,b,sum,carry);
input a,b;
output sum,carry; 
xor(sum,a,b);
and(carry,a,b);
endmodule
~~~
output:
![image](https://github.com/Gokuls2003/VLSI-LAB-EXP-1/assets/159005418/b57a880f-2872-4347-9ac1-6d81fbb4abe1)


elaborated design:
![image](https://github.com/Gokuls2003/VLSI-LAB-EXP-1/assets/159005418/215abfba-2df5-4e18-8634-e77f97c78094)

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

Full Adder:
~~~
module fulladder(S, Co, X, Y, Ci);
  input X, Y, Ci;
  output S, Co;
  wire w1,w2,w3;
  //Structural code for one bit full adder
  xor G1(w1, X, Y);
  xor G2(S, w1, Ci);
  and G3(w2, w1, Ci);
  and G4(w3, X, Y);
  or G5(Co, w2, w3);
endmodule
module rippe_adder(S, Cout, X, Y,Cin);
 input [3:0] X, Y;// Two 4-bit inputs
 input Cin;
 output [3:0] S;
 output Cout;
 wire w1, w2, w3;
 fulladder u1(S[0], w1,X[0], Y[0], Cin);
 fulladder u2(S[1], w2,X[1], Y[1], w1);
 fulladder u3(S[2], w3,X[2], Y[2], w2);
 fulladder u4(S[3], Cout,X[3], Y[3], w3);
endmodule
~~~
otput:
![image](https://github.com/Gokuls2003/VLSI-LAB-EXP-1/assets/159005418/d703c401-bd5c-4a03-9325-819aa6020d4f)

elaborated design:
![image](https://github.com/Gokuls2003/VLSI-LAB-EXP-1/assets/159005418/aedda4d1-1f4b-42f4-9808-f8844fd2fcae)

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

Half Subtractor:
~~~
module halfsubtractor( D,Bo,A,B);
input A,B;
output D,Bo;
wire w1;
xor (D,A,B);
not (w1,B);
and (Bo,B,w1);
endmodule
~~~
oyput:
![image](https://github.com/Gokuls2003/VLSI-LAB-EXP-1/assets/159005418/7031b6e2-f8ef-4ba2-87bc-654563f7a2ec)

elaborated design:
![image](https://github.com/Gokuls2003/VLSI-LAB-EXP-1/assets/159005418/bf4722b5-70c3-4687-8b8c-93c345fa1e04)

-----------------------------------------------------------------------------------------------------------------------------------------------------------------

Full Subtractor:
~~~
module full_subtractor(a, b, c,D, Bout);
input a, b, c;
output D, Bout;
  assign D = a ^ b ^ c;
  assign Bout = (~a & b) | (~(a ^ b) & c);
endmodule  
~~~
output:
![image](https://github.com/Gokuls2003/VLSI-LAB-EXP-1/assets/159005418/5a934534-9fe1-4c10-83f7-e8a56f5d24a0)

elaborated design:
![image](https://github.com/Gokuls2003/VLSI-LAB-EXP-1/assets/159005418/64a5317d-2d50-4259-a631-0bdb7030037d)

-----------------------------------------------------------------------------------------------------------------------------------------------------------------

4 bit ripple carry adder
```
module rippe_adder(S, Cout, X, Y,Cin);
input [3:0] X, Y;// Two 4-bit inputs
input Cin;
output [3:0] S;
output Cout;
wire wl, w2, w3;

fulladder u1(S[0], w1,X[0], Y[0], Cin);
fulladder u2(S[1], w2,X[1], Y[1], w1);
fulladder u3(S[2], w3,X[2], Y[2], w2);
fulladder u4(S[3], Cout,X[3], Y[3], w3);
endmodule
module fulladder(S, Co, X, Y, Ci);
input X, Y, Ci;
output S, Co;
wire w1,w2,w3;
//Structural code for one bit full adder 
xor G1(wl, X, Y);
xor G2(S, w1, Ci);
and G3(w2, w1, Ci);
and G4(w3, X, Y);
or  G5(Co, w2, w3);
endmodule
```
output:
![image](https://github.com/Gokuls2003/VLSI-LAB-EXP-1/assets/159005418/73c5e673-5e01-4356-bf1e-9eb15ee116e9)
elaborated design:
![image](https://github.com/Gokuls2003/VLSI-LAB-EXP-1/assets/159005418/8f576134-1f61-47bd-9896-cc096d0b7049)


8 bit ripple carry adder:
~~~
module fulladder(S, Co, X, Y, Ci);
  input X, Y, Ci;
  output S, Co;
  wire w1,w2,w3;
  //Structural code for one bit full adder
  xor G1(w1, X, Y);
  xor G2(S, w1, Ci);
  and G3(w2, w1, Ci);
  and G4(w3, X, Y);
  or G5(Co, w2, w3);
endmodule
module rippe_adder(S, Cout, X, Y,Cin);
 input [7:0] X, Y;// Two 4-bit inputs
 input Cin;
 output [7:0] S;
 output Cout;
 wire w1, w2, w3, w4, w5, w6, w7;
 // instantiating 8 1-bit full adders in Verilog
 fulladder u1(S[0], w1,X[0], Y[0], Cin);
 fulladder u2(S[1], w2,X[1], Y[1], w1);
 fulladder u3(S[2], w3,X[2], Y[2], w2);
 fulladder u4(S[3], w4,X[3], Y[3], w3);
 fulladder u5(S[4], w5,X[4], Y[4], w4);
 fulladder u6(S[5], w6,X[5], Y[5], w5);
 fulladder u7(S[6], w7,X[6], Y[6], w6);
 fulladder u8(S[7], Cout,X[7], Y[7], w7);
endmodule
~~~
output:
![image](https://github.com/Gokuls2003/VLSI-LAB-EXP-1/assets/159005418/294df087-07fa-4c49-b2d9-51b322dcbd78)

elaborated design:
![image](https://github.com/Gokuls2003/VLSI-LAB-EXP-1/assets/159005418/ceb72ca2-fb92-4e31-b9cb-ad732a9a743a)

-----------------------------------------------------------------------------------------------------------------------------------------------------------------



RESULT:
 simulation and synthesis of Logic Gates,Adders and Subtractor are succesfully verified using Xilinx ISE.


