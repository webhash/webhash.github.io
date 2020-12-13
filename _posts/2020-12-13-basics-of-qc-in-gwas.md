---
title: Understanding Quality Control in GWAS
tags : [GWAS, genomics, basics, QC]
---


### Basics 
- Genotyping arrays enable the direct measurement of an individuals genotype at thousands of markers. 
- Subsequent analyses such as genome-wide association studies rely on the high quality of these marker genotypes


### Per-individual quality control

- We can do following per-individual quality control 
 - Identifying individual with discordant sex information 
 - Indentifying individual with outlying missing genotype and/or heterozygosity rates
 - Identifying related individuals
 - Identifying individuals of divergent ancestry
 
### Per-marker quality control
 
 - We can do following per-marker quality control 
  - Identifying markers with excessive missing genotype rates 
  - Identifying markers showing a significant deviation from Hardy-Weinberg equilibrium
  - Removal of markers with low minor allele frequency (MAF)

### Individuals with discordant sex information

[1] created while following https://meyer-lab-cshl.github.io/plinkQC/articles/plinkQC.html 
