# Project Description
This project focuses on reproducing the results from O’Meara et al. The objectives of the study were to determine if myocytes revert the transcriptional phenotype to a less differentiated state during regeneration and to systematically interrogate the transcriptional data to identify and validate potential regulators of this process.

In reproducing this study we downloaded, QC, processed, and analyzed sequencing data that was generated to better understand how neonatal mice are able to regenerate their heart tissue but lose this ability later in development.

O’Meara et al. Transcriptional Reversion of Cardiac Myocyte Fate During Mammalian Cardiac Regeneration. Circ Res. Feb 2015. PMID: 25477501

# Contributors
* Data Curator: Andrew Gjelsteen (@agjeleste)
* Programmer: Elysha Sameth (@esameth)
* Analyst: Lindsay Wang (@LindsayW007)
* Biologist: Monil Gandhi (@gandhimonil9823)

# Repository Contents
## Programmer
### run_tophat.qsub
* Dependencies: python2, samtools-0.1.19, bowtie2, boost, tophat
* Execution: `qsub run_tophat.qsub`
* Outputs: `P0_1_tophat/accepted_hits.bam`
* Aligns the reads to the mouse genome reference called mm9
* TopHat parameters are `-r 200`, `-G`, `--segment-length=20`, `--segment-mismatches=1`, `--no-novel-juncs`

## run_rseqc.qsub
* Dependencies: python3, samtools, rseqc
* Execution: `qsub run_rseqc.qsub`
* Outputs: quality control metric in `bam_stat.txt`, plots of mRNA distribution and gene coverage
* `genebody_coverage.py`: Calculate the RNA-seq reads coverage over gene body
* `inner_distance.py`: Calculate the inner distance (insert size)  of RNA-seq fragments
* `bam_stat.py`: Summarizing mapping statistics of a BAM or SAM file 

## run_cufflinks.qsub
* Dependencies: cufflinks
* Execution: `qsub run_cufflinks.qsub` 
* Inputs: `P0_1_tophat/accepted_hits.bam`
* Outputs: `P0_1_cufflinks/genes.fpkm_tracking`
* Counts how reads map to genomic regions defined by an annotation
* Cufflinks parameters are `--compatible-hits-norm` 

## Analyst
### Analyst.R
* Dependencies: R
* Inputs: `gene_exp.diff`
* Outputs: `top_10_genes.csv`: Top 10 genes with the lowest q value
* `Log2 Fold Change for All Genes`: Histogram of log2 fold-change of all genes 
* `Log2 Fold Change for Significant Genes`: Histogram of log2 fold-change of significant genes 
* `up_reg_genes.csv`: Up regulated genes
* `down_reg_genes.csv`: Down regulated genes

### Ontology.R
* Dependencies: R
* Inputs: GO output .txt files
* Outputs: `ontology_table.csv`: Summarizes the GO enrichment clusters

### GO_barplot.R
* Dependencies: R
* Outputs: `up.png`: Summarizes the top 5 GO enrichment clusters for up-regulated genes
* `up.png`: Summarizes the top 5 GO enrichment clusters for down-regulated genes



