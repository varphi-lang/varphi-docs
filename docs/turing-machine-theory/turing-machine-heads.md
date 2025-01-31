# Turing Machine Heads

## The Head

In the context of a Turing machine, the _head_ is a component that can read from, write to, and traverse the tape.&#x20;

The head is restricted to being stationed at exactly one tape cell at a time. That is, it cannot read or write a block of cells (more than one cell) at one time. Additionally, the head cannot "teleport" to a certain tape cell that is not immediately to the left or right of the tape cell it is currently stationed at. It can only move to the left or to the right by exactly one tape cell at a time.&#x20;

As a device, the head can perform the following actions:

1. Read the current tape cell
2. Write a tally ($$1$$) to the current tape cell
3. Make the current tape cell blank
4. Move to the tape cell immediately to the right of the current one
5. Move to the tape cell immediately to the left of the current one

However, the head only accepts instructions that are in one of the following formats:

1. Read the current tape cell
2. Write a tally to the current tape cell and move to the tape cell immediately to the right of the current one
3. Write a tally to the current tape cell and move to the tape cell immediately to the left of the current one
4. Make the current tape cell blank and move to the tape cell immediately to the right of the current one
5. Make the current tape cell blank and move to the tape cell immediately to the left of the current one

The Turing machine will supply such instructions to the head as part of its operation.
