# How to use FINN on qce-alveo01

## FINN

FINN is an open source experimental framework from Xilinx research labs, it allows the user to explore deep neural network inference on FPGAs. 

> For information: [FINN documentation](https://finn.readthedocs.io/en/latest/) and [FINN GitHub repository](https://github.com/Xilinx/finn)

## Setup on qce-alveo01

The following explains how FINN can be used on the servers. Instead of Docker a pre-built singularity container for the master branch of FINN is used.

### 1. Clone necessary repos 

- Clone all (or most relevant) dependency repos to your home directory

- e.g.

```shell
mkdir repositories
cd repositories
git clone  https://github.com/Xilinx/finn.git
git clone https://github.com/Xilinx/brevitas.git
git clone https://github.com/Xilinx/finn-hlslib.git
```
