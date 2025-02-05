# Rock, Paper, Scissors

Below is a program which determines the winner of a game of [Rock, Paper, Scissors ](https://en.wikipedia.org/wiki/Rock_paper_scissors)between two players.&#x20;

The machine accepts an input tape containing two contiguous blocks of tallies separated by a blank tape cell, representing the moves of the two players. The first block of tallies (i.e., to the left) will represent the move of the first player, and the second block will represent the move of the second player.

Each contiguous block for a player's move can look like the following:

* `1` , if the move is Rock
* `11` , if the move is Paper
* `111` , if the move is Scissors

For example, the input tape `110111` would represent that the first player played Paper, and the second player played Scissors.

The output tape will be a contiguous block of tallies representing the result of the game. This output tape will take on one of the following forms:

* `1` , if the result was a tie
* `11` , if the first player won
* `111` , if the second player won

```
qUnknown 1 qRock 0 R
qRock 1 qPaper 0 R
qPaper 1 qScissors 0 R

qRock 0 qRockUnknown 0 R
qPaper 0 qPaperUnknown 0 R
qScissors 0 qScissorsUnknown 0 R

qRockUnknown 1 qRockRock 0 R
qPaperUnknown 1 qPaperRock 0 R
qScissorsUnknown 1 qScissorsRock 0 R

qRockRock 1 qRockPaper 0 R
qRockPaper 1 qRockScissors 0 R

qPaperRock 1 qPaperPaper 0 R
qPaperPaper 1 qPaperScissors 0 R

qScissorsRock 1 qScissorsPaper 0 R
qScissorsPaper 1 qScissorsScissors 0 R

qRockRock 0 qTie 0 R
qRockPaper 0 qPlayer2Won 0 R
qRockScissors 0 qPlayer1Won 0 R
qPaperRock 0 qPlayer1Won 0 R
qPaperPaper 0 qTie 0 R
qPaperScissors 0 qPlayer2Won 0 R
qScissorsRock 0 qPlayer2Won 0 R
qScissorsPaper 0 qPlayer1Won 0 R
qScissorsScissors 0 qTie 0 R

qTie 0 qWrite1 0 R
qPlayer1Won 0 qWrite2 0 R
qPlayer2Won 0 qWrite3 0 R

qWrite1 0 qHalt 1 R
qWrite2 0 qWrite1 1 R
qWrite3 0 qWrite2 1 R
```

