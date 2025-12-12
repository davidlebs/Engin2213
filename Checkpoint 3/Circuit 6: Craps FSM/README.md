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

<img width="383" height="668" alt="image" src="https://github.com/user-attachments/assets/24e00f2b-9e85-4cf9-9e8e-d7709b6b54fe" /> (Counter Logic.jpg)

These two numbers are then added together through the use of a Adder Chip and the value is decoded
(through the useof a 4 to 16 decoder) and sent to the FSM logic.

The sum of these numbers also has a connection to a point register (PIPO Register) and a comparator chip. 
Whenever the first roll isn't equal to 2, 3, 12, 7, or 11, a store signal is sent to the point register (connected
to the clock of the PIPO Register) and that value is then stored. On the next roll, if that number is equal to the 
number stored in the register, an equivelncy signal is sent and the player wins. If the number is equal to a 7, that player loses, and if that number is equal to anything else, the player keeps rerolling (as explained in the begining).

Onto the FSM logic, a flowchart was built to simplify the way the game is played. 

<img width="333" height="540" alt="image" src="https://github.com/user-attachments/assets/1030bfdc-8337-4b7b-aa0d-d8eff91f9afc" /> (Flowchart.jpg)

This image reiterates the way the game is played and goes more into depth of how the circuit checks each component.

This flowchart is then used to create the FSM Diagram which then can be used to design a FSM Table. 

<img width="855" height="853" alt="image" src="https://github.com/user-attachments/assets/5e4eabea-e398-4469-bb04-7fd45e4ab54e" /> (State Map.jpg)


<img width="1079" height="475" alt="image" src="https://github.com/user-attachments/assets/ab8b6f54-42a8-4e28-8666-fcf1580ea586" /> (Truth Table.png)

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
checkpoint 1, 
