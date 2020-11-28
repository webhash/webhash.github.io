---
title: Understaning GWAS 
---


## GWAS 

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

- We gather subjects and devide them in two different groups 
- Case group has individuals who are impacted say by diabetes 
- Control group has individuals who are not impacted by the diabetes 
- Then we compare the genome difference between two group
- We might find a variation in genome that seems to be more prevelant in case group than control group 
- If so then we shall have found a region in genome that in itself contribute to phenotype or atleast plays some role 


### Continous Phenotype or Trait

- Say ,for example, height related information is quite prevelant and we have lot of data and genetic data for individuals 
- Then we can map the Height vs SNPs, like a particular variation in allele, plot 
- We might find that people who have less copy of particular SNP in their genome are shorter than people who have more copies 
- So basically GWAS is trying to find relationship between the genome variation and the pheonotype 
- Linear regression model is used to determines these relationship 

### GWAS Model 

- In a full model of linear regression model we have $$ Y = G\beta + \epsilon $$, where G represent all the genetic variation seen and we want to calculate the $$ \beta $$ 
- But it is hard to determine in one go use all the variation G and determine the $$ \beta $$, in statistic we say would say we dont have enough power to fit this model
- So what we do in GWAS is we try to fit a marginal model i.e. $$ Y = G_i\beta_i + e $$
- we are trying to find what impact does $$i^t^h $$ variation/SNP in the genome has



