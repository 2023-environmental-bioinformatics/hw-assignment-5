# HW5 binning

## Co-assembly and binning
For this assignement you will going to use [Metabat2](https://peerj.com/articles/7359/) to reconstruct genomes out of the metagenomes. 
- First, you are going to **co-assemble** the three metagenomes you have used for your previous assignment, ERR598970, ERR598972 and ERR599021 using `megahit`. Make a directory called `scripts` on your repo and upload your sbatch script (*name the script `megahit.qsub`*).

- Before using [Metabat2](https://bitbucket.org/berkeleylab/metabat/src/master/), you will have to map the reads back to the assembly using [`bwa mem`](http://bio-bwa.sourceforge.net). Sort the files using `samtools`. Use Metabat2 to reconstruct bins (*Note: adjust the parameters "Minimum size of a contig for binning" to 1500 and the "maximum number of edges per node" to 100*). Upload the sbatch script that contains all the commands for mapping, sorting and binning on your `script` folder (*named `binning.qsub`*).

## Quality assessment
- Use [CheckM](https://github.com/Ecogenomics/CheckM/wiki) to estimate the completeness and the contamination of the bins (*Hint: use the checkm lineage_wf workflow and export results as a table format. Note: set `--pplacer_threads` to 2*). Make a directory called `tables` on your repo and upload the table (*name the table `checkm_report.txt`*). Upload the sbatch script that contains all the command on your `script` folder (`checkm.qsub`).
>How many genomes are considered high quality and how many medium quality according to the community standards proposed by [Bowers et al. 2017](https://www.nature.com/articles/nbt.3893)? (*Note: from the completeness and contanination estimates you might not be able to fully answer this question. You can report how many of the genomes can be **putatively** characterized as high quality. After functional annotation, you will be able to fully answer the question).

- **For the rest of tasks you will only work with the medium and high quality bins (M/H Q).** Make a folder called `qual_bins` and upload all M/H Q genomes.
Use quast to calculate the assembly statistics of each bin. Upload the sbatch script (`quast.qsub`) and the quast report table `report.tsv` in the directories `scripts` and `tables`, respectively.  

## Taxonomic annotation
Install [GTDB-tk](https://ecogenomics.github.io/GTDBTk/index.html) **version 2.1.1** using mamba to assign taxonomy to the bins you created. See detailed instructions [here](https://ecogenomics.github.io/GTDBTk/installing/bioconda.html). During the installation of GTDB-tk, please **do NOT download the GTDB database**. After you activate your mamba gtdbtk environment use `conda env config vars set GTDBTK_DATA_PATH="/proj/omics/env-bio/collaboration/databases/gtdbtk-2.1.1/db/"` to set up your database path. You also need to execute (inside your gtdbtk-2.1.1 environment) `install -c conda-forge numpy=1.23.1`.

Due to the size of the GTDB-tk, you will be reaching the memomy limitations of the compute nodes. To address this issue, eeduce pplacer threads to 2 (check the help menu to figure out how). Upload the summary tables on your `tables` directory and the `gtdb.qsub` script on the `script` folder.

> How many of the bins belong to Archaea and how many to Bacteria? Which phylum is the most abundant?

## Functional annotation
- Use [prokka](https://github.com/tseemann/prokka) to functionally annotate the bins. Upload the script (`prokka.qsub`). Upload all the tsv tables to the repo.
> How many bins contain at least one rRNA genes? How many contain all rRNA genes (5S rRNA, 16S rRNA and 23S rRNA)? Recover all 16S rRNA gene sequences, add them to a file called `qual_bins_16S.fasta`. Make a directory called `sequences` and upload the file. Report the commands you used to search for the presence of the rRNA genes and recover the sequences.

> Are there bins containing the dissimilatory-type of sulfite reductase? If yes, report their names and the Class they belong. Do they have a species assignment?




______________________________________________________________________________________________________________________________________________________________
## For successful completion of your homework, your Github repo should contain:
- an upadated README file with answers to the questions
- a directory called `tables` that contains the tables: checkm_report.txt, report.tsv, gtdb summary ,  prokka *tsv 
- a directory called `sequences` that contains the file: qual_bins_16S.fasta
- a directory called `scripts` that contains the sbatch scripts: megahit.qsub, binning.qsub, quast.qsub, checkm.qsub, gtdb.qsub, prokka.qsub


Do you hesitate to contact us if you have any questions!

______________________________________________________________________________________________________________________________________________________________



> For all runs use sbatch requesting 36 threads and 180gb of memory.

> For all required sortware, use conda to install.

> You can inquire the path to one of your conda environments by typing `conda info --envs`

> After the completion of this homework, please delete any large files (sra, fastq etc).


