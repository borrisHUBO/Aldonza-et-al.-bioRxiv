# Aldonza-et-al.-Nature-Communications-submission

# Analysis source codes

1. GDSC vs FUT methylation or secretome Spearman analysis
'Spearman/GDSC vs FUT methylation or Secretome Spearman analysis.ipynb' is a ipython script for spearman correlation anaylsis, which done by Python v3.7.6. For those wanting to try it out, the best place to start is the ipython notebook such as Jupyter. All datasets used for this analysis are in Spearman/data directory.

Methylation analysis with FUT genes
1. Methylation datasets contain methylation fraction (1 kb upstream TSS) per cancer type.
2. GDSC drug sensitivity datasets contain drug sensitivity. (cancer types vs each drug)

#Preprocessing
For Methylation datasets
No preprocessing was conducted
For exact n, please find the number of cell lines in the original dataset.

For GDSC datasets
1. Cancer types from two datasets are different (Methylation: Primary disease; GDSC: TCGA classification). TCGA classification was converted to primary disease manually
2. Drug types were not assigned. Three drug type groups were made (Total, Targeted, Cytotoxic).
3. Missing values on GDSC datasets were removed. 0 was regarded as missing value.
4. n = 169 for Total, n = 33 for Targeted, n = 10 for Cytotoxic.


Secretome analysis
1. Core secretome genes dataset contain log2 gene expression per cancer type.
2. GDSC drug sensitivity datasets contain drug sensitivity. (cancer types vs each drug)

#Preprocessing
For both datasets
Cancer type lists of two datasets are different. I used only overlapped cancer types for analysis

For Core secretome datasets
1. Missing values on FC_2 were removed. 0 was regarded as missing value.
2. From the Core secretome dataset, we found three subsets (glycosylation, N-linked or O-linked)
2.1. Gene lists were obtained from geneontology.org. First, find GO term, and search on that website. After then, use organism filter (Homo sapiens).
2.2. In that website, the reported genes are n = 193 for O-linked, n = 81 for N-linked, n = 264 for Protein glycosylation
3. Overlapped genes used in the study: n = 1810 for whole, n = 18 for O-linked n =1 for N-linked, n = 19 for Protein glycosylation
4. p-values were calculated by two-sided Student's t-test
4.1. details: two-sided, non-equal variance, nan_policy: omit. Details are on https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.ttest_ind.html.

For GDSC datasets
1. Drug types were not assigned. Three drug type groups were made (Total, Targeted, Cytotoxic)
2. Missing values on GDSC datasets were removed. 0 was regarded as missing value.
3. n = 169 for Total, n = 33 for Targeted, n = 10 for Cytotoxic.
______

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

______

3. Analysis of GDSC and CCLE datasets
Python scripts used for correlation or association analyses in Figure 1, Supplementary Figures, Figure 3.

