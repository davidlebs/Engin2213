The circuit shown in this folder is a 4-bit unsigned multiplier.

The circuit is derived from the idea of binary multiplication and the fact that addition is communicative.
In binary multiplication, we take the LSB (least significant bit) of the bottom row and multiply it with the 
top row going from LSB to MSB (most signifcant bit) like in decimal multiplication. We then continue on with this 
pattern, going from LSB to MSB of the bottom row and multiplying with each number of the top row. The truth table
for this idea is found in 

<img width="666" height="664" alt="image" src="https://github.com/user-attachments/assets/a7d259ec-ad00-446a-ad8e-ad7aa433df95" />(Multiplication Truth Table.png).

We see how whenever B1 is 0, the output of any sum is always going to be 0. If B1 is 1, the output is A4-A1. 
This pattern continues down to B4. At the end, we add up all numbers and since addition is communicative, 
the order in which we add the numbers doesn't matter. For the LSB LED, we give it an input of A1B1 as in 
multiplication, if another term is added below, we add a zero so the answer for the column just comes out to A1B1. 
The same logic is applied for the second adder. The summationand Cout is then carried into the next adder 
to add with the ongoing addition. The final adder finally outputs the rest of the LEDS with Cout of the 
last adder being the MSB.

KiCAD Schematic:
<img width="1096" height="999" alt="image" src="https://github.com/user-attachments/assets/94c95a93-6e1e-450a-a6df-d9eef8a0b388" />

TinkerCAD Design:
<img width="1518" height="936" alt="image" src="https://github.com/user-attachments/assets/9932191b-7fd1-49ca-a444-2669c200ad7d" />

TinkerCAD Link: 
https://www.tinkercad.com/things/0AATe8rBNMQ-unsigned-multiplier-portfolio-1/editel?returnTo=https%3A%2F%2Fwww.tinkercad.com%2Fdashboard
