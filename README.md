# nMAGMA
nMAGMA is an approach to intergrate Hi-C, eQTL and gene networks inferred from WGCNA into default physical-location-based MGAMA annotation.
## List of files
* __RE_to_genes.zip__: *3DIV_DLPFC_RE_to_genes.txt,3DIV_Hippocampus_RE_to_genes.txt,3DIV_Liver_RE_to_genes.txt,3DIV_Small_Bowell_RE_to_genes.txt.* This file contains RE-gene regulatory relationships obtained from Hi-C.
* __Signifgenepairs.zip__: *Cortex_signifgenepairs.txt,Hippocampus_signifgenepairs.txt,Liver_signifgenepairs.txt,Small_Bowel_signifgenepairs.txt.* This file contains significant gene pairs with TOM >= 0.15.
* __Hi-C_annot__: *DLPFC_assig_throu_re_dataset1.genes.annot, DLPFC_assig_throu_re_dataset2.genes.annot, Hippocampus_assig_throu_re_dataset1.genes.annot, Hippocampus_assig_throu_re_dataset2.genes.annot, Liver_assig_throu_re_dataset1.genes.annot, Liver_assig_throu_re_dataset2.genes.annot, Small_Bowel_assig_throu_re_dataset1.genes.annot, Small_Bowel_assig_throu_re_dataset2.genes.annot.* This folder contains .genes.annot files of two EUR GWAS summary datasets we used through Hi-C. Snps were first mapped to REs and then mapped to genes via the RE-gene relationships.
* __eqtl_annot__: *Cortex_eqtl.genes.annot, Hippocampus_eqtl.genes.annot, Liver_eqtl.genes.annot, Small_Bowel_eqtl.genes.annot.* This folder contains .genes.annot files through eQTL. Snps were directly mapped to their eGenes.
* __TOM_annot__: *Cortex_TOM.zip, Hippocampus_TOM.zip, Liver_TOM.zip, Small_Bowel_TOM.zip.* This folder contains .genes.annot files through assigning eQTLs to genes highly connected with its target gene (TOM >= 0.15).
* __Supplementary Table for results of significant gene associations.xlsx__: This supplementary table contains significant genes (p-values below 0.05 under Bonferroni correction) detected by MAGMA, H-MAGMA and nMAGMA from two SCZ GWAS summary statistics described in the main script and the manuscript of nMAGMA, which have been ordered by the significance of p-values of genes for each method.
## Codes
* __Main_script.txt__:This is a tutorial on how to conduct nMAGMA step-by-step.
* __Calcu_TOM_extract_signifgenepairs.R__: This script can calaulate a TOM matrix using R package 'WGCNA' and extract siginificant gene regulatory pairs with TOM >=0.15. Your can also define a threshold you prefer.
* __Merge_annot_files.R__: Your can repeatly use this script to merge several .genes.annot files in order to expand the SNP-gene annotation. The final annotate file for input in MAGMA can be derived by merging the original MAGMA annotation file (you need to create it by MGAMA yourself, it's very feasible) and all the three kind of .annot files we provide above(Hi-C_annot, eqtl_annot, TOM_annot). Then you can get the final nMAGMA annotation file (we only included protein-coding genes in our paper) and do the downstream analysis like gene and gene-set analysis.
* __Extended LDSC to GSA.R__: This is the LD Score regression extended to gene-set analysis. First a gene-geneset matrix is created and then the LD score and chisq statistics of each gene set are calculated. Your can detect from the regression intercept that whether the inflation of statistics in gene-set analysis are caused by confounding factors or the complex pathogenesis of the disease. 
## Reference
1. Yang A, chen J, Zhao X-M. nMAGMA: a network enhanced method for inferring risk genes from GWAS summary statistics and its application to schizophrenia, bioRxiv 2020:2020.2008.2015.250282.
2. De Leeuw C A , Mooij J M , Heskes T , et al. MAGMA: generalized gene-set analysis of GWAS data.[J]. PLoS Computational Biology, 2015, 11(4):e1004219.
3. Langfelder P, Horvath S. WGCNA: an R package for weighted correlation network analysis[J]. BMC bioinformatics, 2008, 9(1): 559.
