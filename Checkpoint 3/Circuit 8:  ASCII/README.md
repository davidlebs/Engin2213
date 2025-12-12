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
