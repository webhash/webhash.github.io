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

--- 

### Individuals with discordant sex information

- The identification of individuals with discordant sex information helps to detect sample mix-ups and samples with very poor genotyping rates.
- For each sample, the homozygosity rates across all X-chromosomal genetic markers are computed and compared with the expected rates (typically $<$0.2 for females and $>$0.8 for males).
- For samples where the assigned sex (PEDSEX in the .fam file) contradicts the sex inferred from the homozygosity rates (SNPSEX), it should be checked that the sex was correctly recorded (genotyping often occurs at different locations as phenotyping and misrecording might occur). 
-Samples with discordant sex information that is not accounted for should be removed from the study.

### Individuals with outlying missing genotype and/or heterozygosity rates

- The identification of individuals with outlying missing genotype and/or heterozygosity rates helps to detect samples with poor DNA quality and/or concentration that should be excluded from the study.
- Typically, individuals with more than 3-7% of their genotype calles missing are removed.
- Outlying heterozygosity rates are judged relative to the overall heterozygosity rates in the study, and individuals whose rates are more than a few standard deviations (sd) from the mean heterozygosity rate are removed.
- A typical quality control for outlying heterozygoisty rates would remove individuals who are three sd away from the mean rate.

### Related individuals

- Depending on the future use of the genotypes, it might required to remove any related individuals from the study. 
- Related individuals can be identified by their proporting of shared alleles at the genotyped markers
- Standardly, individuals with second-degree relatedness or higher will be excluded. 

### Individuals of divergent ancestry

- The identification of individuals of divergent ancestry can be achieved by combining the genotypes of the study population with genotypes of a reference dataset consisting of individuals from known ethnicities (for instance individuals from the Hapmap or 1000 genomes study)
- Principal component analysis on this combined genotype panel can be used to detect population structure down to the level of the reference dataset

--- 

### Markers with excessive missingness rate 

- Markers with excessive missingness rate are removed as they are considered unreliable. 
- Typically, thresholds for marker exclusion based on missingness range from 1%-5%

### Markers with deviation from HWE 

- Markers with strong deviation from HWE might be indicative of genotyping or genotype-calling errors.
- As serious genotyping errors often yield very low p-values, it is recommended to choose a reasonably low threshold to avoid filtering too many variants (that might have slight, non-critical deviations).
- Can be calculated via the observed and expected heterozygote frequencies per SNP in the individuals that passed the per Individual QC and computes the deviation of the frequencies from Hardy-Weinberg equilibrium (HWE) by HWE exact test

### Markers with low minor allele frequency

- Markers with low minor allele count are often removed as the actual genotype calling is very difficult due to the small sizes of the heterozygote and rare-homozygote clusters. 

---

[1] created while following https://meyer-lab-cshl.github.io/plinkQC/articles/plinkQC.html 
