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


Code for 27C64:
PRIME	A(msb)	B	C	D	E	F	G(lsb)	HEX
0	0	0	0	0	0	0	0	00
0	0	0	0	0	0	0	1	01
1	0	0	0	0	0	1	0	82
1	0	0	0	0	0	1	1	83
0	0	0	0	0	1	0	0	04
1	0	0	0	0	1	0	1	85
0	0	0	0	0	1	1	0	06
1	0	0	0	0	1	1	1	87
0	0	0	0	1	0	0	0	08
0	0	0	0	1	0	0	1	09
0	0	0	0	1	0	1	0	0A
1	0	0	0	1	0	1	1	8B
0	0	0	0	1	1	0	0	0C
1	0	0	0	1	1	0	1	8D
0	0	0	0	1	1	1	0	0E
0	0	0	0	1	1	1	1	0F
0	0	0	1	0	0	0	0	10
1	0	0	1	0	0	0	1	91
0	0	0	1	0	0	1	0	12
1	0	0	1	0	0	1	1	93
0	0	0	1	0	1	0	0	14
0	0	0	1	0	1	0	1	15
0	0	0	1	0	1	1	0	16
1	0	0	1	0	1	1	1	97
0	0	0	1	1	0	0	0	18
0	0	0	1	1	0	0	1	19
0	0	0	1	1	0	1	0	1A
0	0	0	1	1	0	1	1	1B
0	0	0	1	1	1	0	0	1C
1	0	0	1	1	1	0	1	9D
0	0	0	1	1	1	1	0	1E
1	0	0	1	1	1	1	1	9F
0	0	1	0	0	0	0	0	20
0	0	1	0	0	0	0	1	21
0	0	1	0	0	0	1	0	22
0	0	1	0	0	0	1	1	23
0	0	1	0	0	1	0	0	24
1	0	1	0	0	1	0	1	A5
0	0	1	0	0	1	1	0	26
0	0	1	0	0	1	1	1	27
0	0	1	0	1	0	0	0	28
1	0	1	0	1	0	0	1	A9
0	0	1	0	1	0	1	0	2A
1	0	1	0	1	0	1	1	AB
0	0	1	0	1	1	0	0	2C
0	0	1	0	1	1	0	1	2D
0	0	1	0	1	1	1	0	2E
1	0	1	0	1	1	1	1	AF
0	0	1	1	0	0	0	0	30
0	0	1	1	0	0	0	1	31
0	0	1	1	0	0	1	0	32
0	0	1	1	0	0	1	1	33
0	0	1	1	0	1	0	0	34
1	0	1	1	0	1	0	1	B5
0	0	1	1	0	1	1	0	36
0	0	1	1	0	1	1	1	37
0	0	1	1	1	0	0	0	38
0	0	1	1	1	0	0	1	39
0	0	1	1	1	0	1	0	3A
1	0	1	1	1	0	1	1	BB
0	0	1	1	1	1	0	0	3C
1	0	1	1	1	1	0	1	BD
0	0	1	1	1	1	1	0	3E
0	0	1	1	1	1	1	1	3F
0	1	0	0	0	0	0	0	40
0	1	0	0	0	0	0	1	41
0	1	0	0	0	0	1	0	42
1	1	0	0	0	0	1	1	C3
0	1	0	0	0	1	0	0	44
0	1	0	0	0	1	0	1	45
0	1	0	0	0	1	1	0	46
1	1	0	0	0	1	1	1	C7
0	1	0	0	1	0	0	0	48
1	1	0	0	1	0	0	1	C9
0	1	0	0	1	0	1	0	4A
0	1	0	0	1	0	1	1	4B
0	1	0	0	1	1	0	0	4C
0	1	0	0	1	1	0	1	4D
0	1	0	0	1	1	1	0	4E
1	1	0	0	1	1	1	1	CF
0	1	0	1	0	0	0	0	50
0	1	0	1	0	0	0	1	51
0	1	0	1	0	0	1	0	52
1	1	0	1	0	0	1	1	D3
0	1	0	1	0	1	0	0	54
0	1	0	1	0	1	0	1	55
0	1	0	1	0	1	1	0	56
0	1	0	1	0	1	1	1	57
0	1	0	1	1	0	0	0	58
1	1	0	1	1	0	0	1	D9
0	1	0	1	1	0	1	0	5A
0	1	0	1	1	0	1	1	5B
0	1	0	1	1	1	0	0	5C
0	1	0	1	1	1	0	1	5D
0	1	0	1	1	1	1	0	5E
0	1	0	1	1	1	1	1	5F
0	1	1	0	0	0	0	0	60
1	1	1	0	0	0	0	1	E1
0	1	1	0	0	0	1	0	62
0	1	1	0	0	0	1	1	63
0	1	1	0	0	1	0	0	64

Code for 27C1024:
UNUSED	UNUSED	UNUSED	Prime	MSB(100)			LSB(100)	MSB(10)			LSB(10)	MSB(1)			LSB(1)	DECIMAL	HEX
1	1	1	0	0	0	0	0	0	0	0	0	0	0	0	0	0	E000
1	1	1	0	0	0	0	0	0	0	0	0	0	0	0	1	1	E001
1	1	1	1	0	0	0	0	0	0	0	0	0	0	1	0	2	F002
1	1	1	1	0	0	0	0	0	0	0	0	0	0	1	1	3	F003
1	1	1	0	0	0	0	0	0	0	0	0	0	1	0	0	4	E004
1	1	1	1	0	0	0	0	0	0	0	0	0	1	0	1	5	F005
1	1	1	0	0	0	0	0	0	0	0	0	0	1	1	0	6	E006
1	1	1	1	0	0	0	0	0	0	0	0	0	1	1	1	7	F007
1	1	1	0	0	0	0	0	0	0	0	0	1	0	0	0	8	E008
1	1	1	0	0	0	0	0	0	0	0	0	1	0	0	1	9	E009
1	1	1	0	0	0	0	0	0	0	0	1	0	0	0	0	10	E010
1	1	1	1	0	0	0	0	0	0	0	1	0	0	0	1	11	F011
1	1	1	0	0	0	0	0	0	0	0	1	0	0	1	0	12	E012
1	1	1	1	0	0	0	0	0	0	0	1	0	0	1	1	13	F013
1	1	1	0	0	0	0	0	0	0	0	1	0	1	0	0	14	E014
1	1	1	0	0	0	0	0	0	0	0	1	0	1	0	1	15	E015
1	1	1	0	0	0	0	0	0	0	0	1	0	1	1	0	16	E016
1	1	1	1	0	0	0	0	0	0	0	1	0	1	1	1	17	F017
1	1	1	0	0	0	0	0	0	0	0	1	1	0	0	0	18	E018
1	1	1	1	0	0	0	0	0	0	0	1	1	0	0	1	19	F019
1	1	1	0	0	0	0	0	0	0	1	0	0	0	0	0	20	E020
1	1	1	0	0	0	0	0	0	0	1	0	0	0	0	1	21	E021
1	1	1	0	0	0	0	0	0	0	1	0	0	0	1	0	22	E022
1	1	1	1	0	0	0	0	0	0	1	0	0	0	1	1	23	F023
1	1	1	0	0	0	0	0	0	0	1	0	0	1	0	0	24	E024
1	1	1	0	0	0	0	0	0	0	1	0	0	1	0	1	25	E025
1	1	1	0	0	0	0	0	0	0	1	0	0	1	1	0	26	E026
1	1	1	0	0	0	0	0	0	0	1	0	0	1	1	1	27	E027
1	1	1	0	0	0	0	0	0	0	1	0	1	0	0	0	28	E028
1	1	1	1	0	0	0	0	0	0	1	0	1	0	0	1	29	F029
1	1	1	0	0	0	0	0	0	0	1	1	0	0	0	0	30	E030
1	1	1	1	0	0	0	0	0	0	1	1	0	0	0	1	31	F031
1	1	1	0	0	0	0	0	0	0	1	1	0	0	1	0	32	E032
1	1	1	0	0	0	0	0	0	0	1	1	0	0	1	1	33	E033
1	1	1	0	0	0	0	0	0	0	1	1	0	1	0	0	34	E034
1	1	1	0	0	0	0	0	0	0	1	1	0	1	0	1	35	E035
1	1	1	0	0	0	0	0	0	0	1	1	0	1	1	0	36	E036
1	1	1	1	0	0	0	0	0	0	1	1	0	1	1	1	37	F037
1	1	1	0	0	0	0	0	0	0	1	1	1	0	0	0	38	E038
1	1	1	0	0	0	0	0	0	0	1	1	1	0	0	1	39	E039
1	1	1	0	0	0	0	0	0	1	0	0	0	0	0	0	40	E040
1	1	1	1	0	0	0	0	0	1	0	0	0	0	0	1	41	F041
1	1	1	0	0	0	0	0	0	1	0	0	0	0	1	0	42	E042
1	1	1	1	0	0	0	0	0	1	0	0	0	0	1	1	43	F043
1	1	1	0	0	0	0	0	0	1	0	0	0	1	0	0	44	E044
1	1	1	0	0	0	0	0	0	1	0	0	0	1	0	1	45	E045
1	1	1	0	0	0	0	0	0	1	0	0	0	1	1	0	46	E046
1	1	1	1	0	0	0	0	0	1	0	0	0	1	1	1	47	F047
1	1	1	0	0	0	0	0	0	1	0	0	1	0	0	0	48	E048
1	1	1	0	0	0	0	0	0	1	0	0	1	0	0	1	49	E049
1	1	1	0	0	0	0	0	0	1	0	1	0	0	0	0	50	E050
1	1	1	0	0	0	0	0	0	1	0	1	0	0	0	1	51	E051
1	1	1	0	0	0	0	0	0	1	0	1	0	0	1	0	52	E052
1	1	1	1	0	0	0	0	0	1	0	1	0	0	1	1	53	F053
1	1	1	0	0	0	0	0	0	1	0	1	0	1	0	0	54	E054
1	1	1	0	0	0	0	0	0	1	0	1	0	1	0	1	55	E055
1	1	1	0	0	0	0	0	0	1	0	1	0	1	1	0	56	E056
1	1	1	0	0	0	0	0	0	1	0	1	0	1	1	1	57	E057
1	1	1	0	0	0	0	0	0	1	0	1	1	0	0	0	58	E058
1	1	1	1	0	0	0	0	0	1	0	1	1	0	0	1	59	F059
1	1	1	0	0	0	0	0	0	1	1	0	0	0	0	0	60	E060
1	1	1	1	0	0	0	0	0	1	1	0	0	0	0	1	61	F061
1	1	1	0	0	0	0	0	0	1	1	0	0	0	1	0	62	E062
1	1	1	0	0	0	0	0	0	1	1	0	0	0	1	1	63	E063
1	1	1	0	0	0	0	0	0	1	1	0	0	1	0	0	64	E064
1	1	1	0	0	0	0	0	0	1	1	0	0	1	0	1	65	E065
1	1	1	0	0	0	0	0	0	1	1	0	0	1	1	0	66	E066
1	1	1	1	0	0	0	0	0	1	1	0	0	1	1	1	67	F067
1	1	1	0	0	0	0	0	0	1	1	0	1	0	0	0	68	E068
1	1	1	0	0	0	0	0	0	1	1	0	1	0	0	1	69	E069
1	1	1	0	0	0	0	0	0	1	1	1	0	0	0	0	70	E070
1	1	1	1	0	0	0	0	0	1	1	1	0	0	0	1	71	F071
1	1	1	0	0	0	0	0	0	1	1	1	0	0	1	0	72	E072
1	1	1	1	0	0	0	0	0	1	1	1	0	0	1	1	73	F073
1	1	1	0	0	0	0	0	0	1	1	1	0	1	0	0	74	E074
1	1	1	0	0	0	0	0	0	1	1	1	0	1	0	1	75	E075
1	1	1	0	0	0	0	0	0	1	1	1	0	1	1	0	76	E076
1	1	1	0	0	0	0	0	0	1	1	1	0	1	1	1	77	E077
1	1	1	0	0	0	0	0	0	1	1	1	1	0	0	0	78	E078
1	1	1	1	0	0	0	0	0	1	1	1	1	0	0	1	79	F079
1	1	1	0	0	0	0	0	1	0	0	0	0	0	0	0	80	E080
1	1	1	0	0	0	0	0	1	0	0	0	0	0	0	1	81	E081
1	1	1	0	0	0	0	0	1	0	0	0	0	0	1	0	82	E082
1	1	1	1	0	0	0	0	1	0	0	0	0	0	1	1	83	F083
1	1	1	0	0	0	0	0	1	0	0	0	0	1	0	0	84	E084
1	1	1	0	0	0	0	0	1	0	0	0	0	1	0	1	85	E085
1	1	1	0	0	0	0	0	1	0	0	0	0	1	1	0	86	E086
1	1	1	0	0	0	0	0	1	0	0	0	0	1	1	1	87	E087
1	1	1	0	0	0	0	0	1	0	0	0	1	0	0	0	88	E088
1	1	1	1	0	0	0	0	1	0	0	0	1	0	0	1	89	F089
1	1	1	0	0	0	0	0	1	0	0	1	0	0	0	0	90	E090
1	1	1	0	0	0	0	0	1	0	0	1	0	0	0	1	91	E091
1	1	1	0	0	0	0	0	1	0	0	1	0	0	1	0	92	E092
1	1	1	0	0	0	0	0	1	0	0	1	0	0	1	1	93	E093
1	1	1	0	0	0	0	0	1	0	0	1	0	1	0	0	94	E094
1	1	1	0	0	0	0	0	1	0	0	1	0	1	0	1	95	E095
1	1	1	0	0	0	0	0	1	0	0	1	0	1	1	0	96	E096
1	1	1	1	0	0	0	0	1	0	0	1	0	1	1	1	97	F097
1	1	1	0	0	0	0	0	1	0	0	1	1	0	0	0	98	E098
1	1	1	0	0	0	0	0	1	0	0	1	1	0	0	1	99	E099
1	1	1	0	0	0	0	1	0	0	0	0	0	0	0	0	100	E100
