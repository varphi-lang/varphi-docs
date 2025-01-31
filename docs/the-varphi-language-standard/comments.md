# Comments

Comments enhance code readability by providing explanations and context. They can also be used to temporarily disable code when testing alternate code.

Varphi conveniently uses C-style comments. There are two types of comments in Varphi:

1. Inline (single-line) comments
2. Block (multi-line) comments

## Inline Comments

An inline comment begins with `//`. Any text following `//` on the same line is ignored by the compiler and does not affect execution.

Inline comments can appear on lines of a source file by themselves:

```clike
// This is a comment!
```

Inline comments can also appear at the end of a Varphi line:

```clike
q0 1 q0 1 R // If a tally is encountered while on state q0, skip it...
```

## Block Comments

A block comment begins with `/*` and ends with `*/`. Any text enclosed within these markers is ignored by the compiler. Block comments are useful for providing detailed explanations spanning multiple lines.

Here's an example of a block comment spanning multiple lines:

```
/* 
State q0:
- Skip all cells with tallies
- When the first blank tape cell is reached, put a tally there and halt
*/
q0 1 q0 1 R
q0 0 q1 1 L
```

