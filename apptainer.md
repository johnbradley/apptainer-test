
```
#!/bin/bash 
#SBATCH --account PAS2136
#SBATCH --job-name SIFPyBioclip
#SBATCH --nodes=1 
#SBATCH --time=00:10:00 
#SBATCH --gpus-per-node=1 
apptainer exec --nv ./pybioclip2.sif bioclip predict --device cuda Ursus-arctos.jpeg
```
