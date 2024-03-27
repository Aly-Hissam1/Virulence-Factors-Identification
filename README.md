# Virulence-Factors-Identification

Hello and thank you for visiting my pipeline for virulence factor identification. This readme file provides a step-by-step guide to reproduce the work conducted in the study. 

At first you should download some bacterial comlpete genomes to extract the virulence factors from them.

**Pangenome Analysis**

•	Start by creating a Conda environment and downloading the required tools "Prokka & Roary".

•	Utilize Prokka to annotate all complete genomes. Move all gff files into another folder to be used in the second step.

•	Excute Roary to construct your pangenome. 

•	Extract the names of the core genes from the presence-absence file. These genes should be present in at least 99% of the analyzed genomes.

•	Use the extracted gene names to retrieve their corresponding sequences from the complete set of genes fasta file "Pan_genome_reference.fa".


**Virulence Factors Identification**

•	Import the core genes fasta files into the Blast2GO software.

•	Preprocess the genes by running local Blastx against the non-redundant UniProtKB/Swiss-Prot database. Set the parameters as follows: E-value (1.0E-3), number of hits (20), word size (3), and high-scoring pair (HSP) cutoff (33).

•	Exclude genes with no blast hits, genes with a sim mean lower than 65%, and genes with no "bacterial" hits based on the obtained Blast results.

•	Conduct GO mapping to assign functional gene ontology terms for the BLAST hits using curated gene ontology annotated proteins by Goa version 2022.08.

•	Annotate protein BLAST hits by assigning each GO term to its corresponding gene in the fasta file.

•	Perform Gene Ontology enrichment analysis using Fisher’s Exact Test. Compare the output genes' codes against the genes' codes of the reference bacteria. Set the parameters as follows: filter value (0.05), P-value filter mode, annotation type (GO IDs), and the identified GO categories (biological processes, molecular functions, and cellular components).


I am open for any comments...
