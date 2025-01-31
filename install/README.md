# Get the Varphi Interpreter

### Downloading through GitHub Releases

Varphi has an official interpreter, with precompiled binaries available for download on Varphi's [GitHub Releases page](https://github.com/varphi-lang/varphi/releases/tag/v1.0.0). These binaries have been compiled for the following operating systems:

* Windows 10 and 11
* MacOS 13, 14, and 15
* Ubuntu 20.04, 22.04, and 24.04
* Windows Server 2019, 2022, and 2025

No prerequisite programs are required to install and use these binaries.

### Building From Source

{% hint style="info" %}
If your operating system is listed above, it is strongly recommended to download a precompiled version of the Varphi Interpreter.&#x20;
{% endhint %}

It is possible to build the Varphi Interpreter from source. To do so, you will need the following dependencies installed on your machine and on your PATH:

* [Python](https://www.python.org/) (at least version 3.13)
* [Java 23](https://www.oracle.com/ca-en/java/technologies/downloads/#java23)
* [cURL](https://curl.se/download.html)
* Make
* Git

Once you ensure you have these dependencies, please follow the following steps:

1. Clone the Varphi source code repository:

```shell-session
$ git clone https://github.com/varphi-lang/varphi.git
```

2. Change into the `varphi` directory:

```shell-session
$ cd varphi
```

3. Build the `vpi` executable:

```shell-session
$ make executable
```

The Varphi Interpreter should then be available under `bin/vpi` (or `bin\vpi.exe` if you are on Windows), assuming you're in the `varphi` directory.
