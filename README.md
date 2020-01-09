# mhar_release
This repository contains the C/CUDA code for the MHAR. It samples polytopes (fully or non-fully dimensional) determined by a set of equality and inequality constraints.


## Use
You can either download the code from this repository and compile it your self or use the dokcerized version with all the proper libraires (Dockerhub uumami/mhar). The container can easily run in cloud services with gpu architechtures. I extremely recommend using the dockerized version since it is much userfriendly and installation requierements are easier.


### Brief description
The code is wirtten in C and uses CUDA and MAGMA libraries (see https://icl.cs.utk.edu/projectsfiles/magma/doxygen/index.html), lpsolve, and the pcg generator. The Makefile compiles the code, if you are planning on compiling everything yourself you will also need to compile all the other corresponding libraries.


### Requirements

#### Docker Image
NVIDIA drivers capable of running CUDA 10.0 
Docker engine with CUDA capabilities (see https://github.com/NVIDIA/nvidia-docker)

#### Own Compilation
C compiler compatible with lpsolve, MAGMA and CUDA.
CUDA version capable of running the MAGMA libraries.
CUBLAS libraries.
Compiled MAGMA libraries (see contents section).
Compiled lpsolve libraries.
Compiled PCG libraries.


### Contents
Recall the dockerized version of the code compiles automatically. You only need a computer capable of running docker/cuda. For a tutorial of how to install Docker with CUDA capabilities please refer to: 
https://github.com/NVIDIA/nvidia-docker.


#### magma-2.5.1.tar.gz
The MAGMA libraries used for compiling the code. For an oficial tutorial of how to compile MAGMA please refer to:
https://icl.cs.utk.edu/projectsfiles/magma/doxygen/installing.html. This libraries allow us to make fast and precise matrix to matrix operations. Not mine, please thank the MAGMA team!

#### lpsolve
Libraries for finding the Chevyshev center, ultimately you can also pass the initial point as an argument.
As of now, the code does not check if your initialization point is inside the polygon, so please be careful. Official lpsolve page: http://lpsolve.sourceforge.net/5.5/

#### pcg-c-0.94
PCG pseudo random generator (contained in direction_creation). 

### Dockerfile
Is the base Dockerfile with the compiled MAGMA libraries and all the other necessary files to compile and run the rest of the code. Its for debugging porpouses mostly. 

#### Makefile
After compiling the MAGMA and lpsolve libraries this file will compile the code for the MHAR
