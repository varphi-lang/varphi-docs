# Debugging Varphi Programs

## Things Can Go Wrong

Writing Varphi programs is not like writing programs in other languages, since it uses a completely different paradigm. It is very easy to write the wrong state name in the instruction part of a line, or to have incorrect logic somewhere. When things do go wrong, you can debug your code with Varphi.

## The Varphi Command-Line Debugger

The Varphi Command-Line Debugger ships with the Varphi interpreter, and can be used by supplying the `-d` option to `vpi` . We'll continue to use our running example of the addition program from [this section](your-first-varphi-program.md).&#x20;

Let's run the Varphi program in debug mode. Run the following command

```shell-session
$ <PATH TO vpi> -d add1.vp
```

Again, you should see no output, since you must supply the input tape first. Let's do that:

```shell-session
$ <PATH TO vpi> -d add1.vp
111011
State:  qDeleteFirstTallyOrHalt
Tape:  [{1}]11011
Press ENTER to step...
```

The debugger shows you the current state, as well as some details of the tape. You may notice the square braces `[]` and curly braces `{}` . These are explained below:

* Square braces `[]` around an element of the tape indicate that the head is currently stationed at that tape cell.
* Curly braces `{}` around an element of the tape indicate that this tape cell was the tape cell which held the first tally in the input tape. It can be used as a "reference point" when debugging.

As you can see from the output of the debugger, you can step through the program by pressing ENTER. When the program finishes executing, the output tape will be printed and the debugger will exit.&#x20;

In case you're interested, here's the whole session output for this debugger run:

```shell-session
$ <PATH TO vpi> -d add1.vp
111011
State:  qDeleteFirstTallyOrHalt
Tape:  [{1}]11011
Press ENTER to step...

State:  qSkipLeftNumberTallies1
Tape:  {0}[1]1011
Press ENTER to step...

State:  qSkipLeftNumberTallies1
Tape:  {0}1[1]011
Press ENTER to step...

State:  qSkipLeftNumberTallies1
Tape:  {0}11[0]11
Press ENTER to step...

State:  qSkipRightNumberTalliesAndWriteTallyAtEnd
Tape:  {0}110[1]1
Press ENTER to step...

State:  qSkipRightNumberTalliesAndWriteTallyAtEnd
Tape:  {0}1101[1]
Press ENTER to step...

State:  qSkipRightNumberTalliesAndWriteTallyAtEnd
Tape:  {0}11011[0]
Press ENTER to step...

State:  qSkipRightNumberTallies
Tape:  {0}1101[1]1
Press ENTER to step...

State:  qSkipRightNumberTallies
Tape:  {0}110[1]11
Press ENTER to step...

State:  qSkipRightNumberTallies
Tape:  {0}11[0]111
Press ENTER to step...

State:  qSkipLeftNumberTallies2
Tape:  {0}1[1]0111
Press ENTER to step...

State:  qSkipLeftNumberTallies2
Tape:  {0}[1]10111
Press ENTER to step...

State:  qSkipLeftNumberTallies2
Tape:  [{0}]110111
Press ENTER to step...

State:  qDeleteFirstTallyOrHalt
Tape:  {0}[1]10111
Press ENTER to step...

State:  qSkipLeftNumberTallies1
Tape:  {0}0[1]0111
Press ENTER to step...

State:  qSkipLeftNumberTallies1
Tape:  {0}01[0]111
Press ENTER to step...

State:  qSkipRightNumberTalliesAndWriteTallyAtEnd
Tape:  {0}010[1]11
Press ENTER to step...

State:  qSkipRightNumberTalliesAndWriteTallyAtEnd
Tape:  {0}0101[1]1
Press ENTER to step...

State:  qSkipRightNumberTalliesAndWriteTallyAtEnd
Tape:  {0}01011[1]
Press ENTER to step...

State:  qSkipRightNumberTalliesAndWriteTallyAtEnd
Tape:  {0}010111[0]
Press ENTER to step...

State:  qSkipRightNumberTallies
Tape:  {0}01011[1]1
Press ENTER to step...

State:  qSkipRightNumberTallies
Tape:  {0}0101[1]11
Press ENTER to step...

State:  qSkipRightNumberTallies
Tape:  {0}010[1]111
Press ENTER to step...

State:  qSkipRightNumberTallies
Tape:  {0}01[0]1111
Press ENTER to step...

State:  qSkipLeftNumberTallies2
Tape:  {0}0[1]01111
Press ENTER to step...

State:  qSkipLeftNumberTallies2
Tape:  {0}[0]101111
Press ENTER to step...

State:  qDeleteFirstTallyOrHalt
Tape:  {0}0[1]01111
Press ENTER to step...

State:  qSkipLeftNumberTallies1
Tape:  {0}00[0]1111
Press ENTER to step...

State:  qSkipRightNumberTalliesAndWriteTallyAtEnd
Tape:  {0}000[1]111
Press ENTER to step...

State:  qSkipRightNumberTalliesAndWriteTallyAtEnd
Tape:  {0}0001[1]11
Press ENTER to step...

State:  qSkipRightNumberTalliesAndWriteTallyAtEnd
Tape:  {0}00011[1]1
Press ENTER to step...

State:  qSkipRightNumberTalliesAndWriteTallyAtEnd
Tape:  {0}000111[1]
Press ENTER to step...

State:  qSkipRightNumberTalliesAndWriteTallyAtEnd
Tape:  {0}0001111[0]
Press ENTER to step...

State:  qSkipRightNumberTallies
Tape:  {0}000111[1]1
Press ENTER to step...

State:  qSkipRightNumberTallies
Tape:  {0}00011[1]11
Press ENTER to step...

State:  qSkipRightNumberTallies
Tape:  {0}0001[1]111
Press ENTER to step...

State:  qSkipRightNumberTallies
Tape:  {0}000[1]1111
Press ENTER to step...

State:  qSkipRightNumberTallies
Tape:  {0}00[0]11111
Press ENTER to step...

State:  qSkipLeftNumberTallies2
Tape:  {0}0[0]011111
Press ENTER to step...

State:  qDeleteFirstTallyOrHalt
Tape:  {0}00[0]11111
Press ENTER to step...

State:  qHalt
Tape:  {0}000[1]1111
Press ENTER to step...

000011111
$ 
```

