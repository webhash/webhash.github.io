---
title: Basics of statistics for genomics 
tags: [basics, statistics, genomics]
---

### p-value and null-hypothesis 


  P-value = P($$ S^n $$ more extreme than $$ S^0 $$ ```|``` null-distribution)

  $$ S^0 $$ : evaluated for how extreme it is 

  $$ S^n $$ : random variable generated from the null distribution 

  Null Distribution : The distribution of observed or expected $$ S^n $$ given that the null hypothesis is true. 


- The P-value is the probability of observing your test statistic or a statistic more extreme than it given that it was drawn from the null distribution.

- P-value caluclation based on the the random sample used. The more people we sample the more accurate will be our p-value. 

- A very small p-value means that such an extreme observed outcome would be very unlikely under the null hypothesis.

- But remember p-value doesn't say anything about the alternate hypothesis, it only talks about validity of null hypothesis. 

**Null Distribution**

- Assumed distribution would rarely match exactly with the emperical distribution

- Normal distribution is the most used Null distribution

![Normal Distribution](https://webhash.github.io/img/Normal_Distribution.png "Normal Distribution")

- X-axis represent the values that will be generated from the distribution and Y-axis represent the probability of generating that value 

- $$ Y = X \beta $$ , where Y represent the phenotype and X represent the bunch of genetics, and $$ \beta $$ represent affect size. $$ \beta $$ will follow normal distribution 

**Alternate Hypothesis**

- ![Normal Distribution and P-Values](https://webhash.github.io/img/ndist_pvalue.png "Normal Distribution and P-values")

- $$ Y = X_{42} \beta_{42} $$ , where $$ X_{42} $$ is an alternate allele or SNP42, $$ \beta_{42} $$ is the effect of alternate allele at SNP42 

- Null: $$ \beta_{42} $$ = 0 

- Alt theory is not $$ \beta_{42} \ne 0 $$, but ...

- Alt : SNP 42 is perfect LD with another SNP with non-zero effect , Or 

- Alt : SNP 42 correlates/tags population structure or confounding that we are don't know about

**Significance Threshold**

- If the significance threashold for rejecting the null hypothesis is 0.05, it means we have 1/20 chance that we reject the null hypothesis incorrectly, on each test that we do. 

- So if we do 100 test , all of which are truly under null , we can expect 5 false positives 




[1] created while following https://www.youtube.com/playlist?list=PLvdBkUzU6hPL1oZnsVW4hURGiIjfOLqzq
