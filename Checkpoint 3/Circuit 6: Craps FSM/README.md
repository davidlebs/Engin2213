The circuit shown in this folder is a Finite State Machine (FSM) of the card game Craps / Shooting Dice. 
Without mentioning the betting aspect of this game, the game begins by rolling 2 dice in hops of getting
a 7 or 11. If a 7 or 11 are achieved then the roller wins. If a 2, 3, or 12 are achieved, the player loses.
If a 4, 5, 6, 8, 9, or 10 (any number than previously mentioned) are achieved, then that value is "stored".
The player keeps rolling until they either get one of those numbers (4, 5, ...) and wins, or gets a 7 and loses.
The game is then reset and the player starts again.

The dice are both represented through the use of a counter counting from 1 to 6. In reality, the counter actually
starts at 0, counts to 1 up to 6, and after 6 reverts back to 1. To adjust this, we use the preset pins
to preset the counters automatically to 1 whenever the dice are reset. The reset function is taken from the FSM.

<img width="383" height="668" alt="image" src="https://github.com/user-attachments/assets/24e00f2b-9e85-4cf9-9e8e-d7709b6b54fe" /> (Counter Logic.jpg)
