
Download a pybioclip container.
```
apptainer pull oras://ghcr.io/imageomics/pybioclip-sif:1.0.0
```
The above command will create a `pybioclip_1.0.0.sif` container image file.


CPU based prediction:
```
./pybioclip_1.0.0.sif bioclip predict Ursus.jpeg
```

GPU based prediction:
```
apptainer exec -nv ./pybioclip_1.0.0.sif bioclip predict --device cuda Ursus.jpeg
```

SLURM sbatch script:
`bioclip.sh`
```
#!/bin/bash 
#SBATCH --job-name SIFPyBioclip
#SBATCH --nodes=1 
#SBATCH --time=00:10:00 
#SBATCH --gpus-per-node=1 
apptainer exec --nv ./pybioclip_1.0.0.sif bioclip predict --device cuda $*
```

```
sbatch --account <SLURMACCT> bioclip.sh Ursus-arctos.jpeg Other.jpeg
```
