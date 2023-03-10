# RNA-seq-Differential-Expression-Analysis

**Author**: Migle Apanaviciute

*Date: 28/12/2022*

**About Data**:<br/>
RNA-seq data from Human HGSC (high grade serous ovarian cancer) cell line - OVCAR4.<br/>
Libraries were sequenced to a target coverage of 50 × on Illumina's HiSeq 4000 (2 x 75 bp paired end reads).<br/> 
Data split into 2 groups (3 samples each): carboplatin-resistant vs carboplatin-sensitive.<br/>
In total there were 12 raw FASTQ files (2 for each sample). 

**Objective**:<br/>
Investigate the changes in gene expression and effects on Gene Ontology Biological Pathways (GOBP) in carboplatin-resistant samples compared to carboplatin-sensitive.

**Bioinformatics Pipeline**:<br/>

*Bash:*<br/>
Running QC on FASTQ files.<br/>
Adapter trimming using trim_galore.<br/>
Mapping to the human genome (hg38, Genome Reference Consortium GRCh38) using STAR.<br/>
Quantification of gene abundance using rsem.<br/>

*R:*<br/>
Generating matrix of the rsem estimated_counts.<br/>
Filtering out low count genes (allowing 10 counts in at least 3 samples).<br/>
Differential Expression Analysis using DESeq2.<br/>
Annotating using Ensembl annotation.<br/>
Performing Pre-Ranked Gene Set Enrichment Analysis (GSEA Pre-Ranked) using Molecular Signatures Database (c5.go.bp.v7.4.symbols.gmt).<br/>
Performing pathway analysis using online tool Reactome.

**Results:**<br/>
Gene Ontology Biological Pathways (GOBP) related to the tumor micro-environment, particularly the extracellular matrix, were enriched in carboplatin-resistant cells

**Data sets provided**:<br/>

*Array jobs in bash (pipeline in this order):*
QC_job.sh<br/>
trim_job.sh<br/>
STAR_job.sh<br/>
bam_job.sh<br/>

*Samples IDs:*<br/>
sample_IDs.csv

*Raw gene counts output files from rsem analysis:*<br/>
WTCHG_626197_201106_.genes.results<br/>
WTCHG_626197_289105_.genes.results<br/>
WTCHG_626197_290117_.genes.results<br/>
WTCHG_626197_291129_.genes.results<br/>
WTCHG_626197_295177_.genes.results<br/>
WTCHG_626197_296189_.genes.results<br/>

*R code for DE analysis:*<br/>
RNA-seq project.Rmd<br/>
RNA-seq project.ipynb<br/>

*Pathway analysis with Reactome:*<br/>
reactome_result.csv<br/>
