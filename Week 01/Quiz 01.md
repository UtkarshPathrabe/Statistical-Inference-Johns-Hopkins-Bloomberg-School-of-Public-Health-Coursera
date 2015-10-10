---
title: "Statistical Inference - Quiz 01"
author: "Utkarsh Ashok Pathrabe"
output: md_document
---

Quiz 01
=======  

|Attempts|Score|  
|:------:|:---:|  
|   1/3  | 6/6 |  

Question 01
-----------  
Consider influenza epidemics for two parent heterosexual families. Suppose that the probability is 17% that at least one of the parents has contracted the disease. The probability that the father has contracted influenza is 12% while the probability that both the mother and father have contracted the disease is 6%. What is the probability that the mother has contracted influenza?  

### Answer  
11%  

#### Explanation  
P(A Union B) = 0.17  
P(A) = 0.12  
P(A Intersection B) = 0.06  
P(B) = P(A Union B) + P(A Intersection B) - P(A)  
P(B) = 0.11  

Question 02
-----------  
A random variable, X is uniform, a box from 0 to 1 of height 1. (So that its density is f(x) = 1 for 0 <= x <= 1.) What is its 75th percentile?   

### Answer  
0.75  

#### Explanation  
Execute `pbeta(0.75, 1, 1)`.  

Question 03  
-----------  
You are playing a game with a friend where you flip a coin and if it comes up heads you give her X dollars and if it comes up tails she gives you Y dollars. The probability that the coin is heads is p (some number between 0 and 1.) What has to be true about X and Y to make so that both of your expected total earnings is 0. The game would then be called "fair".  

### Answer  
p/(1-p) = Y/X  

#### Explanation  
p\*(-X) + (1-p)\*(Y) = 0  
p\*X = (1-p)\*Y  
p/(1-p) = Y/X  

Question 04
-----------  
A density that looks like a normal density (but may or may not be exactly normal) is exactly symmetric about zero. (Symmetric means if you flip it around zero it looks the same.) What is its median?  

### Answer  
* The median must be 0.  

Question 05
-----------  
Consider the following PMF shown below in R.  
```{r}
x <- 1:4
p <- x/sum(x)
temp <- rbind(x, p)
rownames(temp) <- c("X", "Prob")
temp
```  
```{r}
##      [,1] [,2] [,3] [,4]
## X     1.0  2.0  3.0  4.0
## Prob  0.1  0.2  0.3  0.4
```  
What is the mean?  

### Answer  
3  

#### Explanation  
(1\*0.1) + (2\*0.2) + (3\*0.3) + (4\*0.4)  
= 0.1 + 0.4 + 0.9 + 1.6  
= 3.0  

Question 06
-----------  
A web site [www.medicine.ox.ac.uk/bandolier/band64/b64-7.html](www.medicine.ox.ac.uk/bandolier/band64/b64-7.html) for home pregnancy tests cites the following: "When the subjects using the test were women who collected and tested their own samples, the overall sensitivity was 75%. Specificity was also low, in the range 52% to 75%." Assume the lower value for the specificity. Suppose a subject has a positive test and that 30% of women taking pregnancy tests are actually pregnant. What number is closest to the probability of pregnancy given the positive test?  

### Answer  
* 40%  

#### Explanation  
Sensitivity = P(+|D) = 0.75  
Specificity = P(-|D') = 0.52  
P(D) = 0.30  
P(+|D') = 1 - P(-|D') = 1 - 0.52 = 0.48  
P(C') = 1 - P(D) = 1 - 0.3 = 0.7  
P(+|D)\*P(D) = 0.225  
P(+|D')\*P(D') = 0.336  
By Bayes Theorem,  
P(D|+) = (P(+|D)\*P(D)) / ((P(+|D)\*P(D)) + (P(+|D')\*P(D')))  
P(D|+) = (0.225) / (0.225 + 0.336)  
P(D|+) = 0.4010695187  