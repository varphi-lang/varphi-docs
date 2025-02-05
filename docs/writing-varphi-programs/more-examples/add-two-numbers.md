# Add Two Numbers

Below is a Varphi program that adds (i.e., "merges") two contiguous blocks of tallies (containing at least one tally each) separated by a blank tape cell into one contiguous block of tallies.&#x20;

```
q0 0 qh 0 R // Nothing from first number remaining; halt
q0 1 q1 0 R // Change first tally (to the left) of the first number to a 0 (we'll "move" this to the end of the second number)
q1 1 q1 1 R // Skip the rest of the tallies of the first number
q1 0 q2 0 R // Found middle blank
q2 1 q2 1 R // Skip through the tallies of the second number
q2 0 q3 1 L // Found end of second number; add a tally here
q3 1 q3 1 L // Skip through tallies of second number (moving left)
q3 0 q4 0 L // Found middle blank
q4 1 q4 1 L // Skip through tallies of first number
q4 0 q0 0 R // Found end of first number (it will be 1 less than before now), switch to q0 and repeat the process
```

