
apptainer pull oras://ghcr.io/johnbradley/apptainer-test-sif:1.0.0
./pybioclip_1.0.0.sif bioclip predict Ursus.jpeg

apptainer exec -nv ./pybioclip_1.0.0.sif bioclip predict --device cuda Ursus.jpeg


`bioclip.sh`
```
#!/bin/bash 
#SBATCH --job-name SIFPyBioclip
#SBATCH --nodes=1 
#SBATCH --time=00:10:00 
#SBATCH --gpus-per-node=1 
apptainer exec --nv ./pybioclip_1.0.0.sif bioclip predict --device cuda $*
```

sbatch --account <SLURMACCT> bioclip.sh Ursus-arctos.jpeg Other.jpeg
