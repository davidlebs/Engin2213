The circuit shown in this folder is a Finite State Machine (FSM) of the card game Craps / Shooting Dice. 
Without mentioning the betting aspect of this game, the game begins by rolling 2 dice in hops of getting
a 7 or 11. If a 7 or 11 are achieved then the roller wins. If a 2, 3, or 12 are achieved, the player loses.
If a 4, 5, 6, 8, 9, or 10 (any number than previously mentioned) are achieved, then that value is "stored".
The player keeps rolling until they either get one of those numbers (4, 5, ...) and wins, or gets a 7 and loses.
The game is then reset and the player starts again.

The dice are both represented through the use of a counter counting from 1 to 6. In reality, the counter actually
starts at 0, counts to 1 up to 6, and after 6 reverts back to 1. To adjust this, we use the preset pins
to preset the counters automatically to 1 whenever the dice are reset. The reset function is taken from the FSM.
Then, a Binary Coded Decimal (BCD) to 7 Segment Display Decoder is used to display the dice numbers on an LED Display.

<img width="383" height="668" alt="image" src="https://github.com/user-attachments/assets/24e00f2b-9e85-4cf9-9e8e-d7709b6b54fe" /> 
(Counter Logic.jpg)

These two numbers are then added together through the use of a Adder Chip and the value is decoded
(through the useof a 4 to 16 decoder) and sent to the FSM logic.

The sum of these numbers also has a connection to a point register (PIPO Register) and a comparator chip. 
Whenever the first roll isn't equal to 2, 3, 12, 7, or 11, a store signal is sent to the point register (connected
to the clock of the PIPO Register) and that value is then stored. On the next roll, if that number is equal to the 
number stored in the register, an equivelncy signal is sent and the player wins. If the number is equal to a 7, that player loses, and if that number is equal to anything else, the player keeps rerolling (as explained in the begining).

Onto the FSM logic, a flowchart was built to simplify the way the game is played. 

<img width="333" height="540" alt="image" src="https://github.com/user-attachments/assets/1030bfdc-8337-4b7b-aa0d-d8eff91f9afc" /> 
(Flowchart.jpg)

This image reiterates the way the game is played and goes more into depth of how the circuit checks each component.

This flowchart is then used to create the FSM Diagram which then can be used to design a FSM Table. 

<img width="855" height="853" alt="image" src="https://github.com/user-attachments/assets/5e4eabea-e398-4469-bb04-7fd45e4ab54e" /> 
(State Map.jpg)


<img width="1079" height="475" alt="image" src="https://github.com/user-attachments/assets/ab8b6f54-42a8-4e28-8666-fcf1580ea586" /> 
(Truth Table.png)

Our FSM consists of 9 inputs and 7 outputs. We then have to solve for A, B, C of the next state as well as the win, lose
roll, and store output. The subsequent simplifications are listed below. 

<img width="561" height="227" alt="image" src="https://github.com/user-attachments/assets/2677db59-77c2-4396-b57d-6a7ad60549d9" /> (Simplification.jpg)

Using these expressions, we are able to implement it into our circuit, finally completing it. Quickly reitering previously stated points, our 
reset not only resets the FSM but also our clocks, our store button clocks our register chip and stores our points, and our roll button enables 
our clocks so the dice can give a random output. 

<img width="2311" height="1007" alt="image" src="https://github.com/user-attachments/assets/20f87bee-ad6e-420a-840b-225295cda6cf" />
(CircuitVerse Screenshot.jpg)
Link: https://circuitverse.org/simulator/embed/craps

The simulation also includes multiple sub-circuits. One of those being an Adder / Subtractor who's derivation and explanation is in 
checkpoint 1 / circuit 1.
<img width="621" height="357" alt="image" src="https://github.com/user-attachments/assets/0a2d4c55-b850-4d21-8df2-0f39b387c132" />
(Adder Subtractor.jpg)

I also have a BCD to 7 Segment Display. This circuit is derived from looking at when each LED should be on. For example,
the top segment A, should turn on for 0, 2, 3, 5, 6, 7, 8, and 9. For these numbers, a 1 is sent to turn on the LED, and for the rest of the
numbers, a 0 is sent to keep the LED off. Doing this for each segment and each number, you can derive the expression. This topic is further 
discussed in checkpoint 3, circuit 8. 
<img width="663" height="1086" alt="image" src="https://github.com/user-attachments/assets/9911ff82-512e-45ea-bbac-5cdbf500d2b5" />
(BCD to 7SD.jpg)

We also have a 4 to 16 decoder which is built by taking each combination of the inputs and inputs inverted. As seen in the circuit,
we see this labelled on the outputs. Then whenever a signal is sent, only that output will be enabled because it matches that sequence of numbers.
<img width="1282" height="949" alt="image" src="https://github.com/user-attachments/assets/25dbeec9-a35a-486b-99d4-4c5a2c10b351" />
(Decoder.jpg)

A comparator chip was also built by comparing each bit to its respective counterpart. We compare the MSB first, and if A>B, we know that A is
greater than B and vice versa. This process is then continued for each bit all the way to the LSB. If each bit is equal to one another, then 
we know A=B. 
<img width="966" height="810" alt="image" src="https://github.com/user-attachments/assets/7c096729-3256-4539-9297-fc726340eee2" />
(Comparator.jpg)

A 4 to 1 mux was bulit from having 2 enable bits and their inverse. Like the decoder, we then make each combination using 3 input and gates, 
where only one gate is activated at a time, and the third input is for the signal which is going to be sent through, a 0 or a 1. 
<img width="552" height="501" alt="image" src="https://github.com/user-attachments/assets/1828a645-8063-4b33-b973-200269d0ea05" />
(MUX.jpg)

Lastly, a universal shift register was built by using D flip-flops and 4 to 1 muxs. We have 2 enable bits to selct the mode, either 
hold (00), shift right (01), shift left (10), or load data (11). The mux then sends the proper signal through depending on which
enable bits are selected, and using the D flip-flops, we can store the data and then either hold, shift, or load data in. A clear button
is connected to the D flip-flops premade clear pin, as well as a clock button to clock the D flip-flops.
<img width="1090" height="1094" alt="image" src="https://github.com/user-attachments/assets/8ef424f0-c4e9-4174-96c8-64eb5b48f8ce" /> 
(Universale Shift Register.jpg)
