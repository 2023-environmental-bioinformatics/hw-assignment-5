# HW3 binning


For this assignement you will going to use [Metabat2](https://peerj.com/articles/7359/) to reconstruct genomes out of the metagenomes. 
- First, you are going to co-assemble the three metagenomes you have used for your previous assignment, ERR598970, ERR598972 and ERR599021 using `megahit`. Make a directory called `scripts` on your repo and upload your sbatch script (*name the script `megahit.qsub`*).

- Before using [Metabat2](https://bitbucket.org/berkeleylab/metabat/src/master/), you will have to map the reads back to the assembly using [`bwa`](http://bio-bwa.sourceforge.net) mem. Sort the files using `samtools`. Use Metabat2 to reconstruct bins (*Note: adjust the parameters "Minimum size of a contig for binning" to 1500 and the "maximum number of edges per node" to 100*). Upload the sbatch script that contains all the commands for mapping, sorting and binning on your `script` folder.

- Use [CheckM](https://github.com/Ecogenomics/CheckM/wiki) to estimate the completeness and the contamination of the bins (*Hint: use the checkm lineage_wf workflow and export results as a table format. Note: set `--pplacer_threads` to 2*). Make a directory called `tables` on your repo and upload the table (*name the table `checkm_report.txt`*). Upload the sbatch script that contains all the commands for mapping, sorting and binning on your `script` folder.
>How many genomes are considered high quality and how many medium quality according to the community standards proposed by [Bowers et al. 2017](https://www.nature.com/articles/nbt.3893)? (*Note: from the completeness and contanination estimates you might not be able to fully answer this question. You can report how many of the genomes can be **putatively** characterized as high quality. After functional annotation, you will be able to fully answer the question).

- **For the rest of tasks you will only work with the medium and high quality bins (M/H Q).** Make a folder called `qual_bins` and upload all M/H Q genomes.
Use quast to calculate the assembly statistics of each bin, and to estimate the coverage of each bin in the metagenomes (ERR598970, ERR598972 and ERR599021). Upload the sbatch script (`quast.qsub`) and the quast report table `report.tsv` in the directories `scripts` and `tables`, respectively.  

- Use [GTDB-tk](https://ecogenomics.github.io/GTDBTk/index.html) to assign taxonomy to the bins (*Note: during the installation of GTDB-tk, please do NOT download the GTDB. Modify the `gtdbtk.sh`file that is inside your gtdb environment `etc/conda/activate.d/` to modify the database path. Use `/vortexfs1/omics/env-bio/collaboration/databases/release202`. Due to the size of the GTDB-tk, you will be reaching the memomy limitations of the compute nodes. Use the flag `--scratch_dir` to overcome this issue. Also reduce pplacer threads to 1*). Upload the summary tables on your `tables` directory and the `gtdb.sh` script on the script folder.
> How many bacterial and how many archaeal M/H Q genomes did you recover? Which phylum was the most abundant?

- Use [prokka](https://github.com/tseemann/prokka) to functionally annotate the bins. Upload the script. Upload all the tsv tables to the repo.
> How many bins contain at least one rRNA genes? How many contain all rRNA genes (5S rRNA, 16S rRNA and 23S rRNA)? Recover all 16S rRNA gene sequences, add them to a file called `qual_bins_16S.fasta`. Make a directory called `sequences` and upload the file.






> For all runs use sbatch requesting 36 threads and 180gb of memory.

> For all required sortware, use conda to install.

> You can inquire the path to one of your conda environments by typing `conda info --envs`


