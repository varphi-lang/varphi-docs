# Turing Machines

> A Turing machine is a quadruple $$(Q, s, F, \delta)$$, where
>
> * $$Q$$ is a finite nonempty set of states (e.g., $$\{q_0, q_1,...,q_n\}$$, for some $$n\in\mathbb{N}$$.
> * $$s\in Q$$ is the initial state.
> * $$F\subseteq Q$$ is the set of final states.
> * $$\delta: (Q\setminus F)\times\{0, 1\}\rightarrow Q\times\{0, 1\}\times\{L, R\}$$ is the transition (partial) function.
>
> NOTE: Above, we represent "tally" using $$1$$, "blank" using $$0$$, "left" using $$L$$, and "right" using $$R$$.

Wow! That's a lot to take in. The first three items in the quadruple are pretty straightforward, but what is that fourth item? Let's describe this in a more gentle way:

> $$\delta: (Q\setminus F)\times\{0, 1\}\rightarrow Q\times\{0, 1\}\times\{L, R\}$$ is a partial function (may not be defined for some inputs in the domain) mapping pairs of non-final states and tape cell possibilities to triples containing a state, tape cell possibility, and head direction.

For example, if $$\delta$$ maps $$(q_0, 0)$$ to $$(q_1, 1, R)$$, then this can be read as "if the machine's state is $$q_0$$ and the current tape cell is blank, then switch to state $$q_1$$, place a tally at the current tape cell, and move the head to the tape cell immediately right of the current tape cell.&#x20;

{% hint style="info" %}
Since we previously mentioned that states do not need to define rules for all possible tape cell conditions, $$\delta$$ is a partial, not total, function.
{% endhint %}

Recall our example of adding two tallies to a number on a tape. We used the following algorithm:

Start at state $$q_0$$. Read the current tape cell.

* If we are on state $$q_0$$:&#x20;
  * If there is a tally at the current tape cell, write a tally to the current tape cell (leaving it as-is) and move to the tape cell immediately to the right of the current one. Stay on state $$q_0$$. Repeat.
  * If the current tape cell is blank, write a tally to the current tape cell and move to the tape cell immediately to the right of the current one. Switch to state $$q_1$$. Repeat.
* If we are on state $$q_1$$:
  * If the current tape cell is blank, write a tally to the current tape cell and move to the tape cell immediately to the right of the current one. Switch to state $$q_2$$. Repeat.

The transition function for this algorithm can be represented using a table:

<table><thead><tr><th>If on state</th><th>If read</th><th width="195">Then switch to state</th><th>Then write</th><th>Move</th></tr></thead><tbody><tr><td><span class="math">q_0</span></td><td><span class="math">1</span></td><td><span class="math">q_0</span></td><td><span class="math">1</span></td><td><span class="math">R</span></td></tr><tr><td><span class="math">q_0</span></td><td><span class="math">0</span></td><td><span class="math">q_1</span></td><td><span class="math">1</span></td><td><span class="math">R</span></td></tr><tr><td><span class="math">q_1</span></td><td>0</td><td><span class="math">q_2</span></td><td><span class="math">1</span></td><td><span class="math">R</span></td></tr></tbody></table>

Again, $$1$$ means "tally", $$0$$ means "blank", $$R$$ means "right", and $$L$$ means "left" here.

We can write the transition function in an even more compact notation as follows:

$$
q_0\quad 1 \quad q_0 \quad 1 \quad R\\
q_0\quad 0 \quad q_1 \quad 1 \quad R\\
q_1\quad 0 \quad q_2 \quad 1 \quad R
$$

The transition function of a Turing machine is extremely powerful. In fact, supplying just the transition function of a Turing machine gives you everything you need to know about the Turing machine except for the initial state of the machine. However, we will make the assumption that the initial state is the first state mentioned (that is, the state at the top left corner of the Turing program), which is called the [Top-Left Rule for Varphi](../the-varphi-language-standard/addressing-ambiguities.md). Writing the transition function in compact notation makes it very easy to describe Turing machines without heavy notation or tables.

Believe it or not, you've just written your first Varphi Program! Here it is in a code block.

```
q0 1 q0 1 R
q0 0 q1 1 R
q1 0 q2 1 R
```

Pretty simple, right?
