# Environment Modules

## Introduction

[Environment Modules](http://modules.sourceforge.net/) is a package that provides for the dynamic modification of a user's environment via modulefiles. By utilizing this package we can install multiple versions of the same application and be able to load each application seperately without having the libraries and environment from the other versions conflict with each other. 

It use to be that you would install a program on a computer and just use that version. However, in research situations, sometimes we need to be able to use different versions of the same software in order to compare results between them for example. So by using environment modules it allows us to be able to utilize many different versions of software and allow the user to pick which application and version that they would like to use. 

## List Modules


    [slyoung@grid ~]% module avail
    ------------------------------------------------ /etc/modulefiles --------------------------------------------------
    mpi/mpich-3.0-x86_64    mpi/mpich-3.2-x86_64    mpi/mpich-x86_64        mpi/mvapich2-2.0-x86_64 mpi/mvapich2-2.2-x86_64 
    mpi/mvapich2-x86_64
    -------------------------------------- /usr/local/global/modulefiles --------------------------------------------------
    amber/14            cuda/7.5            gaussian/03         namd/2.12           namd/2.12-ib        openmpi/3.0.0       
    R/3.4.2
    amber/16            cuda/8.0            matlab/R2016a       namd/2.12-cuda      namd/2.12-src       python/anaconda-5.0

## Load Modules

    [slyoung@grid ~]% which python
    /bin/python
    [slyoung@grid ~]% module load python/anaconda-5.0
    [slyoung@grid ~]% which python
    /usr/local/Dist/anaconda-5.0.0/bin/python
    [slyoung@grid ~]% 

## Unload Modules

## Creating your own Modules

## Documentation

 - [Environment Modules site](http://modules.sourceforge.net/)
 - [Environment Modules Documentation](https://modules.readthedocs.io/en/latest/)


