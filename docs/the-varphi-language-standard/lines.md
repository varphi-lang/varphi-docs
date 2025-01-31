# Lines

### Structure

A _line_ represents a transition rule in the Turing machine. Every line consists of five elements in the following order:

1. A state name representing the current state of the Turing machine.
2. A tally or blank representing the condition of the tape cell that the head is currently positioned at.
3. A state name representing the state the Turing machine is left in after the transition is applied.
4. A tally or blank representing the condition of the tape cell after the transition is applied.
5. A head direction representing the direction the head will move in after the transition is applied.

A general line will look like the following:

```
STATE_NAME1 TALLY|BLANK STATE_NAME2 TALLY|BLANK HEAD_DIRECTION
```

{% hint style="info" %}
The space between elements of a line is not restricted to being a single space. Any whitespace can be added between elements of a line without causing syntax errors, which makes it possible to format programs!
{% endhint %}

{% hint style="info" %}
The parser uses the following pattern to match lines (assuming single spaces between elements, though this is not required):

<pre><code><strong>q[a-zA-Z0-9_]+ 0|1 q[a-zA-Z0-9_]+ 0|1 L|R
</strong></code></pre>
{% endhint %}

### The Condition and the Instruction

The first two elements of a Varphi line are called the _condition._ The condition can be read as follows:

> If
>
> 1. the Turing machine is using state \[state], and
> 2. the tape cell which the head is currently situated at \[contains a tally/is blank]

The remaining three elements of the line are called the _instruction_. They _instruct_ the Turing machine to perform a series of actions. You can read the instruction as follows:

> Make
>
> 1. the Turing machine use state \[state]
> 2. the tape cell at the which the head is currently situated at \[contain a tally/blank]
> 3. the head move to the tape cell immediately to the \[left/right] of the tape cell which it is currently situated at.

Overall, you can read a Varphi line as follows:

> If
>
> 1. the Turing machine is using state \[state]
> 2. the tape cell which the head is currently situated at \[contains a tally/is blank],
>
> then make
>
> 1. the Turing machine use state \[state]
> 2. the tape cell at the which the head is currently situated at \[contain a tally/blank]
> 3. the head move to the tape cell immediately to the \[left/right] of the tape cell which it is currently situated at.
