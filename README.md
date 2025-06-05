
# Floral Metagenomic Analysis Workflow

## Daphne Garcia, Hendry Lab, Cornell, 5/27/2025

This workflow has been written to assemble and process the metagenomic data from floral, crop, and pollen provisions collected by Vivianna Sanchez for her dissertation. 

Proposed steps in the analysis pipeline: 
1.  FastQC quality analysis
2.  Trimmomatic adapter trimming
3.  Bowtie2 read filtering
4.  MetaSpades assembly
5.  CheckM host contamination
6.  Phyloflash taxonomy composition