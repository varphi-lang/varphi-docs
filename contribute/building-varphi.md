# Building Varphi

{% hint style="info" %}
This guide assumes the following command-line programs are located on your PATH:

* [Python](https://www.python.org/) (at least version 3.13)
* [Java 23](https://www.oracle.com/ca-en/java/technologies/downloads/#java23)
* [cURL](https://curl.se/download.html)
* Make
* Git
{% endhint %}

## Cloning the Repository

Varphi is a completely open-source language. It is hosted on a [public GitHub repository](https://github.com/varphi-lang/varphi). You can get the source on your local machine by cloning the repository. You can do so by running the following command in a new terminal:

```shell-session
$ git clone https://github.com/varphi-lang/varphi.git
```

A new directory named `varphi` should now be created with the source code under it. Change into this directory:

```shell-session
$ cd varphi
```

For the rest of this guide, it is assumed that your terminal is changed into the Varphi root directory.

## Building Varphi

Varphi uses Make for building the project. The easiest way to build everything in the Varphi project is by running

```shell-session
$ make executable
```

This will generate the lexer and parser, install the Varphi-to-Python Compiler as a package (called `varphi`) in a Python virtual environment, and generate the Varphi Interpreter (vpi) binary for your operating system under `bin/vpi`(or `bin\vpi.exe` if you have a Windows machine).

You can also build individual components of the Varphi project, as shown below.

<details>

<summary>Building the Lexer and Parser</summary>

To build the lexer and parser, run

```shell-session
$ make parsing
```

You should see the `varphi/parsing` directory become populated with the following three Python files:

1. `VarphiLexer.py`
2. `VarphiParser.py`
3. `VarphiListener.py`

</details>

<details>

<summary>Installing the Varphi-to-Python Compiler as a Python Package</summary>

To install the Varphi-to-Python compiler as a Python package in a Python virtual environment, run

```shell-session
$ make install
```

NOTE: This will build the lexer and parser as a side effect, as the lexer and parser are needed as a prerequisite.&#x20;

</details>

##

