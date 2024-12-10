# cr-run-snakemake

```cr-run-snakemake``` is a Snakemake pipeline designed to process raw ATAC-seq and multiome data from public datasets, handling everything from data download to generating processed outputs compatible with the Signac package.

## Installation & Running 
### Installation 
```cr-run-snakemake``` can be installed by cloning the Github repository
```
# Clone this repository into your local machine
git clone https://github.com/??

# Change into the ?? directory
cd ??
```

After cloning the GitHub repo, you can install snakemake and the other dependencies using [mamba](https://mamba.readthedocs.io/en/latest/installation/mamba-installation.html) by using the code below:
```
# Make sure mamba is already installed
mamba env create -f environment.yaml

# Activate cr-run-snakemake mamba environment
mamba activate run_cellranger_env
```

### Running
#### On local computer
```
snakemake --cores all --keep-incomplete --resources load=100
```
<div style="color: red;">
  <strong>Resources flag must be added when running Snakemake pipeline to ensure proper load management; modify according to computing power.</strong>
</div>
[For reference, 1 run_cr requires a load of 50; 256GB of ram allows for ~ 2 simultaneous runs of CellRanger.]

#### On HPC

xxx.batch script must be present

*Example of xxx.sbatch format to run pipeline:*
```
#!/bin/bash

#SBATCH -t 72:00:00           # Maximum time to run the whole pipeline, will stop after the time exceed
#SBATCH -N 1
#SBATCH --ntasks-per-node 60
#SBATCH --cpus-per-task 1
#SBATCH --mem 128G            # Max RAM memory needed
#SBATCH -J CR_pipeline        # Prefix for .out and .err file
#SBATCH --output=%x-%j.out    # Show the output produced
#SBATCH --error=%x-%j.err     # Show the error output produced
#SBATCH -p cpu

snakemake --cores all --keep-incomplete --resources load=100
```

After preparing the sbatch file, submit the job to HPC:
```
sbatch xxx.sbatch
```
After running the code above, job_id will be given and you can check the jon status (```RUNNING```, ```PENDING```, ```FAILED```) by:
```
sacct -j [job id]
```



