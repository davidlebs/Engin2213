TinkerCAD Link: https://www.tinkercad.com/things/jkgjS5CNosi-2s-adder-subtractor-w-overflow-portfolio-1/editel?returnTo=%2Fthings%2FjkgjS5CNosi-2s-adder-subtractor-w-overflow-portfolio-1

The circuit shown in this folder is a 4-bit 2's complement adder-subtractor with an overflow LED. 

Tackling the adding component first, this circuit adds by using a simple adder chip (74LS283) and taking each input (A4-A1 and B4-B1) 
and wiring it with the correct input on the adder chip (A4 from dipswitch to A4 on adder chip and so on). 
This gives us the addition summation in binary format.



Moving on to the subtraction aspect, the circuit simply adds a negative number (A + (-B)). This is done with the use of an XOR chip as the truth table alligns with our goals.
The truth table of an XOR chip is 

<img width="245" height="176" alt="image" src="https://github.com/user-attachments/assets/3831234d-b4d8-43d6-ba6d-c175542a8cca" />(XOR Truth Table.webp)

Changing the variables of A and B to Switch and B respectively, we see how whenever the switch is off,
B acts as B, meaning when B is 0 the output is 0 and when B is 1 the output is 1.
When the switch is on, it acts as an inverter, flipping B's value. 
The switch is also connected to Cin of the adder chip, basically adding a value of 1 when the switch is on. 
This therefore acts as flipping the number into its negative component, and then the addition is carried out as previously stated. 



The overflow logic is derived from the truth table using A4, B4, and S4. The truth table is seen in 

<img width="327" height="188" alt="image" src="https://github.com/user-attachments/assets/40e14db7-8e1d-4693-bf49-dcbbdfa5981e" />(Overflow Logic.png)

In 2's complement, whenver A4 and B4 both equal 0, and S4 equals 1, this means there is an overflow because 2 positive numbers can't ever 
add up to a negative number. The opposite is true as well, where if both A4 and B4 are equal to 1, and S4 is equal to 0, then there is 
an overflow. From this we are able to derive an equation of F = A'B'S + ABS' (A is A4, B is B4, and S is S4). Using this derivation, 
we can implement it into our circuit using a NOT, AND, and OR chips. This overflow logic of 2's complement works for both addition 
and subtraction because we are technically adding a negative number, not trully subtracting. As a result, it is still addition and
the 2's complement overflow logic works.

1000 - 1001 = 1111 (-8 - -7 = -1)
<img width="1440" height="1920" alt="image" src="https://github.com/user-attachments/assets/87f84d20-3df8-4551-9af2-f9839f42b759" />
<img width="1440" height="1920" alt="image" src="https://github.com/user-attachments/assets/1de56b0a-ef19-4575-af6a-2414b624b335" />
<img width="1440" height="1920" alt="image" src="https://github.com/user-attachments/assets/2f0e481d-3456-4ca2-95e1-98b69de34672" />

1001 + 1001 = Overflow (-7 + -7 //Outside the bounds of 4 bits)
<img width="1920" height="1440" alt="image" src="https://github.com/user-attachments/assets/f533b1bb-9bea-4c95-9d91-a6e9bd6c8698" />

0001 - 0001 = 0000 (1 - 1 = 0)
<img width="1920" height="1440" alt="image" src="https://github.com/user-attachments/assets/e9fd798a-4351-4326-b5c6-b6eba21832e3" />
