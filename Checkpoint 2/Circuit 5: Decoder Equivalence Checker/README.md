This circuit uses a decoder as a comparator of some sorts. It is only able to detect if the values are of the same magnitude.
This is another possible implimentation into our design project (cops and robbers), depending on how we would like to build it. 
Considering we will have obstacles, if the values are the same, then the player wouldn't be able to move into that spot.

This circuit mainly relies on a 3 to 8 decoder to send 1 signal at a time to an AND gate which checks if the values are the same.
If they are, it sends another signal through to an OR gate which then splits the values into either being the same or different.
Using this idea, we can implement it into our design project where each X coordinate has a different input, and using some 
ROM we can check if the values overlap or if that spot is free.
