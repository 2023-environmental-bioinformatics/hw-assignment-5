# HW3 binning




For this assignement you will going to use [Metabat2](https://peerj.com/articles/7359/) to reconstruct genomes out of the metagenomes. First, you are going to co-assemble the three metagenomes you have used for your previous assignment, ERR598970, ERR598972 and ERR599021 using `megahit`.

Before using [Metabat2](https://bitbucket.org/berkeleylab/metabat/src/master/), you will have to map the reads back to the assembly using `bwa`. Sort the files using `samtools`.

Use [CheckM](https://github.com/Ecogenomics/CheckM/wiki) to estimate the completeness and the contamination of the bins (*Hint: use the checkm lineage_wf workflow and export results as a table format).

`envs/gtdbtk_class/etc/conda/activate.d/gtdbtk.sh`
`/vortexfs1/omics/env-bio/collaboration/databases/release202`





> For all runs use sbatch requesting 36 threads and 180gb of memory

> For all software mentioned below, use conda to install


