# Compilers on HPC

## `Illegal Instruction` errors

Some HPC systems like Princeton's `della` cluster can have sufficiently different architectures between the login node and the compute node that you get `Illegal Instruction` errors. This happens if the `-march=native` flag is enabled during compilation and can be fixed by simply removing that flag.