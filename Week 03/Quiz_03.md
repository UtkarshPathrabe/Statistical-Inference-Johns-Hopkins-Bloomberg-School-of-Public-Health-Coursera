Quiz 02
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
<td align="center">7/7</td>
</tr>
</tbody>
</table>

Question 01
-----------

In a population of interest, a sample of 9 men yielded a sample average
brain volume of 1,100cc and a standard deviation of 30cc. What is a 95%
Student's T confidence interval for the mean brain volume in this new
population?

### Answer

-   \[1077,1123\]

#### Explanation

    x_bar <- 1100
    s <- 30
    n <- 9
    alpha <- 0.05
    ts <- qt(1 - alpha / 2, n - 1)
    round(x_bar + c(-1, 1) * ts * s / sqrt(n))

    ## [1] 1077 1123

Question 02
-----------

A diet pill is given to 9 subjects over six weeks. The average
difference in weight (follow up - baseline) is -2 pounds. What would the
standard deviation of the difference in weight have to be for the upper
endpoint of the 95% T confidence interval to touch 0?

### Answer

-   2.60

#### Explanation

    x_bar <- -2
    n <- 9
    alpha <- 0.05
    ts <- qt(1 - alpha / 2, n - 1)
    s <- -x_bar*sqrt(n) / ts
    s

    ## [1] 2.601903

Question 03
-----------

In an effort to improve running performance, 5 runners were either given
a protein supplement or placebo. Then, after a suitable washout period,
they were given the opposite treatment. Their mile times were recorded
under both the treatment and placebo, yielding 10 measurements with 2
per subject. The researchers intend to use a T test and interval to
investigate the treatment. Should they use a paired or independent group
T test and interval?

-   It's necessary to use both.  
-   You could use either.  
-   A paired interval.  
-   Independent groups, since all subjects were seen under both systems.

### Answer

-   A paired interval.

#### Explanation

-   Independent Group T test is used when there are no related
    participants.  
-   Paired T test is used when there are related participants and same
    group uses 2 different tests.

Question 04
-----------

In a study of emergency room waiting times, investigators consider a new
and the standard triage systems. To test the systems, administrators
selected 20 nights and randomly assigned the new triage system to be
used on 10 nights and the standard system on the remaining 10 nights.
They calculated the nightly median waiting time (MWT) to see a
physician. The average MWT for the new system was 3 hours with a
variance of 0.60 while the average MWT for the old system was 5 hours
with a variance of 0.68. Consider the 95% confidence interval estimate
for the differences of the mean MWT associated with the new system.
Assume a constant variance. What is the interval? Subtract in this order
(New System - Old System).

### Answer

-   \[-2.75, -1.25\]

#### Explanation

    n_x <- 10
    n_y <- 10
    x_bar <- 5
    y_bar <- 3
    var_x <- 0.6
    var_y <- 0.68
    alpha <- 0.05
    sp_2 <- ((n_x - 1)*var_x + (n_y - 1)*var_y) / (n_x + n_y - 2)
    sp <- sqrt(sp_2)
    ts <- qt(1 - (alpha/2), n_x + n_y - 2)
    round((y_bar - x_bar) + c(-1, 1) * ts * sp * (sqrt(1/n_x + 1/n_y)), 2)

    ## [1] -2.75 -1.25

Question 05
-----------

Suppose that you create a 95% T confidence interval. You then create a
90% interval using the same data. What can be said about the 90%
interval with respect to the 95% interval?

-   The interval will be the same width, but shifted.  
-   It is impossible to tell.  
-   The interval will be wider.  
-   The interval will be narrower.

### Answer

-   The interval will be narrower.

#### Explanation

90% confidence interval gives a lower range of t-test confidence
interval then 95% confidence interval.

Question 06
-----------

To further test the hospital triage system, administrators selected 200
nights and randomly assigned a new triage system to be used on 100
nights and a standard system on the remaining 100 nights. They
calculated the nightly median waiting time (MWT) to see a physician. The
average MWT for the new system was 4 hours with a standard deviation of
0.5 hours while the average MWT for the old system was 6 hours with a
standard deviation of 2 hours. Consider the hypothesis of a decrease in
the mean MWT associated with the new treatment. What does the 95%
independent group confidence interval with unequal variances suggest vis
a vis this hypothesis? (Because there's so many observations per group,
just use the Z quantile instead of the T.)

-   When subtracting (old - new) the interval contains 0. The new system
    appears to be effective.  
-   When subtracting (old - new) the interval contains 0. There is not
    evidence suggesting that the new system is effective.  
-   When subtracting (old - new) the interval is entirely above zero.
    The new system does not appear to be effective.  
-   When subtracting (old - new) the interval is entirely above zero.
    The new system appears to be effective.

### Answer

-   When subtracting (old - new) the interval is entirely above zero.
    The new system appears to be effective.

#### Explanation

    n_x <- 100
    n_y <- 100
    x_bar <- 6
    y_bar <- 4
    s_x <- 2
    s_y <- 0.5
    alpha <- 0.05
    sp_2 <- ((n_x - 1)*s_x^2 + (n_y - 1)*s_y^2) / (n_x + n_y - 2)
    sp <- sqrt(sp_2)
    ts <- qt(1 - (alpha/2), n_x + n_y - 2)
    round((x_bar - y_bar) + c(-1, 1) * ts * sp * (sqrt(1/n_x + 1/n_y)), 2)

    ## [1] 1.59 2.41

Question 07
-----------

Suppose that 18 obese subjects were randomized, 9 each, to a new diet
pill and a placebo. Subjects' body mass indices (BMIs) were measured at
a baseline and again after having received the treatment or placebo for
four weeks. The average difference from follow-up to the baseline
(followup - baseline) was ???3 kg/m2 for the treated group and 1 kg/m2
for the placebo group. The corresponding standard deviations of the
differences was 1.5 kg/m2 for the treatment group and 1.8 kg/m2 for the
placebo group. Does the change in BMI over the four week period appear
to differ between the treated and placebo groups? Assuming normality of
the underlying data and a common population variance, calculate the
relevant `90%` t confidence interval. Subtract in the order of (Treated
Placebo) with the smaller (more negative) number first.

### Answer

-   \[-5.364, -2.636\]

#### Explanation

    n_x <- 9
    n_y <- 9
    x_bar <- -3
    y_bar <- 1
    s_x <- 1.5
    s_y <- 1.8
    alpha <- 0.1
    sp_2 <- ((n_x - 1)*s_x^2 + (n_y - 1)*s_y^2) / (n_x + n_y - 2)
    sp <- sqrt(sp_2)
    ts <- qt(1 - (alpha/2), n_x + n_y - 2)
    round((x_bar - y_bar) + c(-1, 1) * ts * sp * (sqrt(1/n_x + 1/n_y)), 3)

    ## [1] -5.364 -2.636
