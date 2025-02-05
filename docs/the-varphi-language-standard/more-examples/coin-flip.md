# Coin Flip

Below is an example of a [nondeterministic](../../turing-machine-theory/nondeterministic-turing-machines.md) Varphi program that, when given an input tape containing exactly one tally, returns an output tape containing one or two tallies.&#x20;

```
qStart 1 qHeads 0 R
qStart 1 qTails 0 R

qHeads 0 qWrite1 0 R
qTails 0 qWrite2 0 R

qWrite1 0 qHalt 1 R
qWrite2 0 qWrite1 1 R
```

