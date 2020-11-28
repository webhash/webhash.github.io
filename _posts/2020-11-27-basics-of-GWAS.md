---
title: Understanding GWAS
tags : [GWAS, genomics, basics]
---


### GWAS 

- GWAS means Genome wide association studies 

- We are trying to find relationship between the phenotype and the genetics 

### Exophenotypes

In easy words it is basically outward apperance of a being like 
- Height
- BMI
- Hair color  
- Annual Salary 
- Favorite color 

### Endophenotype 

Things that are inside of us and might not be visible but are determined by the genetics like

- Blood sugar Level 
- RELN protien level 
- Diabetes
- Addiction 
- Cystic fibrosis


### Case-Control studies 

- We gather subjects and divide them in two different groups

- Case group has individuals who are impacted say by diabetes 

- Control group has individuals who are not impacted by the diabetes 

- Then we compare the genome difference between two group

- We might find a variation in genome that seems to be more prevelant in case group than control group

- If so then we shall have found a region in genome that in itself contribute to phenotype or atleast plays some role 


### Continous Phenotype or Trait

- For example height related information is quite prevelant and we have lot of data and genetic data for individuals

- Then we can map the Height vs SNPs, like a particular variation in allele, plot 

- We might find that people who have less copy of particular SNP in their genome are shorter than people who have more copies 

- So basically GWAS is trying to find relationship between the genome variation and the pheonotype 

- Linear regression model is used to determines these relationship 

### GWAS Model 

- In a full model of linear regression model we have $$ Y = G\beta + \epsilon $$, where G represent all the genetic variation seen and we want to calculate the $$ \beta $$ 

$$ 
\begin{bmatrix} y_{1} \\ y_{2} \\ \dots \\ y_{N} \end{bmatrix} = 
\begin{bmatrix} g_{11} & g_{12} & g_{13} & \dots & g_{1M} \\ 
g_{21} & g_{22} & g_{23} & \dots & g_{2M} \\ 
\dots  & \dots  & \dots  & \dots & \dots  \\ 
g_{N1} & g_{N2} & g_{N3} & \dots & g_{NM} \end{bmatrix} 
\begin{bmatrix} \beta_1 \\ \beta_2 \\ \dots \\ \beta_N  \end{bmatrix}
+
\begin{bmatrix} \epsilon_1 \\ \epsilon_2 \\ \dots \\ \epsilon_N \end{bmatrix} 
$$

- But it is hard to determine in one go use all the variation G and determine the $$ \beta $$, in statistic we say would say we dont have enough power to fit this model

- So what we do in GWAS is we try to fit a marginal model i.e. $$ Y = G_i\beta_i + \epsilon $$

$$ 
\begin{bmatrix} y_{1} \\ y_{2} \\ \dots \\ y_{N} \end{bmatrix} = 
\begin{bmatrix} g_{1i} \\ g_{2i} \\ \dots \\ g_{Ni}  \end{bmatrix} \beta_i +
\begin{bmatrix} \epsilon_1 \\ \epsilon_2 \\ \dots \\ \epsilon_N \end{bmatrix} $$

- we are trying to find what impact does $$i^{th} $$ variation/SNP in the genome has rather than all the variations.


### GWAS in the real world  

- We can write the GWAS equation for $$i^{th} $$ SNP on the $$ j^{th} $$ individual 

$$ y_j = \beta_i g_{ij} + \epsilon_j $$

- In real world we have to consider many other factors, below is the real world translation of above simplified equation 

$$ y_i = \beta_{sex}S_j + \beta_{age}A_j + \beta_{PC1}PC_{1j} + \beta_{PC2}PC_{2j} + \beta_ig_{ij} + \epsilon_j  $$

- In the above real world equation we have considered other covariants like sex, age and principal components. 

- If phenotype under consideration is height, we would like to remove impact that sex and age has on it. 

- Principal components capture the impact of population structure. 

- $$\beta_i$$ is the true effect which we would never know 

- $$ \hat {\beta_i} $$ is the estimated effect 

### GWAS, p-value and Manhattan plot 

- We use the Marginal model $$ y_j = \beta_i g_{ij} + /epsilon_j $$ to get the estimated effect $$ \hat {\beta_i} $$ and p-values

- We use manhattan plot to plot the p-values and different variants in the different section of genome 

![Manhattan](https://webhash.github.io/img/Manhattan_Plot.png "Manhattan Plot")

- In above plot one can see that on X-axis we have marked different chromosomes, each dot represent the different variant that were tested during the GWAS

- Y-axis plots the $$-log_{10}$$(p-value), smaller the p-value the higher the $$-log_{10}$$(p-value) and more the chance that null-hypothesis to be is invalid.

- Null hypothesis shall be in our context that the variation in genotype has no estimated effect.

### GWAS, p-value, FWER and Manhattan plot 

- Normally in statistic we use p-value as 0.05 , which $$-log_{10}$$(0.5) = 1.3 

- In the plot we have the this 1.3 right close to the bottom of the bars, and most of the variants have higher significance than 1.3 

![Manhattan](https://webhash.github.io/img/Manhattan_Plot.png "Manhattan Plot")

- We dont consider the p-value of 0.05 because we can have high family-wise error rate, i.e. the probability of having one or more false discovery 

- Thus we use p-value of 5 X $$10^{-8}$$ which translates to 7.3 through negative log scale 

- In the plot we see the high tower have bunch of variants maps together.

- Reason for that could be that bunch of variants are in high LD with each other, which means they going to have similar estimated effects and p-values

- So we don't precisely know which variant is causal variant or risk variant among the group, but we know some of the variant from the group have impact on the phenotype.

- So we call these groups genome locus or association locus, representing a group of variant that together have impact on phenotype. And the top of the peak is called top GWAS head or top head. 

- We might intutively think that the GWAS head would be the main variation, but that might not be the case.

- We do further analysis to determine the real varition among the GWAS locus.  




[1] created while following https://www.youtube.com/playlist?list=PLvdBkUzU6hPIkloQgFoSRqcC_SlsXvUOP 

 
