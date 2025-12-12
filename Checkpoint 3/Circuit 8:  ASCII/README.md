This circuit demonstrates a Binary Coded Decimal (BCD) to ASCII using a 16 segment display. Using the same technique we used to derive a 7 segment display,
we can apply it to a 16 segment display and find out when each segment should be lit up. First, we have to find out what the binary code for "A" is
and write it down (01000001). Following this, we have to figure out which segment is supposed to light up. To figure out this, I connected an input
to the 16 segment display and set the bitwidth at 16 (for 16 segments). For example, the lsb turns on the bottom left diagnal, the 2nd to last lsb turns on the bottom vertical bar, and so on. Then I wrote down which binary bit corresponds to which segment of the display using the annotation
"a", "b", "c", and so on to represent each semgment. 

<img width="518" height="280" alt="image" src="https://github.com/user-attachments/assets/108c0e82-519a-40ad-b027-e71b4818a77f" />

(16SD 16 Bitwidth.jpg)

Now we can derive the expression for each capital letter and input our binary into a calculator (LogicAid in my situation) to get the expression
for each segment. 

*If you would like to look at the data or recreate this project head over to Checkpoint 3 / Circuit 8 / Derivation.csv* 

<img width="1342" height="484" alt="image" src="https://github.com/user-attachments/assets/05e32e2f-9013-404c-8384-262066250e86" />

(Derivation.jpg)

<img width="442" height="328" alt="image" src="https://github.com/user-attachments/assets/55d00c8e-783d-4b4d-a7ed-ed18b0192323" />

(Variable Names.jpg)

<img width="277" height="352" alt="image" src="https://github.com/user-attachments/assets/c8eaaf63-43b2-4f37-81b7-e7c8556cabad" />

(Variable Settings.jpg)

Now that we have each segment's expression, we can start implementing this on CircuitVerse.

<img width="2224" height="1018" alt="image" src="https://github.com/user-attachments/assets/05b31eb7-de4f-4faa-a855-5c9aec5dfcde" />

(BCD to 16SD PT.1.jpg)

<img width="2336" height="966" alt="image" src="https://github.com/user-attachments/assets/466a12e2-fdf9-4d49-a2a1-df9fed90ad4b" />

(BCD to 16SD PT.2.jpg)
Link: https://circuitverse.org/simulator/embed/hex-to-ascii

Now that we have our BCD to 16SD built, we can start messing around with it and start making designs. One idea I had was to use a 32 to 5 priority 
encoder to select each letter. Since the ASCII code is a byte long, this wouldn't be possible, but because the first 3 msb are constant (always 010) 
we are only change the last 5, and since we got 26 letters this fits perfectly in our situation. The unused inputs are then grounded so 
they don't interfere with our seleciton. 

<img width="1094" height="815" alt="image" src="https://github.com/user-attachments/assets/263524f3-253a-4444-ac8f-9c300da2e45a" />

(Priority Encoder.jpg)

We now have a circuit where you can select a letter, with Z being msb and having priority, which outputs the binary value, the hex value, and the 
ASCII character. 

Messing around with the circuit, I also wanted to see if you could type the letters and get an output on the 16SD. Knowing that CircuitVerse has
a keyboard, I started messing around with that to see how it funcitons. I connected an output box to the ASCII Output pin and got an error
requiring a bitwidth of 7. Applying the changes, I tried again with capital A and got "1000001". I did this with a few more letters and 
realized that the output was just the ASCII binary code which I used to built my previous components. I then connected up the keyboard to the 
circuit and was able to type letters into the keyboard and get an output on the display.

<img width="619" height="759" alt="image" src="https://github.com/user-attachments/assets/dfc19254-cfab-42ea-a1d6-9b6cbf642d7b" />

(Keyboard.jpg)

I had one other subcircuit in this project which will now be discussed. A BCD to 7SD w/ Hex was used to show the hex value of the ASCII character
on top of the already shown binary output. This circuit was derived the same way as the 16SD was. I first wrote out each input in 4 bits, where
0000 was 0 and 1111 was F. I then wrote down which segment should light up for each binary input. 

<img width="676" height="676" alt="image" src="https://github.com/user-attachments/assets/651fe9bf-a7f4-4c05-86b5-e97b9ada1870" />

(BCD to 7SD.jpg)
