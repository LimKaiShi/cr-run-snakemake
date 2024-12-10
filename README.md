# cr-run-snakemake

```cr-run-snakemake``` is a Snakemake pipeline designed to process raw ATAC-seq and multiome data from public datasets, handling everything from data download to generating processed outputs compatible with the Signac package.

## Installation & Running 

cr-run-snakemake can be installed by cloning the Github repository
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

