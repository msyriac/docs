# Compilers on HPC

## `Illegal Instruction` errors

Some HPC systems like Princeton's `della` cluster can have sufficiently different architectures between the login node and the compute node that you get `Illegal Instruction` errors. This happens if the `-march=native` flag is enabled during compilation and can be fixed by simply removing that flag.

## Forcing `distutils` to use Intel

Something like this

``
LDSHARED="icc -shared" CC=icc $(PYTHON) setup.py build_ext --inplace
``

seems to be necessary to force Python's distutils to use an Intel compiler instead of gcc.

## What instruction sets does a program/library use

Sigurd has made:
http://folk.uio.no/sigurdkn/amop

One can do e.g.:
``
amop libsharp.a 
``

to list the instructions used.

## Show dependencies

``
ldd file.so
``

