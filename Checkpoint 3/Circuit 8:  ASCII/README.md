This circuit demonstrates a Binary Coded Decimal (BCD) to ASCII using a 16 segment display. Using the same technique we used to derive a 7 segment display,
we can apply it to a 16 segment display and find out when each segment should be lit up. First, we have to find out what the binary code for "A" is
and write it down (01000001). Following this, we have to figure out which segment is supposed to light up. To figure out this, I connected an input
to the 16 segment display and set the bitwidth at 16 (for 16 segments). Then I wrote down which binary bit corresponds to which segment of the display.
