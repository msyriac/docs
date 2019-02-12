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

## FFTW idiosyncracies

On systems like Niagara, an Intel version of fftw is the default module. This has a bug which makes it impossible to FFT multi-dimensional arrays.

If you are going to compile FFTW yourself, then you have to use gcc, and this is what it will typically look like:

``
# single precision
./configure CC=gcc CXX=g++ CFLAGS=-fPIC --enable-openmp --enable-mpi --enable-sse --enable-sse2 --enable-avx --enable-avx2 --enable-float --enable-shared --prefix=/home/r/rbond/msyriac/.local/lib
make -j24 CFLAGS=-fPIC
make install
make clean
# double precision
./configure CC=gcc CXX=g++ CFLAGS=-fPIC --enable-openmp --enable-mpi --enable-sse2 --enable-avx --enable-avx2 --enable-shared --prefix=/home/r/rbond/msyriac/.local
make -j24 CFLAGS=-fPIC
make install
make clean
./configure CC=gcc CXX=g++ CFLAGS=-fPIC --enable-openmp --enable-mpi --enable-long-double --enable-shared --prefix=/home/r/rbond/msyriac/.local
make -j24 CFLAGS=-fPIC
make install
make clean
``

and pyfftw with

``
pip install pyfftw --user
``