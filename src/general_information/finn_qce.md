# How to use FINN on qce-alveo01

Before you use FINN on qce-alveo01 check with `top` if someone else is using the server and discuss with the people whether you can start your experiments. FINN uses Vivado and Vitis and can use a lot of resources.

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

- You can find the necessary dependency repos [here](https://github.com/Xilinx/finn/blob/e443a5859066a410a63c08dcfec4a90527ca24be/docker/Dockerfile.finn_dev#L73)

- Checkout each repo the currently used git version, can be found [here](https://github.com/Xilinx/finn/blob/e443a5859066a410a63c08dcfec4a90527ca24be/docker/finn_entrypoint.sh#L13)

### 2. Open container

- Use pre-build singularity container from /work/singularity/xilinx-finn.sif

- Bind own version of dependency repos to the container

- If you are in just created directory *repository*, execute this command with the folders you want to bind:

```shell
singularity shell --bind finn:/workspace/finn --bind finn-hlslib:/workspace/finn-hlslib [...] /work/singularity/xilinx-finn.sif
```

### 3. Inside the container

- You have to set all the desired env variables manually and brevitas has to be installed (or just write a shell script and execute it with `source ./set_env_var.sh`)

```shell
export VIVADO_PATH="/opt/apps/xilinx/Vivado/2020.1"
source $VIVADO_PATH/settings64.sh
export VITIS_PATH="/opt/apps/xilinx/Vitis/2020.1"
source $VITIS_PATH/settings64.sh
export PLATFORM_REPO_PATHS="/opt/xilinx/platforms"
export XILINX_XRT="/opt/xilinx/xrt"
export FINN_INST_NAME="finn_dev_[username]"
pip install --user -e /workspace/brevitas
```

- Set env variable for your target device, for instance

```shell
export PYNQ_BOARD="Pynq-Z1"
```

or

```shell
export ALVEO_BOARD="U50"
```

- Other environment variable settings that might be necessary can be found [here](https://github.com/Xilinx/finn/blob/e443a5859066a410a63c08dcfec4a90527ca24be/run-docker.sh#L82)

### Other settings and remarks

- In a new terminal outside of the singularity container create a folder under /tmp/finn\_dev\_[username] because you will not have permission to create a folder from inside the container but this is where all the generated files from FINN are saved. As soon as this folder exists, the FINN compiler can save the produced files there

- VitisBuild cannot work in this singularity container because there is a mismatch of the xrt dependencies that are installed on the server and what would be needed inside the singularity container

- If you want to make a VitisBuild:
    - Still execute VitisBuild inside the container because this will generate the necessary files and uses Vivado to synthesize the necessary parts
    - When the build failed, use another terminal outside of the container, go into the vitis\_link\_[...] folder under /tmp/finn\_dev\_[username]
    - Execute the bash script manually bash run\_vitis\_link.sh

- If you have questions, please write to: J.Petri-Koenig@tudelft.nl
