---
{"dg-publish":true,"permalink":"/vasp-on-cluster/running-vasp-on-gpu-machine/","dgHomeLink":true,"dgPassFrontmatter":false}
---

# Running VASP through slurm on gpu machine
This is a typical job script for running a vasp simulation in two GPUs. Important to load nvhpc. 

```bash
#!/bin/bash
#SBATCH --job-name=VASP
#SBATCH --partition=normal
#SBATCH --ntasks=2
#SBATCH --cpus-per-task=2
#SBATCH --gres=gpu:2

module load nvhpc/22.9
mpirun -np 2 vasp_std
```


