Wraps a given JXIO codebase in a container that can be seen as a JXIO remote (a.k.a. test node). This is basically build dependencies, plus an sshd, plus environment setup so that (1) the experiment master can communicate with the container via SSH and (2) binaries built from source are in the PATH.

===================================================
Quickstart
===================================================

To build JXIO:

    docker ps -aq | xargs docker stop
    docker ps -aq | xargs docker rm
    docker run -it \
        --name jxio \
        -v `pwd`/JXIO:/JXIO \
        jxio
    
To start JXIO server:

    docker ps -aq | xargs docker stop
    docker ps -aq | xargs docker rm
    docker run -it \
    --name jxio \
    --net=host \
    -v `pwd`/JXIO:/JXIO \
    --entrypoint=/bin/bash \
    jxio

    /JXIO/examples/runHelloWorld.sh server localhost 1234
    /JXIO/examples/runHelloWorld.sh client localhost 1234 

