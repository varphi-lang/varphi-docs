# Good Practices

## Comments

From our example in [this section](your-first-varphi-program.md), it is clear that writing comments to explain what each state does is important for readers to understand your programs.&#x20;

To document a state, you should open a [block comment](../the-varphi-language-standard/comments.md) before it and try your best to explain the following details:

1. The purpose of the state
2. What the machine does if a tally is encountered at the current tape cell when on the state
3. What the machine does if a blank tape cell is encountered at the current tape cell when on the state

## Number of States

When possible, try to limit the number of states your Varphi program uses to avoid a large file. This may be accomplished by moving to a simple algorithm. This is a concept that is applied in every other programming language (although not necessarily with state names like in Varphi, but perhaps with variables).&#x20;

## State Names

State names can follow any identifier naming case style you prefer. However, you should ensure that the names of your states are clear, especially in larger programs, as the number of states required by algorithms tends to grow extremely fast as the algorithms become more complex.&#x20;

## File Naming Conventions

Files should be given a name that is descriptive of the Turing machine they represent, and should end with the .vp extension.

{% hint style="info" %}
The .vp extension is not a requirement for Varphi files, but it is conventional to give Varphi files this extension.&#x20;
{% endhint %}

## Final Move of the Head

On a Varphi line where you are transitioning to a halting state, pay attention to the direction you move the head before halting. If possible, move the head in a direction such that its final position will be an already-visited tape cell. If you move the head in a direction such that its final position is not an already visited tape cell, then that tape cell will be considered visited, and will be displayed in the output tape (the Varphi Interpreter will automatically display all visited tape cells in the output tape).&#x20;

