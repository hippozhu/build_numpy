##Build Numpy with varies linear algebra libs and Linux distros

####Python3.4.2 Ubuntu14.04LT(AWS) openblas (0.2.13)

1) Download and build latest openblas (0.2.13). Install it at /path/to/openblas

2) Download and unpack numpy (1.9.1). Modify site.cfg as:

    [DEFAULT]
    library_dirs = /path/to/openblas/lib

    [atlas]
    libraries = openblas
    include_dirs = /path/to/openblas/include
"openblas" appears in [atlas] section because "Numpy will try to build against Atlas by default when available in the system library dirs". The same reason why library_dirs in [DEFAULT] is changed to openblas lib directory.

3) Build & install numpy:
    
    $ python3 setup.py build
    $ sudo python3 setup.py install

4) Verify:
    
    $ python3 -c "import numpy;numpy.__config__.show()"
    lapack_opt_info:
        library_dirs = ['/path/to/openblas/lib']
        language = f77
        libraries = ['openblas']
    blas_opt_info:
        library_dirs = ['/path/to/openblas/lib']
        language = f77
        libraries = ['openblas']
    openblas_info:
        library_dirs = ['/path/to/openblas/lib']
        language = f77
        libraries = ['openblas']
    blas_mkl_info:
    NOT AVAILABLE
    openblas_lapack_info:
        library_dirs = ['/path/to/openblas/lib']
        language = f77
        libraries = ['openblas']
