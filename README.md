# sagemath-resources

Resources I'm using to teach / introduce SageMath.
Additionally resources I use to teach myself.


## Docker

The [official SageMath Docker images](https://hub.docker.com/u/sagemath/#!) require differentiation between `py` and `py3`; in general, prefer the command 
```bash
docker pull sagemath/sagemath:latest-py3
```
to get the Python3 version of SageMath (I'm unsure if the tag `latest` still maps to py2?).

The default working directory of the sagemath docker image is
```
/home/sage
```

A handly little shell script to use is then:
```
#!/bin/bash

WORKING_DIR=${NOTEBOOK_DIR:-~/Documents/SageMath}

echo "Using working directory local:$WORKING_DIR"

docker run --rm -p 8888:8888 -v $WORKING_DIR:/home/sage/notebooks --name sagemath sagemath/sagemath:latest-py3 sage-jupyter
```

Which will default the persitent notebook directory to your Documents folder, and init a jupyter kernel for you.

Any notebooks created in `~/notebooks` on the filesystem of the docker image will then be saved on the host machine.
```
