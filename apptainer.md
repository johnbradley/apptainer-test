# Using the Apptainer/Singularity pybioclip Container
[Apptainer/Singularity](https://apptainer.org/docs/user/main/index.html) images for pybioclip are provided at [ghcr.io/Imageomics/pybioclip-sif registry](https://github.com/Imageomics/pybioclip/pkgs/container/pybioclip-sif).
NOTE: It is also possible to download the pybioclip docker container and convert that into a singularity container, but that process can take quite a while.

## Usage

## Download a pybioclip container

```
apptainer pull oras://ghcr.io/imageomics/pybioclip-sif:1.0.0
```
The above command will create a `pybioclip_1.0.0.sif` container image file.

## Create predictions using a CPU
```
./pybioclip_1.0.0.sif bioclip predict Ursus.jpeg
```

## Create predictions using a GPU
```
apptainer exec -nv ./pybioclip_1.0.0.sif bioclip predict --device cuda Ursus.jpeg
```


## Create predictions using a GPU via a Slurm Job
Create a Slurm sbatch script named `bioclip.sh` with the following content:
```
#!/bin/bash 
#SBATCH --job-name SIFPyBioclip
#SBATCH --nodes=1 
#SBATCH --time=00:10:00 
#SBATCH --gpus-per-node=1 
apptainer exec --nv ./pybioclip_1.0.0.sif bioclip predict --device cuda $*
```
Run the slurm job:
```
sbatch --account <SLURMACCT> bioclip.sh Ursus-arctos.jpeg Other.jpeg
```
