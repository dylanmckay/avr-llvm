# AVR-LLVM

[![Build Status](https://travis-ci.org/avr-llvm/llvm.svg?branch=avr-support)](https://travis-ci.org/avr-llvm/llvm)

*NOTE: The AVR backend has now been completely upstreamed into LLVM trunk. Development will no longer
occur on this repository - it will occur directly in LLVM [trunk](http://llvm.org/viewvc/llvm-project/llvm/trunk/lib/Target/AVR)*

See the [Wiki](https://github.com/avr-llvm/llvm/wiki/Getting%20Started) for more information.

An LLVM backend for the Atmel [AVR](http://en.wikipedia.org/wiki/Atmel_AVR) microprocessor architecture.

Currently AVR-LLVM can generate assembly files and ELF object files.

As the project is still very much in development, it is likely that you will encounter bugs. If you think you've found one, submit an issue - we're aiming for AVR-LLVM to eventually be
a production-quality compiler backend, so bugs will not be tolerated.

AVR-related code can be found in `lib/Target/AVR`.

## Related projects

* [Rust for AVR](https://github.com/avr-rust/rust)

## Features

* Assembly or machine code generation
* Support for the entire instruction set
* ELF object file support
* AVR-GCC compatability
* Permissive license

## History

The original project started several years ago and then it was abandoned. It is hosted on [SourceForge.net](http://sourceforge.net/projects/avr-llvm).

A fork was created which updated the project to a more recent version of LLVM, which is located on [GitHub](https://github.com/sushihangover/llvm-avr).

This repository is a fork of the updated version.

The AVR-LLVM project aims to keep to code updated (so that it's always compatible with LLVM master), and also to improve the backend.

## Goals

We would like to be able to compile any program that AVR-GCC can, have comparable diagnostics, and on-par performance.

Ideally, the avr-llvm project would provide a drop-in 100% compatible replacement for AVR-GCC and binutils.

## Contributing

Any improvement, however minor, is welcomed :)

Take a look at the issues page for goals and bugs that currently exist. Pull requests are very welcome!

For more information, please read the [Contributing](https://github.com/avr-llvm/llvm/wiki/Contributing) page on the Wiki.

## Submitting Bugs

Bugs can be reported on the GitHub issue [tracker](https://github.com/avr-llvm/llvm/issues).

It is useful to submit small testcases (generally LLVM IR files) that reproduce the bug. We prefer IR files over
C/C++ sources for several reasons:

* They often require headers or libraries that we must also install (e.g. Arduino)
* They require building clang (which we don't often do, as it takes a long time)
* They are smaller and self-contained

If you want to submit a C/C++ testcase, please convert into IR form first.

To do this:
``` bash
# compile `main.c` into `main.ll`
clang -S -emit-llvm main.c -o main.ll
```

This will add all included headers, and concatenate it into one simple file.

Good luck!
