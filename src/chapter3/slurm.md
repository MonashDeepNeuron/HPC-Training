# Job batching & SLURM

```bash
#!/bin/bash

#SBATCH --ntasks=1
#SBATCH --mem=1MB
#SBATCH --time=0-00:01:00
#SBATCH --mail-user=jmar0066@student.monash.edu
#SBATCH --mail-type=BEGIN,END,FAIL

echo "Hello World"
```