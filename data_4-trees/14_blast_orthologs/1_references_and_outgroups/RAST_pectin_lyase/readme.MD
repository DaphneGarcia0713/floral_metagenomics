This folder is made Dec 11, 2025. this aligns with benchling "Metagenomic ortholog pectin lyase tree Vivi's 2021 data" notebook

I am trying to make a phylogenetic tree for metagenomic pectin-lyase orthologs found by a BLAST search, with references from the RAST-annotated pectin lyase that Vivi used for her paper. 

For this, I took all orthologs from Vivi's pectin lyase tree from her paper, and I will align it with MAFFT here. Then, I will create a tree to confirm that I have the same clades, since Vivi's tree didn't have which specific strains/orthologs from which strain are in which clade. 

`cd /local/workdir/Daphne/Floral_metagenomics/data_4-trees`

To get all of the orthologs into one .fasta file, I ran:
`cd  14_blast_orthologs/1_references_and_outgroups/RAST_pectin_lyase`
`cat ./*.fasta >> all_PL_ref_fastas.fasta`
Then, I went into all_PL_ref_fastas.fasta and manually made sure the strain-ortholog name was the header for every fasta block, so that it appears on iTOL tree

PLUS: I created a new file called `all_PL_ref_PLUS_outgroups.fasta` manually added the pectobacterium, odoriferum, pseudomonas outgroups, and also A. apis referene, to include all the members of the tree in Vivi's paper

For MAFFT I ran:

`export PATH=/programs/mafft/bin:$PATH`
`/programs/mafft/bin/mafft --auto --nuc --thread 10 all_PL_ref_PLUS_outgroups.fasta > aligned_orthologs_MAFFT_pectin_lyase.aln`

This took 3 seconds, used strategy L-INS-i (Probably most accurate, very slow)

For IQ tree I ran:

`/programs/iqtree-2.2.2.6-Linux/bin/iqtree2 -s aligned_orthologs_MAFFT_pectin_lyase.aln -m MFP --prefix pectin_lyase_tree -B 1000`

* -m MFP: modelfinder plus
* -B 1000: boostrap

This took 15 seconds