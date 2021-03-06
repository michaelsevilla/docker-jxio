Wraps a given JXIO codebase in a container that can be seen as a JXIO remote (a.k.a. test node). This is basically build dependencies, plus an sshd, plus environment setup so that (1) the experiment master can communicate with the container via SSH and (2) binaries built from source are in the PATH.

===================================================
Quickstart
===================================================

To build JXIO:

    ```bash
    docker run -it \
        --name jxio \
        -v `pwd`/JXIO:/JXIO \
        michaelsevilla/jxiodev-build
    ```

To start JXIO server:

    ```bash
    docker run -it \
        --name jxio \
        --net=host \
        -v `pwd`/JXIO:/JXIO \
        --entrypoint=/bin/bash \
        michaelsevilla/jxiodev-build
    ```

This will drop you into a shell where you can run JXIO:

    /JXIO/examples/runHelloWorld.sh server localhost 1234
    /JXIO/examples/runHelloWorld.sh client localhost 1234 

