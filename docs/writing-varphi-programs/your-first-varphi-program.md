---
description: Let's get started with Varphi and write a program from scratch.
---

# Your First Varphi Program

The objective of this tutorial is to show how to write a simple program with Varphi. We will show how to go about thinking about the algorithm, and then how to translate that algorithm into Varphi.

## Objective of the Turing Machine

The Turing machine we will design for this guide performs binary addition (that is, addition of two numbers), specifically on numbers from the set of positive integers, $$\mathbb{Z}^+$$ in a more unique way (a very efficient way is given [here](more-examples/add-two-numbers.md)).

## Input and Output Representation Conventions

The input tape's representation convention will be as follows:

> To represent two positive integers $$x$$ and $$y$$, repeat $$x$$ tallies, followed by a blank, followed by $$y$$ tallies. Leave the rest of the tape blank.&#x20;

The output tape's representation convention will be as follows:

> There shall only be one contiguous block of tallies, which will represent the output of the Turing machine. If there are $$n$$ tallies in the contiguous block, then the number being represented by the tape is $$n$$.

## Thinking About the Algorithm

When thinking about how to design Turing machine algorithms, it often helps to think about an example. Suppose we would like to add the positive integers $$3$$ and $$2$$. Under the input representation convention, the input tape to the machine will look like the following:

<figure><img src="../.gitbook/assets/TwoAndThreeOnTape.drawio (1) (1).png" alt=""><figcaption></figcaption></figure>

We would like to "merge" these two numbers to form a contiguous block with five tallies on it. One may think about this as perhaps shifting all the tallies of the left (or right) number to the right (or left) by one tape cell. The way we will implement it is by "teleporting" the left (or right) number to appear immediately to the right (or left) of the right (or left) number. This is depicted below. Again, this is by no means the most efficient way to do this, but we implement it in this way for demonstration purposes.

<figure><img src="../.gitbook/assets/TwoAndThreeOnTape.drawio (1) (3).png" alt=""><figcaption></figcaption></figure>

A way to perform such an algorithm is to transfer each individual tally to the left of the right number, one-by-one. That is, for every tally in the left number, delete it, then go to the rightmost tally of the right number and replace the blank cell to the right of it with a tally.&#x20;

Let's phrase this in a more "Turing-machine-like" way. For the purposes of this algorithm, let's call the blank tape cell separating the two numbers on the input tape the _middle blank_. Now recall that the Turing machine's head always starts off at the leftmost tally. So, what we'll do is replace that tally with a blank, then pass all of the remaining tallies of the left number (moving the head to the right) until we hit the middle blank. Once we hit this middle blank, we'll skip it, then skip all of the tallies of the right number (again, still moving the head to the right) until we hit the first blank to the right of the right number. Then, write a tally to this blank tape cell. Now we have successfully transferred the first tally of the left number to the right place. To start working on the rest of the tallies of the left number, skip through the tallies of the right number (moving the head left this time) until we hit the middle blank. Once we hit the middle blank, we'll skip it, then skip all of the tallies of the left number (again, still moving the head to the left) until we hit the first blank to the left of the left number. Then, move the head one position to the right. If the tape cell at this tape cell is blank, then we've successfully moved all the tallies of the left number to the right of the right number. Otherwise, we still have tallies to move, and we can restart the same process we took with the initial tally we moved.

Hopefully this algorithm makes intuitive sense. However, notice how much it took us to describe it in English. Below, you'll see the equivalent Varphi algorithm, and you can judge for yourself if it makes writing such algorithms easier!

## Writing the Varphi Program

Now that we have an algorithm, we can start to write it in Varphi. You may be able to see from the algorithm's description that we need six states:

1. A state for replacing the leftmost tally of the left number with a blank
2. A state for skipping the tallies of the left number, moving towards the right
3. A state for skipping the tallies of the right number, moving towards the right
4. A state for skipping the tallies of the right number, moving towards the left
5. A state for skipping the tallies of the left number, moving towards the left
6. A halting state

Instead of describing in English the function of each state and how it connects with other states, we've decided that a Varphi program may actually be the clearest way to do this. Here's the Varphi program describing this Turing machine:

{% code lineNumbers="true" fullWidth="false" %}
```clike
/*
qDeleteFirstTallyOrHalt
Replace the leftmost tally of the left number with a blank.
If there are no tallies left in the number, halt.
This state assumes the head is pointed towards the first tally of the left number,
if any tallies remain.
After erasing the first tally, transition to qSkipLeftNumberTallies.
*/
qDeleteFirstTallyOrHalt 1 qSkipLeftNumberTallies1 0 R
qDeleteFirstTallyOrHalt 0 qHalt 0 R

/*
qSkipLeftNumberTallies
Traverse the tallies of the left number (moving right) without modifying them, then
transition to qSkipRightNumberTalliesAndWriteTallyAtEnd.
*/
qSkipLeftNumberTallies1 1 qSkipLeftNumberTallies1 1 R
qSkipLeftNumberTallies1 0 qSkipRightNumberTalliesAndWriteTallyAtEnd 0 R

/*
qSkipRightNumberTalliesAndWriteTallyAtEnd
Traverse the tallies of the right number (moving right) without modifying them.
After reaching the end of the right number, insert a tally at the tape cell
immediately to the right.
*/
qSkipRightNumberTalliesAndWriteTallyAtEnd 1 qSkipRightNumberTalliesAndWriteTallyAtEnd 1 R
qSkipRightNumberTalliesAndWriteTallyAtEnd 0 qSkipRightNumberTallies 1 L

/*
qSkipRightNumberTallies
Traverse the tallies of the right number (moving left) without modifying them,
then transition to qSkipLeftNumberTallies2.
*/
qSkipRightNumberTallies 1 qSkipRightNumberTallies 1 L
qSkipRightNumberTallies 0 qSkipLeftNumberTallies2 0 L


/*
qSkipLeftNumberTallies2 
Traverse the tallies of the left number (moving left) without modifying them,
then transition to qDeleteFirstTallyOrHalt, leaving the head at the first tally of the left number (if it exists).
*/
qSkipLeftNumberTallies2 1 qSkipLeftNumberTallies2 1 L
qSkipLeftNumberTallies2 0 qDeleteFirstTallyOrHalt 0 R
```
{% endcode %}

Here's a version without comments:

<pre data-line-numbers><code><strong>qDeleteFirstTallyOrHalt 1 qSkipLeftNumberTallies1 0 R
</strong>qDeleteFirstTallyOrHalt 0 qHalt 0 R
<strong>qSkipLeftNumberTallies1 1 qSkipLeftNumberTallies1 1 R
</strong>qSkipLeftNumberTallies1 0 qSkipRightNumberTalliesAndWriteTallyAtEnd 0 R
qSkipRightNumberTalliesAndWriteTallyAtEnd 1 qSkipRightNumberTalliesAndWriteTallyAtEnd 1 R
qSkipRightNumberTalliesAndWriteTallyAtEnd 0 qSkipRightNumberTallies 1 L
qSkipRightNumberTallies 1 qSkipRightNumberTallies 1 L
qSkipRightNumberTallies 0 qSkipLeftNumberTallies2 0 L
qSkipLeftNumberTallies2 1 qSkipLeftNumberTallies2 1 L
qSkipLeftNumberTallies2 0 qDeleteFirstTallyOrHalt 0 R
</code></pre>

That's it! You've just written your first Varphi program :tada:
