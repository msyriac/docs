# Compilers on HPC

## `Illegal Instruction` errors

Some HPC systems like Princeton's `della` cluster can have sufficiently different architectures between the login node and the compute node that you get `Illegal Instruction` errors. This happens if the `-march=native` flag is enabled during compilation and can be fixed by simply removing that flag.

## Forcing `distutils` to use Intel

Something like this

``
LDSHARED="icc -shared" CC=icc $(PYTHON) setup.py build_ext --inplace
``

seems to be necessary to force Python's distutils to use an Intel compiler instead of gcc.