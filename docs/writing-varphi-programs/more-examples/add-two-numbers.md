# Add Two Numbers

Below is a Varphi program that adds (i.e., "merges") two contiguous blocks of tallies (containing at least one tally each) separated by a blank tape cell into one contiguous block of tallies.&#x20;

```
q0 1 q1 0 R // Remove first tally of left number
q1 1 q1 1 R // Skip remaining tallies of left number
q1 0 q2 1 R // Make middle blank be a tally
```

