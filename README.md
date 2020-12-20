# Diff_expression_analysis

Authors:
- Komarova Margarita
- Gainova Kristina
- Kvach Anna

This repositorium consist description of several pipelines of differential gene expression analysis.

**Aim**

In this project we tests several pipelines of differential gene expression analysis. 
The aim of this project was to compare different methods of differential gene expression analysis and identification of the most suitable for certain types of data. 
For the implementation of this project, several articles were taken and reanalyzed on open sequencing data.

# *Mus Musculus* (Komarova Margarita)
## Methods:
- STAR (v2.7.3a) alignment
- featureCounts (v2.0.1) (getting counts table)
- DESeq2 (v1.26.0) (gene expression analysis in Rstudio)
- also we use fgsea (v1.12.0) and ClusterProfiler (v3.14.3) packages to identify signal pathways. 

For the first pipline was taken article doi:10.3390/genes11091057. 
The object of the study in the article is the cell line of murine myoblasts C2C12: wild type (wt_contr) and with a mutation in the LMNA gene (232_contr). The aim of the study in this article was to assess the effect of the mutation on myogenic differentiation C2C12 (wt_HS and 232_HS).

## The first step of all piplines was quality assessment of reads using FastQC program (https://www.bioinformatics.babraham.ac.uk/projects/fastqc/).

Reads of this article were posted in open access and are available via the link https://trace.ncbi.nlm.nih.gov/Traces/study/?acc=SRP261257&o=acc_s%3Aa. The reads have of high quality and do not need trimming procedure.

## At the next step, the genome was indexed in the STAR program. Example of command for this step:
```
/home/tools/STAR-2.7.3a/bin/Linux_x86_64/STAR --runThreadN 10 --runMode genomeGenerate --genomeDir /mnt4/transciptome_compare/komarova/STAR_genome_index --genomeFastaFiles /mnt4/transciptome_compare/komarova/Mus_musculus.GRCm38.dna_sm.primary_assembly.fa --sjdbGTFfile /mnt4/transciptome_compare/komarova/Mus_musculus.GRCm38.101.gtf --sjdbOverhang 50 
```
Depending on the organism, this process can take 4-8 hours.

## Then you need to align the reads to the genome
```
/home/tools/STAR-2.7.3a/bin/Linux_x86_64/STAR --genomeDir /mnt4/transciptome_compare/komarova/STAR_genome_index/ --runThreadN 10 --readFilesIn /mnt4/transciptome_compare/komarova/SRR11776837.fastq --outFileNamePrefix /mnt4/transciptome_compare/komarova/STAR_alignment/11776837 --outSAMtype BAM SortedByCoordinate --outSAMunmapped Within --outSAMattributes Standard
```
## Counts table
After STAR, counts are obtained in files with .tab resolution and aligned reads in .out.bam. But it is better to run featureCount to calculate counts.
```
/home/tools/subread-2.0.1-source/bin/featureCounts -T 4 -s 0 -a /mnt4/transciptome_compare/komarova/Mus_musculus.GRCm38.101.gtf -o /mnt4/transciptome_compare/komarova/STAR_alignment/featureCount_results/Counts.txt /mnt4/transciptome_compare/komarova/STAR_alignment/*.out.bam
```
Where is:
- -T number of cores
- -s these data are "reverse"ly stranded
- -a path to annotation
- -o output file. The output of this tool is 2 files, a count matrix and a summary file that tabulates how many the reads were “assigned” or counted and the reason they remained “unassigned”.

## "Cleaning" of output file
Unnecessary columns need to be removed.
```
cut -f1,7-18 /mnt4/transciptome_compare/komarova/STAR_alignment/featureCount_results/Counts.txt > /mnt4/transciptome_compare/komarova/STAR_alignment/featureCount_results/Counts.Rmatrix.txt
```
After that we need to add column names and remove unnecessary information.


2. Пайплайн Кристины Гайновой

3. Пайплайн Ани Квач

The first step of all piplines was quality assessment of reads using FastQC programm.

