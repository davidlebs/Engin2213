The circuit in this file shows an Adder/Subtractor with overflow like in Checkpoint 1/ Circuit 1, but the major difference
is the usage of MUXs to make this happen. Please check out the previously mentioned circuit for the explanation of how 
a regular Adder/Subtractor works.

A MUX is used for both the overflow logic as well as the 2's complement logic. Starting of with the 2's complement,
we use a 2 to 1 MUX with a switch acting as the enable to send our signal to either add or subtract. A 2 to 1 MUX
when the switch is set to 0 sends a regular B signal to the adder. When the switch is flipped though (in subtraction mode),
the inverted version of B is sent through and the switch signal to the Cin (like in Checkpoint 1/ Circuit 1).

The overflow logic uses a 4 to 1 MUX instead because we need two enable pins, the S4 and A4 (or B4 instead of A4). 

PS. I'm still working on the overflow logic and trying to implement
