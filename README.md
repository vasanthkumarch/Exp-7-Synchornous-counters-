# Exp-6-Synchornous-counters - up counter and down counter 
## Name: Loshini.G
## Reference no: 212223220051
## AIM: To implement 4 bit up and down counters and validate  functionality.
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
## THEORY: 

### UP COUNTER 
The counter is a digital sequential circuit and here it is a 4 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.



 
 

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:

 
 

Four-bit “Up” Counter
![image](https://user-images.githubusercontent.com/36288975/169644758-b2f4339d-9532-40c5-af40-8f4f8c942e2c.png)



### DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![image](https://user-images.githubusercontent.com/36288975/169644844-1a14e123-7228-4ed8-81a9-eb937dff4ac8.png)


4-bit Count Down Counter
## Procedure:
/*
### 1.	Create a New Project:

Open Quartus and create a new project by selecting "File" > "New Project Wizard."
Follow the wizard's instructions to set up your project, including specifying the project name, location, and target device (FPGA).
### 2.	Create a New Design File:

Once the project is created, right-click on the project name in the Project Navigator and select "Add New File."
Choose "Verilog HDL File" or "VHDL File," depending on your chosen hardware description language.
### 3.	Write the Combinational Logic Code:

Open the newly created Verilog or VHDL file and write the code for your combinational logic.
### 4.	Compile the Project:
To compile the project, click on "Processing" > "Start Compilation" in the menu.
Quartus will analyze your code, synthesize it into a netlist, and perform optimizations based on your target FPGA device.
### 5.	Analyze and Fix Errors:

If there are any errors or warnings during the compilation process, Quartus will display them in the Messages window.
Review and fix any issues in your code if necessary. View the RTL diagram.
### 6.	Verification:

Click on "File" > "New" > "Verification/Debugging Files" > "University Program VWF".
 
Once Waveform is created Right Click on the Input/Output Panel > " Insert Node or Bus" > Click on Node Finder > Click On "List" > Select All.
Give the Input Combinations according to the Truth Table amd then simulate the
Output Waveform.

 */



## PROGRAM :
/*
```

Program for flipflops  and verify its truth table in quartus using Verilog programming.
Developed by: Loshini.G
RegisterNumber: 212223220051
##UP COUNTER:
module upcounter(clk,A);
input clk;
output reg[0:3]A;
always@(posedge clk)
begin
A[0]=((((A[1])&(A[2]))&A[3])^A[0]);
A[1]=(((A[2])&(A[3]))^A[1]);
A[2]=((A[3])^A[2]);
A[3]=1^A[3];
end
endmodule
##DOWN COUNTER:
module downcounter(clk,A);
input clk;
output reg [3:0]A;
always@(posedge clk)
begin
   A[3]=(((~A[0])&(~A[1])&(~A[2]))^A[3]);
	A[2]=(((~A[0])&(~A[1]))^A[2]);
	A[1]=(~A[0])^A[1];
	A[0]=1^A[0];
end
endmodule
```
*/
## RTL LOGIC UP COUNTER AND DOWN COUNTER:
### UP COUNTER:
![upcounter rtl](https://github.com/vasanthkumarch/Exp-7-Synchornous-counters-/assets/150007305/9296e760-cbd4-41af-8036-bad5ab15c637)

### DOWN COUNTER:
![downcounter rtl](https://github.com/vasanthkumarch/Exp-7-Synchornous-counters-/assets/150007305/e4bef68d-deed-4bd1-9065-edb9145ba812)


## TIMING DIGRAMS FOR COUNTER:
### UP COUNTER:
![upcounter wf](https://github.com/vasanthkumarch/Exp-7-Synchornous-counters-/assets/150007305/0bf1bdb6-f1fa-42ef-98df-786347b56e64)

### DOWN COUNTER:
![downcounter wf](https://github.com/vasanthkumarch/Exp-7-Synchornous-counters-/assets/150007305/45ac3c4c-d99d-4e7b-bea1-91d195d2cf71)


## TRUTH TABLE:
### UP COUNTER:
![Screenshot 2024-01-02 192147](https://github.com/vasanthkumarch/Exp-7-Synchornous-counters-/assets/150007305/29de4c4c-3dfa-4105-9935-5074c697a5a5)


### DOWN COUNTER:
![Screenshot 2024-01-02 192413](https://github.com/vasanthkumarch/Exp-7-Synchornous-counters-/assets/150007305/55818388-7449-4522-b592-e8cf9cc91de4)




### RESULTS:
By this we have verified the truth table of 4-bit up-counter using verilog
