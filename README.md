# HW3 binning




For this assignement you will going to use [Metabat2](https://peerj.com/articles/7359/) to reconstruct genomes out of the metagenomes. First, you are going to co-assemble the three metagenomes you have used for your previous assignment, ERR598970, ERR598972 and ERR599021 using `megahit`. Make a directory called `scripts` on your repo and upload your sbatch script (name the script `megahit.qsub`.

Before using [Metabat2](https://bitbucket.org/berkeleylab/metabat/src/master/), you will have to map the reads back to the assembly using `bwa`. Sort the files using `samtools`. Use Metabat2 to reconstruct bins (*Note: for the needs of this class, you are working with small metagenomes that produced a small assembly
runMetaBat.sh -m 1500 --maxEdges 100 final.contigs.fa ERR598970.bam ERR598972.bam ERR599021.bam

Use [CheckM](https://github.com/Ecogenomics/CheckM/wiki) to estimate the completeness and the contamination of the bins (*Hint: use the checkm lineage_wf workflow and export results as a table format).

`envs/gtdbtk_class/etc/conda/activate.d/gtdbtk.sh`
`/vortexfs1/omics/env-bio/collaboration/databases/release202`





> For all runs use sbatch requesting 36 threads and 180gb of memory

> For all software mentioned below, use conda to install


