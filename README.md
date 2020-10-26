# Aldonza-et-al.-Nature-Communications-submission

# Analysis source codes

1. GDSC vs FUT methylation or secretome Spearman analysis
'Spearman/GDSC vs FUT methylation or Secretome Spearman analysis.ipynb' is a ipython script for spearman correlation anaylsis, which done by Python v3.7.6. For those wanting to try it out, the best place to start is the ipython notebook such as Jupyter. All datasets used for this analysis are in Spearman/data directory.

2. RNA-seq analysis
RNA-seq libraries used in this study are deposited in GEO***. Raw 2x101 paired-end sequencing reads were mapped to the human genome (build hg38) with HISAT2 v2.1.0 using default parameters except with the option "--dta". Stringtie v.2.0.6 was used to quantify the expression of genes and transcripts by employing transcriptome information from GENCODE v27. 
Ballgown package was used to perform differential gene expression analysis generating FPKM for each gene. 'RNA-seq/DEG.Rmd' is a R notebook for DEG analysis using ballgown library.
For hierarchical clustering, pheatmap library in R was used. FPKM values of low-variance-filtered genes were analyzed using default options except “scale='row',clustering_distance_rows='correlation', main='genes'” options. Heatmap colors indicate z-score in each row. 'RNAseq/HierarchicalClustering.Rmd' is a R notebook for hierarchical clustering analysis using pheatmap library.

Get help for installation of those softwares/libraries in these sites:
HISAT2: http://daehwankimlab.github.io/hisat2/
Stringtie: https://ccb.jhu.edu/software/stringtie/
Ballgown: https://bioconductor.org/packages/release/bioc/html/ballgown.html

Example codes are:
hisat2 -p 8 --dta -x /directory/for/index -1 read_1.fastq -2 read_2.fastq -S output.sam
stringtie -e -B -p 8 -G /directory/for/GTF -o output/output.gtf sample.bam

3. Analysis of GDSC and CCLE datasets
Python scripts used for correlation or association analyses in Figure 1, Supplementary Figures, Figure 3.

