# Codebase Structure

## Varphi's High-Level Process

Here is a timeline of events that happen when a user invokes the Varphi Interpreter (`vpi`) on a Varphi file:

{% stepper %}
{% step %}
### Argument Handling

The Varphi Interpreter executable, through [Python's argparse](https://docs.python.org/3/library/argparse.html), parses the arguments supplied to the executable. It extract's the user's Varphi source code file path, and determines what the compilation target will be (either a command-line program, command-line program with debugging, or debug adapter).&#x20;
{% endstep %}

{% step %}
### Compiler API Call

The Varphi Interpreter makes an API call to the Varphi-to-Python compiler, sending the file name of the user's Varphi source code file.&#x20;
{% endstep %}

{% step %}
### Lexing

The user's Varphi source code file is opened for reading, and it's contents are passed through a lexer. The lexer _tokenizes_ the code and catches specific syntax errors at this stage (specifically, a syntax error is thrown by the lexer only if a line element does not fit the criteria to be a state name, tally, blank, or head direction).&#x20;
{% endstep %}

{% step %}
### Parsing

The tokens from the lexer are passed into a parser, which combines them to form internal representations of the Varphi lines in the user's source code. If there are any malformed lines in the user's source code, syntax errors will be thrown by the parser.&#x20;
{% endstep %}

{% step %}
### Translator

The translator goes through the internal representations of the Varphi lines and, for each line, produces equivalent Python code. This Python code, using the Varphi Runtime Library written in Python, will match the behavior of the user's Varphi source code.
{% endstep %}

{% step %}
### Evaluating the Compiled Code

Once every line has been stepped through by the translator, a string containing the compiled Python code is sent to the interpreter. A call to [Python's `exec`](https://docs.python.org/3/library/functions.html#exec) is made on the compiled Python code, which opens a session that the user can pass the input tape to and receive output from.&#x20;
{% endstep %}
{% endstepper %}

## Structure of the Codebase

The Varphi codebase consists of two parts:

1. The Varphi-to-Python Compiler
2. The Varphi Interpreter

### The Varphi-to-Python Compiler

The Varphi-to-Python Compiler is a (non-published) Python package and is located under the `varphi` directory in the source code directory.&#x20;

The three components of the Varphi-to-Python Compiler are:

1. The lexer and parser
2. The translators (Compilers)
3. The Varphi Runtime Library

#### The Lexer and Parser

The lexer and parser are generated from a grammar file (`Varphi.g4`) and are not included in the source code. When Varphi is built, they are located under `varphi/parsing/VarphiLexer.py` and `varphi/parsing/VarphiParser.py`, respectively.

#### The Translators (Compilers)

Varphi includes a translator, or compiler, for every possible target (command-line program, debug adapter, etc.). These are located under `varphi/compilation/varphi_translator.py`.&#x20;

#### The Varphi Runtime Library

The Varphi Runtime Library is a set of utilities used by the Python code which Varphi programs are compiled to. This library is located under `varphi/runtime`.
