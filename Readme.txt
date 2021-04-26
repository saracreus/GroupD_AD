·DATABASE SEARCH AND DATABASE SELECTION
The sequences of human proteins were collected in FASTA format from NCBI. When there were more than 1 isoform, only 1 of them was selected. In order to obtain the sequences in the other species, the BLAST tool was used. The BLAST was run against the UniprotKB/Swissprot database because of the non-necessity of getting sequences with known structure. All the resulting sequences were downloaded in FASTA format. The human protein, the one that was the query sequence, was added into the file. 



·CLUSTERING
In order to cluster the sequences among all the species, CD-HIT was used in each protein ("CD-HIT Official Website", 2021). CD-HIT is a program able to cluster similar proteins that meet a defined similarity threshold. The first sequence is automatically classified as the first cluster representative sequence. Then each query sequence of the remaining sequences is compared to the representative sequences found before it, and is classified as redundant or representative based on whether it is similar to one of the existing representative sequences. For this reason, the species with the highest percentage of identity do not appear in the following steps. The determined threshold in this study was of 0,65. The following code is needed so as to run CD-HIT from terminal.
 cd-hit -i input/nombreprot.fasta -o output/nombreprotclusters.fasta -c 0.65 
Once the code has been run, two files containing the sequences in each cluster are obtained.  To make sure the centroid sequence is the sequence of the protein of interest a BioPython code using SeqIO was applied. 

·MSA 
A multiple sequence alignment of the centroid sequence of each cluster was performed for every protein. To do so, a command-line MAFFT program was employed. The following code was needed to perform it: 
mafft --auto output/my_clusters.fasta > output/2HDXMT_msa.fasta 
The output of that program is the MSA file. As a means to visualize the MSA and the conserved regions, chimera was used. ("Download UCSF Chimera", 2021). 

·PHYLOGENETIC TREE
A phylogenetic tree from the previous MSA was done for each protein. To do so, a program called MEGA was used. The MSA file was uploaded into the program and a maximum likelihood method was applied. The tree was edited from the same program and downloaded. 

·DISTANCE MATRIX 
A distance matrix was performed in order to analyze the difference between the species. The MEGA program was used to calculate it. 
