###Build Numpy with varies linear algebra libs and Linux distros

#####Python3.4.2 Ubuntu14.04LT(AWS) openblas (0.2.13)

1) Download and build latest openblas (0.2.13). Install it at /path/to/openblas

2) Download and unpack numpy (1.9.1). Modify site.cfg as:

    [DEFAULT]
    library_dirs = /home/ubuntu/workspace/.local/lib

    [atlas]
    libraries = openblas
    include_dirs = /home/ubuntu/workspace/.local/include

