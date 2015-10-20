Quiz 04
=======

<table>
<thead>
<tr class="header">
<th align="center">Attempts</th>
<th align="center">Score</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="center">1/3</td>
<td align="center">9/9</td>
</tr>
</tbody>
</table>

Question 01
-----------

A pharmaceutical company is interested in testing a potential blood
pressure lowering medication. Their first examination considers only
subjects that received the medication at baseline then two weeks later.
The data are as follows (SBP in mmHg)

<table>
<thead>
<tr class="header">
<th align="center">Subject</th>
<th align="center">Baseline</th>
<th align="center">Week 2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="center">1</td>
<td align="center">140</td>
<td align="center">132</td>
</tr>
<tr class="even">
<td align="center">2</td>
<td align="center">138</td>
<td align="center">135</td>
</tr>
<tr class="odd">
<td align="center">3</td>
<td align="center">150</td>
<td align="center">151</td>
</tr>
<tr class="even">
<td align="center">4</td>
<td align="center">148</td>
<td align="center">146</td>
</tr>
<tr class="odd">
<td align="center">5</td>
<td align="center">135</td>
<td align="center">130</td>
</tr>
</tbody>
</table>

Consider testing the hypothesis that there was a mean reduction in blood
pressure? Give the P-value for the associated two sided T test.  
(Hint, consider that the observations are paired.)

### Answer

-   0.087

#### Explanation

    pharm <- data.frame(baseline = c(140, 138, 150, 148, 135), week2 = c(132, 135, 151, 146, 130))
    t.test(pharm$baseline, pharm$week2, alternative = "two.sided", paired = T)

    ## 
    ##  Paired t-test
    ## 
    ## data:  pharm$baseline and pharm$week2
    ## t = 2.2616, df = 4, p-value = 0.08652
    ## alternative hypothesis: true difference in means is not equal to 0
    ## 95 percent confidence interval:
    ##  -0.7739122  7.5739122
    ## sample estimates:
    ## mean of the differences 
    ##                     3.4

Question 02
-----------

A sample of 9 men yielded a sample average brain volume of 1,100cc and a
standard deviation of 30cc. What is the complete set of values of
*μ*<sub>0</sub> that a test of *H*<sub>0</sub> : *μ* = *μ*<sub>0</sub>
would fail to reject the null hypothesis in a two sided 5% Students
t-test?

### Answer

-   1077 to 1123

#### Explanation

    n <- 9
    mu <- 1100
    sd <- 30
    alpha <- .05
    tstat <- qt(1 - alpha/2, n - 1)
    mu + c(-1, 1)*tstat*sd / sqrt(n)

    ## [1] 1076.94 1123.06

Question 03
-----------

Researchers conducted a blind taste test of Coke versus Pepsi. Each of
four people was asked which of two blinded drinks given in random order
that they preferred. The data was such that 3 of the 4 people chose
Coke. Assuming that this sample is representative, report a P-value for
a test of the hypothesis that Coke is preferred to Pepsi using a one
sided exact test.

### Answer

-   0.31

#### Explanation

    library(stats)
    binom.test(x = 3, n = 4, p = .5, alt = "greater")

    ## 
    ##  Exact binomial test
    ## 
    ## data:  3 and 4
    ## number of successes = 3, number of trials = 4, p-value = 0.3125
    ## alternative hypothesis: true probability of success is greater than 0.5
    ## 95 percent confidence interval:
    ##  0.2486046 1.0000000
    ## sample estimates:
    ## probability of success 
    ##                   0.75

Question 04
-----------

Infection rates at a hospital above 1 infection per 100 person days at
risk are believed to be too high and are used as a benchmark. A hospital
that had previously been above the benchmark recently had 10 infections
over the last 1,787 person days at risk. About what is the one sided
P-value for the relevant test of whether the hospital is `below` the
standard?

### Answer

-   0.03

#### Explanation

    p <- 1 / 100
    pr <- 10 / 1787
    n <- 1787
    error <- sqrt(p * (1-p) / n)
    z <- (p-pr) / error
    pnorm(z, lower.tail = F)

    ## [1] 0.03066625

Question 05
-----------

Suppose that 18 obese subjects were randomized, 9 each, to a new diet
pill and a placebo. Subjects' body mass indices (BMIs) were measured at
a baseline and again after having received the treatment or placebo for
four weeks. The average difference from follow-up to the baseline
(followup - baseline) was -3 kg/m2 for the treated group and 1 kg/m2 for
the placebo group. The corresponding standard deviations of the
differences was 1.5 kg/m2 for the treatment group and 1.8 kg/m2 for the
placebo group. Does the change in BMI appear to differ between the
treated and placebo groups? Assuming normality of the underlying data
and a common population variance, give a `p-value` for a two-sided
`t-test`.

### Answer

-   Less than 0.01

#### Explanation

    n1 <- 9
    n2 <- 9
    df <- n1 + n2 - 2
    meanTreat <- -3
    meanPlacebo <- 1
    sdTreat <- 1.5
    sdPlacebo <- 1.8
    pooledVar <- (sdTreat^2 * n1 + sdPlacebo^2 * n2)/df
    se.diff <- sqrt(pooledVar/n1 + pooledVar/n2)
    tstat <- (meanTreat - meanPlacebo) / se.diff
    pValue <- 2 * pt(tstat, df = df)
    pValue

    ## [1] 0.0001852248

Question 06
-----------

Brain volumes for 9 men yielded a 90% confidence interval of 1,077 cc to
1,123 cc. Would you reject in a two sided 5% hypothesis test of
*H*<sub>0</sub> : *μ* = 1, 078?

### Answer

-   No you wouldn't reject.

#### Explanation

The 95% confidence interval contains 90% confidence interval.
*μ* = 1, 078 falls within 90% confidence interval and hence we don't
reject *H*<sub>0</sub>.

Question 07
-----------

Researchers would like to conduct a study of 100 healthy adults to
detect a four year mean brain volume loss of .01 mm3. Assume that the
standard deviation of four year volume loss in this population is .04
mm3. About what would be the power of the study for a 5% one sided test
versus a null hypothesis of no volume loss?

### Answer

-   0.80

#### Explanation

    n <- 100
    mu <- .01
    sd <- .04
    power.t.test(n, delta = mu, sd = sd, type = "one.sample", alt = "one.sided")$power

    ## [1] 0.7989855

Question 08
-----------

Researchers would like to conduct a study of n healthy adults to detect
a four year mean brain volume loss of .01 mm3. Assume that the standard
deviation of four year volume loss in this population is .04 mm3. About
what would be the value of n needded for 90% power of type one error
rate of 5% one sided test versus a null hypothesis of no volume loss?

### Answer

-   140

#### Explanation

    mu <- .01
    sd <- .04
    power <- .9
    power.t.test(power = power, delta = mu, sd = sd, type = "one.sample", alt = "one.sided")$n

    ## [1] 138.3856

Question 09
-----------

As you increase the type one error rate, *α*, what happens to power?

### Answer

-   You will get larger power.

#### Explanation

As you increase the type one error rate *α*, or use one-sided test
instead of two-sided test or increase n, power will get larger.
