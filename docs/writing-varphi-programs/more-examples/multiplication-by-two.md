# Multiplication By Two

Below is a program accepting a single contiguous block of tallies (containing at least one tally) and duplicates it. The output tape will be a contiguous block of tallies containing double the tallies in the original contiguous block of tallies on the input tape.

```
q0 1 q1 0 R // "Mark" the current tally from the first number by changing it to 0
q0 0 qmerge 0 R // No more tallies from the first number, "merge" the two halves of the doubled number
q1 1 q1 1 R // Skip over the rest of the tallies from the first number
q1 0 q2 0 R // We've reached the middle blank
q2 1 q2 1 R // Skip over the tallies from the second number
q2 0 q3 1 L // We've reached the end of the first number, place a tally here
q3 1 q3 1 L // Skip over the tallies from the second number (moving left now)
q3 0 q4 0 L // We've reached the middle blank
q4 1 q4 1 L // Skip over the tallies from the first number (moving left now)
q4 0 q0 1 R // We've reached the beginning of the first number. Return the tally that we replaced with a blank, and point the head to the next tally of the first number and restart

qmerge 1 qmerge1 1 L // When we hit qmerge, the head will be pointed at the first tally from the second half. Shift to the left to go to the middle blank
qmerge1 0 qmerge2 1 R // Change the middle blank to a tally
qmerge2 1 qmerge2 1 R // Skip over the tallies of the second half
qmerge2 0 qmerge3 0 L // We've reached the end of the second half, but there's one more tally at the far right of the second half. Remove it
qmerge3 1 qh 0 R // Replace the last tally of the second half with a blank
```

