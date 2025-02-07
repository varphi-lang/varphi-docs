# Add Two Numbers

Below is a Varphi program that adds (i.e., "merges") two contiguous blocks of tallies (containing at least one tally each) separated by a blank tape cell into one contiguous block of tallies.&#x20;

```
q0 1 q0 1 R // Skip left number's tallies
q0 0 q1 1 R // Found middle blank, make it contain a tally
q1 1 q1 1 R // Skip right number's tallies
q1 0 q2 0 L // Reached end of right number, go back to remove last tally
q2 1 qh 0 R // Remove final tally of right number
```

