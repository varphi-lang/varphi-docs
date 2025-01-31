# The Unary Number System

## What are Number Systems?

From Wikipedia:

> A numeral system is a writing system for expressing numbers; that is, a [mathematical notation](https://en.wikipedia.org/wiki/Mathematical_notation) for representing numbers of a given set, using [digits](https://en.wikipedia.org/wiki/Numerical_digit) or other symbols in a consistent manner.

There are infinitely many number systems. The most commonly used of these is the _decimal_ (base 10) number system, which uses the symbols $$0, 1, ..., 9$$ to represent numbers. Our modern-day computers use the _binary_ (base 2) number system, which uses the symbols $$0$$ and $$1$$ to represent numbers. For example, the binary representation of the decimal number $$25$$ is $$11001$$.&#x20;

## The Unary Number System

By definition, the simplest number system is the one which uses the least number of symbols. This number system is called the _unary_ number system, and it uses _one_ symbol to represent numbers, which we call a tally.&#x20;

{% hint style="info" %}
We will often use the symbol $$1$$ to denote a tally in this text.
{% endhint %}

You use this number system more than you know! Imagine trying to represent the decimal number $$7$$ on your fingers. You would put up seven fingers (probably, unless your brain operates in binary), which is like writing seven tallies on a paper!

Although the unary number system is extremely simple, it is not any less (or more) powerful than any other number system.

## Representation Conventions

The example above about representing numbers on your fingers shows how to use the unary number system to represent _positive_ numbers. This does not mean that the unary number can only represent positive numbers, however.&#x20;

In the above example, the following _representation convention_ was used

> To represent a number $$n\in\mathbb{Z}^+$$, repeat the symbol $$1$$ $$n$$ times.

Suppose now that we wanted to represent the set of nonnegative integers (to be able to represent zero as well) using the unary number system. We could define the following _representation convention_:

> To represent a number $$n\in\mathbb{N}$$, repeat the symbol $$1$$ $$n + 1$$ times.

{% hint style="info" %}
Above, we used $$\mathbb{N}$$ to represent the set of nonnegative integers (i.e., $$\{x: x\in\mathbb{Z}\wedge x\geq 0\}$$.
{% endhint %}

Under this representation convention, we can represent the number decimal number $$0$$ with $$1$$, the decimal number $$1$$ with $$11$$, and so on...

You can theoretically come up with any convention you like to represent a set of numbers using unary. Here's a rather crazy one:

> To represent a number $$n\in\mathbb{Z}^+$$, repeat the symbol $$1$$ $$n^2 + 5$$ times.

Try to represent the decimal number $$3$$ in unary using this convention.&#x20;

The whole point of this is to show that providing a unary representation of a number to someone is not enough for them to know which number is being represented. You must also give them the convention you used to come up with that representation. The number that the unary representation $$111111$$ represents varies greatly between the three input conventions shown above (it represents six, five, and one respectively).
