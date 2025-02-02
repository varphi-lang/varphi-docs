# Nondeterministic Turing Machines

## Nondeterminism

The Turing machines discussed in this section so far, such as the one that adds two tallies to any number, are called _deterministic_ machines, since their outputs are guaranteed to be the same every time if the input tape is the same between runs.

Turing machines can also be _nondeterministic_, meaning their outputs can vary between runs with the same input tape.&#x20;

## Example

For example, consider the following transition function (written as a Turing program, or Varphi program):

```
qStart 1 qHalt 1 R
qStart 1 qHalt 0 R
```

Notice that we have defined two different rules for when the Turing machine is on state `qStart` and encounters a tally. The first rule instructs the Turing machine to leave the tally untouched and halt, while the other rule instructs it to make the tape cell blank and halt.&#x20;

Which path will the Turing machine take on an input tape with one tally? There is no way to tell. The machine actually has a 50% chance of using the first rule over the second, and vice versa. So, for one run of the machine, the output tape may have one tally, and for another run, it will have no tallies.&#x20;
