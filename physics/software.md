# Reminders for specific physics/astronomy/cosmology software


## CosmoMC + WMAP

- On NERSC, wmap + Cosmomc requires Cfitsio 3.410

## CosmoMC without iFort and with GCC6

After compiling GCC6, you need to compile LAPACK with GCC6 and add it to library path. You will likely get some `gomp` related errors. I got around this by manually copying files like `libgomp.spec` and `libgomp.so` into library paths.

## Healpy with Intel compilers

In the git cloned directory, do:

``
CXX=icpc CXXL=icpc LDSHARED="icc -shared" CC=icc python setup.py build_ext -i --compiler=intelem -c icc -vvv
``

and add to the Python path.