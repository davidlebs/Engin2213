In this circuit, I used 2 eprom chips decode numbers 0 to 100 and show which number is prime. Using the 27C64, I derived the chips hex characters
by writting out each number in binary and setting the MSB as A and LSB as G. A is Q6 (pin Q6 of eprom) and G is Q0 (pin Q0 of eprom). Then Q7 was used
to show which numbers are prime and which ones aren't. For example, 0 and 1 had the prime light not turn on, but 2, 3, and 5 did. Using these binary 
numbers, I then decoded the HEX value for each and coded the eprom using the software XGPRO. These outputs were then each sent to an LED to show what 
number is selected and if its prime or not.

<img width="231" height="827" alt="image" src="https://github.com/user-attachments/assets/d07601b5-1b80-4339-a918-34cb8fa29f66" />

(27C64.png)

For the 27C1024, I was using that chip to send a signal to a BCD to 7SD so I could use a 7SD to show what number is selected. Q3 to Q0 was the 
MSB to LSB respectively for the 1's place, Q7 to Q4 the MSB to LSB respectivelly for the 10's place, and Q11 to Q8 was the MSB to LSB respectively 
for the hundreds place. When building the circuit, instead of using 3 decoders and 3 7SD, I decided to just use 2 for each instead, only showing
the 1's and 10's place. For the hundred's place, I used a LED instead and this was possible due to the fact that the binary was the same for both
a 7SD and LED. Q12 was then used for my primes, and since Q15 to Q13 weren't used, we don't care about their value. I then converted the 4 nibbles 
to 4 HEX characters and coded the eprom.  


<img width="466" height="827" alt="image" src="https://github.com/user-attachments/assets/4d6fff66-142c-4be6-b821-65e3e7780383" />

(27C1024.png)

<img width="1628" height="1121" alt="image" src="https://github.com/user-attachments/assets/de997f01-5837-4641-ac40-17189694bed3" />

(KiCAD Screenshot.jpg)

*If you would like a closer look at the data, head over to Eprom Data.csv in checkpoint 3 / circuit 7*

![IMG_7776](https://github.com/user-attachments/assets/28e153f5-41e4-4282-8209-12204d858099)
![IMG_7777](https://github.com/user-attachments/assets/e82039a2-283c-4d90-b47d-f8bd40b2b74c)
![IMG_7778](https://github.com/user-attachments/assets/3daebc16-0e51-49fa-842d-b2fcaecddd57)
![IMG_7779](https://github.com/user-attachments/assets/7d99d9f3-90a4-4884-9a0b-82d23b8152f7)

(IMG_7776.jpg to IMG_7779.jpg respectively)
