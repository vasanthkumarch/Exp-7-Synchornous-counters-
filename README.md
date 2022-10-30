# Exp-6-Synchornous-counters - up counter and down counter 
### AIM: To implement 4 bit up and down counters and validate  functionality.
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 

## UP COUNTER 
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

## DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.
This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![image](https://user-images.githubusercontent.com/36288975/169644844-1a14e123-7228-4ed8-81a9-eb937dff4ac8.png)
4-bit Count Down Counter
### Procedure
```
1.Create module projectname(input ,output) to start the verilog programming.
2.create a if loop condition to increase the count in counter_up function.
3.Similarly, create another loop for the down counter.
4.End the verilog program using keyword endmodule.
5.Get the timing diagram and RTL realization diagram for respective Counters.
```
## Program:
```
Program for flipflops  and verify its truth table in quartus using Verilog programming.
Developed by: H.Syed Abdul Wasih
RegisterNumber:  212221240057
```
### UP COUNTER:
```
module now(input clk,input reset,output[0:3]counter);
reg[0:3] counter_up;
always@(posedge clk or posedge reset)
begin
if(reset)
counter_up <=4'd0;
else
counter_up<=counter_up+4'd1;
end
assign counter=counter_up;
endmodule
```
### DOWN COUNTER:
```
module dc(input clk,input reset,output[0:3]counter);
reg[0:3] counter_down;
always@(posedge clk or posedge reset)
begin
if(reset)
counter_down <=4'd0;
else
counter_down<=counter_down+4'd1;
end
assign counter=counter_down;
endmodule
```
## Output:
### RTL LOGIC UP COUNTER AND DOWN COUNTER: 
![uc-rtl](https://user-images.githubusercontent.com/93427208/169768632-71a6d2bd-960b-499f-be47-786c3e2485a1.png)
![dc-rtl](https://user-images.githubusercontent.com/93427208/169768640-f52e9138-811c-41cb-87eb-4ef82dba554f.png)

### TIMING DIGRAMS FOR COUNTER:
![downtime1](https://user-images.githubusercontent.com/93427208/169768915-394aa9b4-25dd-4e46-b4a2-977fbe090c88.png)

![downtime2](https://user-images.githubusercontent.com/93427208/169768928-b1b707b1-b30d-460c-85b6-2a251b6970bf.png)

### TRUTH TABLE:
![1](https://user-images.githubusercontent.com/91781810/198869113-7671b9ff-4763-4bec-9850-b1df2cae1476.png)
![2](https://user-images.githubusercontent.com/91781810/198869122-14a2576c-7030-4c30-82b3-3857ef4330c3.png)


### RESULT:
Thus 4 bit up and down counters is implemented and its functionality is validated.
