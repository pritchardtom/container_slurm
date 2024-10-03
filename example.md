# Running Apptainer Container

Process can be achieved multiple ways.  This method involves using two scripts:
1. Slurm submission script.
2. A Bash script with instructions you wish to execute in the container.

## Slurm Submission Script

```bash
#!/bin/bash --login

#SBATCH --job-name=kathrin_example
#SBATCH --output=out.out.%J
#SBATCH --error=err.err.%J
#SBATCH --time=1-00:00              # format in days-hours:minutes
#SBATCH --nodes=1
#SBATCH --ntasks=40
#SBATCH --mem=10G
#SBATCH --account=scwXXXX

module purge
module load slurm
module load apptainer/1.0.3

# execute every command in the instructions.sh file inside the container:
apptainer exec container_name.sif /bin/bash instructions.sh
```

## Instructions Script

```bash
#!/bin/bash

python3 /path/to/python/script.py
mb run

```
