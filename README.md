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
* Dependencies: samtools-0.1.19_gnu446, bowtie2, boost, tophat
* Execution: `qsub run_tophat.qsub`
* Aligns the reads to the mouse genome reference called mm9
