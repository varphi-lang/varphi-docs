# Running Varphi Programs

{% hint style="info" %}
This guide assumes you have already have the Varphi Interpreter (vpi) installed on your machine. If not, please refer to the [Installation Guide](https://app.gitbook.com/o/hMeTnvPNTmM7sZRSGpuI/s/rKaYRM7NKhGo5JuTSl9j/).
{% endhint %}

## File Extensions

The Varphi Interpreter does not explicitly check for a particular extension for input files. However, it is considered a good practice to use the .vp extension anyways.&#x20;

## Using the Varphi Interpreter

For this guide, we'll use the Varphi program that we created from the [last section](your-first-varphi-program.md), where we add two positive integers. For your convenience, we have included it below (the version without comments):

```
qDeleteFirstTallyOrHalt 1 qSkipLeftNumberTallies1 0 R
qDeleteFirstTallyOrHalt 0 qHalt 0 R
qSkipLeftNumberTallies1 1 qSkipLeftNumberTallies1 1 R
qSkipLeftNumberTallies1 0 qSkipRightNumberTalliesAndWriteTallyAtEnd 0 R
qSkipRightNumberTalliesAndWriteTallyAtEnd 1 qSkipRightNumberTalliesAndWriteTallyAtEnd 1 R
qSkipRightNumberTalliesAndWriteTallyAtEnd 0 qSkipRightNumberTallies 1 L
qSkipRightNumberTallies 1 qSkipRightNumberTallies 1 L
qSkipRightNumberTallies 0 qSkipLeftNumberTallies2 0 L
qSkipLeftNumberTallies2 1 qSkipLeftNumberTallies2 1 L
qSkipLeftNumberTallies2 0 qDeleteFirstTallyOrHalt 0 R
```

The first step is to create a file and save this code to it. We'll assume the file's name is `add.vp` , but feel free to name it anything you wish!

We'll now run this program on our example from the last section, where we added $$3$$ and $$2$$. To do so, run the following command

```shell-session
$ <PATH TO vpi> add1.vp
```

You should notice that no output is produced, for the interpreter is waiting for you to provide the input tape. Since we're adding $$3$$ and $$2$$, the input tape is `111011` (remember, `0` represents a blank tape cell, not a tape cell with the character "0"). Type this string into your terminal and hit ENTER. The output tape should then be printed on the terminal.

```shell-session
$ <PATH TO vpi> add1.vp
111011
000011111
```

{% hint style="info" %}
Remark: The Varphi Interpreter does not produce any output when you execute it on an input program, since it will be waiting for the input tape on standard input. No prompt appears that asks for this. It is common to confuse this as the interpreter "loading" or "hanging," when in reality it is just waiting for the input tape.
{% endhint %}

Now recall the output convention from the last section:

> There shall only be one contiguous block of tallies, which will represent the output of the Turing machine. If there are $$n$$ tallies in the contiguous block, then the number being represented by the tape is $$n$$.

Under this output convention, the output tape, `000011111` , represents the decimal number $$5$$, which is a correct result (as $$3 + 2 = 5$$)!&#x20;

{% hint style="info" %}
The Varphi interpreter automatically prints out all tape cells that have ever been accessed. This includes tape cells that have been written to (even when writing the input tape) and read from.
{% endhint %}
