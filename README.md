# Diff_expression_analysis
This repositorium consist description of several pipelines of differential gene expression analysis.

In this project we tests several pipelines of differential gene expression analysis. 
The aim of this project was to compare different methods of differential gene expression analysis and identification of the most suitable for certain types of data. 
For the implementation of this project, several articles were taken and reanalyzed on open sequencing data.
1. Methods:
STAR (v2.7.3a) alignment -> featureCounts (v2.0.1) (getting counts table) -> DESeq2 (v1.26.0) (gene expression analysis in Rstudio).
Also we use fgsea (v1.12.0) and ClusterProfiler (v3.14.3) packages to identify signal pathways. 

For the first pipline was taken article doi:10.3390/genes11091057. 
The object of the study in the article is the cell line of murine myoblasts C2C12: wild type (wt_contr) and with a mutation in the LMNA gene (232_contr). The aim of the study in this article was to assess the effect of the mutation on myogenic differentiation C2C12 (wt_HS and 232_HS).

The first step of all piplines was quality assessment of reads using FastQC programm.
Reads of this article were posted in open access and are available via the link https://trace.ncbi.nlm.nih.gov/Traces/study/?acc=SRP261257&o=acc_s%3Aa. The reads have of high quality and do not need trimming procedure.

2. Пайплайн Кристины Гайновой

3. Пайплайн Ани Квач

The first step of all piplines was quality assessment of reads using FastQC programm.

