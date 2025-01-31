# Addressing Ambiguities

## The "Top-Left" Rule

Arguably the only ambiguity in a Varphi program is the starting state. How is the state which the Turing machine starts with determined?

The "Top-Left" Rule is a rule that can be applied to determine the starting state of any Varphi program. Simply select the state located at the top-left corner of the program. For example, suppose your program looks like this:

```
q0 1 q0 1 R
q0 0 q1 1 R
q1 0 q2 1 R
```

Then, the starting state is `q0`.

## The "At Least One Tally" Rule

Input tapes must include at least one tape cell with a tally. If not, a runtime error will be thrown.&#x20;

## The "Leftmost Tally" Rule

A standard that is followed by Turing machine developers is to make the initial position of the head be the leftmost tally on the tape. This convention is adopted by Varphi. The leftmost tally is guaranteed to exist by the ["At Least One Tally" Rule](addressing-ambiguities.md#the-at-least-one-tally-rule).&#x20;
