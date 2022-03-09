# Confidence Intervals for Cross Validation Error Estimates

We use cross validation to estimate the extra-sample ("training data") accuracy (or "error estimate") for a given model. This error metric gives us a good estimation on how well the model will likely perform on data it has not yet seen (e.g., the greater population of data).

The cross-validation error estimate (the average of the error estimates across all folds) is a great way to compare different models as well.

Adding a confidence interval to the cross validation error estimate gives us a better idea of how well the model will perform over time as it encounters the population of data in the wild.



## What Are Confidence Intervals?

A confidence interval gives us a range of values that bound a statistic's mean (above and below). These bounds likely contain the unknown population parameter we're interested in measuring. These bounds (e.g., "confidence interval") refer to a percentage of probability ("certainty") that the confidence interval range would capture the true population parameter if we were to draw random samples from the population a lot of times.

"A confidence interval is a range of values, bounded above and below the statistic's mean, that likely would contain an unknown population parameter. Confidence level refers to the *percentage of probability*, or certainty, that the confidence interval would contain the true population parameter when you draw a random sample many times."


### How Are Confidence Intervals Useful in Machine Learning?

A confidence interval for cross validation error estimates gives us a good explanation of the range of performance of a machine learning model.

We sometimes may want to give a measure of the uncertainty around the error estimate. This can help us understand the range of potential outcomes which may impact how a line of business would use a given model. In these situations we want to compute a “confidence interval” for the error estimation of cross-validation.

If "confidence level" refers to "percentage of probability" of certainty, then we can assume that 95% of the time our accuracy should be between the lower and upper bound of the estimate.

Based on statistics we can then calculate how often (e.g., "number of days per year") a model will perform outside of the confidence interval. This is useful when expressing to non-data science folks how often to expect the model to hold within the confidence interval range. The sidebar below explains how to calculate this "number of days" metric.

<style>
th, td {
padding: 15px;
text-align: left;
}
th {
  background-color: #666666;
  color: white;
}
tr:nth-child(even) {background-color: #e2e2e2;}
tbody{
    width: 100%;
    display: table;
}
</style>
<div style="width: 100%; margin:0 auto;">
<div style="padding: 16px; font-size: 12px; border: 1px solid #999999; width: 85%; text-align: left; background-color: #eeeeee;">
<img src="./spyglass_icon.jpg" style=" width: 80px; height: 80px; float: left; margin-right: 20px;" />

<h4>Probabilities of Occurrence of Rare Events</h4>
<p style="font-size: 14px; ">
<i>

<table style="width: 100%; border: 1px solid;">
<tr>
<th>std. deviations</th>
<th>Probability (%)</th>
<th>Events/year</th>
<th>Events/five years</th>
</tr>
<tr>
<td>-1.0</td>
<td>15.87</td>
<td>40</td>
<td>200</td>
</tr>
<tr>
<td style="font-weight: bold;">-2.0</td>
<td style="font-weight: bold;">2.28</td>
<td style="font-weight: bold;">6</td>
<td style="font-weight: bold;">29</td>
</tr>
<tr>
<td>-2.5</td>
<td>0.62</td>
<td>2</td>
<td>8</td>
</tr>
<tr>
<td>-3.0</td>
<td>0.13</td>
<td>0</td>
<td>2</td>
</tr>																		
</table>
<br/>
<p>
Table Source: <A href="https://www.amazon.com/Advanced-Portfolio-Management-Fundamental-Investors/dp/1119789796/ref=sr_1_3?crid=OHH49WRDMO4L&keywords=advanced+portfolio+management+by+paleologo&qid=1638288877&qsid=142-2453615-6550551&sprefix=advanced+portfolio%2Caps%2C163&sr=8-3&sres=1119789796%2CB071Y3MSRK%2CB07236Q2C3%2CB075332F51%2CB07SVG5N45%2CB08N46B7HJ%2CB07MPNMGHS%2CB08QMCHBM2%2CB07PC3FXV5%2CB01N74KH32%2CB0931YYH25%2CB08S7NMR8Q%2CB01FKZSCRW%2CB086JWBF8M%2CB093L8B373%2CB084STCZNP&srpt=ABIS_BOOK">Advanced Portfolio Management: A Quant's Guide for Fundamental Investors 1st Edition</A>
</p>

<p>
The above chart represents a single tail metric (the "bad tail", as opposed to the tail on the other side of the mean) for how often a "rare event" occurs. It's another way to think about how often our model error would be outside its confidence interval in terms of "days per year".
</p>
<p>
A 95% confidence interval is roughly the same as -1.96 std. deviations from the mean.
</p>
<p>
So model performance outside of the 95% confidence interval should be 12 days (240 days * .95 = ~228 days, 240 - 228 == 12 days).
</p>
<p>
The means that half of those days outside of the confidence interval should be below the low bound, so 6 days per year we'd fall under the lower end of the confidence interval.
</p>
</i></p>
</div>	
</div>	


## Methods to Build Confidence Intervals

Below we list 4 ways that we can calculate a confidence interval for a model's performance.

* [](se-cv-err-estimate-model)
* [](using-bootstrap-calc-err-estimate-ci)
* [](using-student-t-calc-err-estimate-ci)
* Binomial proportion

In the following sections, we give explanations and live notebook code for 3 of the the methods.

```{note}
For more reading on Confidence Intervals and various methods to generate them, check out Sebastian Raschka's paper:

* Raschka, S. (2018). <a href="https://arxiv.org/abs/1811.12808">Model Evaluation, Model Selection, and Algorithm Selection in Machine Learning
</a>, Arxiv.org
```


(se-cv-err-estimate-model)=
## Using Standard Error to Calculate the Cross Validation Error Estimate Confidence Interval

With K-fold cross-validation it is often useful to understand the quantitative notion of variability for the cross-validation error (evaluation metric) estimate. One method to build this confidence interval is to use standard error.

This method is based on:

* Cross-validation: what does it estimate and how well does it do it? by Stephen Bates, Trevor Hastie, and Robert Tibshirani, (2021) available at [https://arxiv.org/abs/2104.00673](https://arxiv.org/abs/2104.00673)
* [Dr. Ryan Tibshirani’s notes on CV error](https://www.stat.cmu.edu/~ryantibs/advmethods/notes/errval.pdf)

We compute the confidence intervals with the following formula:


```{math}
\bar{e} - z_{1-\alpha/2}\cdot\hat{SE}, \\
\bar{e} + z_{1-\alpha/2}\cdot\hat{SE} \\
```

where:

* $\bar{e}$ is the cross validation error estimate (e.g., average of the cross validation folds' errors)
* $z_{1-\alpha/2}$ is the z-score 
* $\hat{SE}$ is the standard error of the cross validation error estimate

### Calculating the Cross Validation Error Estimate

The cross validation error estimate is computed by averaging the error scores of each of the held out cross validation K folds. This is the normal error estimate produced by any cross validation modeling building process.

### Calculating the Z-Score

The z-score (also called hte "standard normal deviate", or the "normal score") is calcuated based on the level of confidence interval we want. For a 95% confidence interval, the z-score is the approximate value of the 97.5 percentile point of the standard normal distribution. This 97.5 percentile point gives us the [approximate value of 1.96 standard deviations](https://en.wikipedia.org/wiki/1.96).

[![The Normal Distribution via Wikipedia](https://upload.wikimedia.org/wikipedia/commons/2/25/The_Normal_Distribution.svg)](https://upload.wikimedia.org/wikipedia/commons/2/25/The_Normal_Distribution.svg)

This 1.96 standard deviations value is what we substitute back into the original confidence interval equation for z when calculating a 95% confidence interval.

```{note}
It's worth mentioning that 95% of the values for our distribution fall inside the range of (-1.96 standard deviations, +1.96 standard deviaions)
```

To understand how the z term gives us the value 1.96 standard deviations (via the 97.5 percentile point, as seen in the "cumulative %" band in the graph above) for the 95% confidence interval, let's quickly work through calculating the term $z_{1-\alpha/2}$ by resolving its subscript value (aka the "percentile point", or "cumulative %"):

```{math}
 = 1 - \alpha / 2
```

And to calculate alpha we use a 0.95 confidence level:

```{math}
\alpha = 1 - 0.95 \\
\alpha = 0.05
```

Substituting $\alpha$ back into the percentile point equation, this gives us:

```{math}
 = 1 - 0.05 / 2 \\
 = 1 - 0.025 \\
 = 0.975
```

From the 0.975 (the 97.5% percentile point) value we can look up our z-score on the graph above, giving us 1.96 as the z-score to substitute back into the confidence interval equation.


### Calculating the Standard Error of the Cross Validation Error Mean

We can [compute the standard error of the cross validation error estimate](https://www.stat.cmu.edu/~ryantibs/advmethods/notes/errval.pdf) by dividing the sample standard deviation by the square root of the number of observations (K, for K folds).

```{math}
\hat{SE} = \frac{sd(cverr_0, cverr_1,...,cverr_K)}{\sqrt{K}}
```

where $sd$ denotes the sample standard deviation and $cverr_n$ are the errors from each of the cross validation folds.

Standard error is defined as:
> Standard Error of a statistic (usually an estimate of a parameter) is the standard deviation of its sampling distribution or an estimate of that standard deviation. If the statistic is the sample mean, it is called the standard error of the mean (SEM)

(source: <a href="https://en.wikipedia.org/wiki/Standard_error">wikipedia.org</a>)

Standard error measures the accuracy of how a data sample represents the larger population of data. It is the approximate standard deviation of a statistical sample. Put another way, the standard error is the deviation of a sample mean from the actual population mean.

```{note}
In the context of machine learning, we're taking the "sample standard deviation" here of the sample represented by the training records; we don't have the full population of data to train on, so our training records, from a statistical viewpoint, are considered a "sample".

* For further reading on the intuition of Standard Error, check out [this discussion on Stack Exchange](https://stats.stackexchange.com/questions/60484/why-is-the-formula-for-standard-error-the-way-it-is)
```

With the standard error of the sample mean (here, the mean of the fold errors), we can then calculate the 95% confidence intervals for our cross validation error estimate (e.g., "95% confidence interval for the population mean", or to put it another way: "confidence intervals for the error estimate of the full population of data our model might encounter in the wild").

This is useful for helping us understand if the difference between two models is statistically significant, which is certainly useful.

```{note}
<!--
This method is from [Dr. Ryan Tibshirani’s notes on CV error](https://www.stat.cmu.edu/~ryantibs/advmethods/notes/errval.pdf) where he reminds us that the standard deviation and the standard error of the cross-validation error estimate are the same thing because n > 30 for CV K = 10 (where we’re using the error estimates of each fold as our samples of population). 
-->
<!-- 
He goes on to state it more directly:

> The standard error is the standard deviation of the Student t-distribution

And if we treat each error estimate as a sample then n = 10 (e.g., “small sample size”) and we only have the sample standard deviation, we need to use the Student’s T distribution.

> TODO: explain how this is different than the other section below

The method given in Ryan's notes pdf is the one given in his lecture notes and also the book [Elements of Statistical Learning](https://web.stanford.edu/~hastie/ElemStatLearn//printings/ESLII_print12_toc.pdf); the k averages are treated as data and we use our usual standard error formula.

If we wish to “assign a quantitative notion of variability to the cv error estimate” (aka “quick estimate of the standard error of the out-of-sample error”), then we can take the average of the fold errors and calculate the standard error of the model error estimate as: 
CV_SE = stddev( fold errors ) / sqrt( K )
-->
To read more on calculating standard error for cross validation, take a look at:

The Paper: Cross-validation: what does it estimate and how well does it do it? by Stephen Bates, Trevor Hastie, and Robert Tibshirani, (2021) available at [https://arxiv.org/abs/2104.00673](https://arxiv.org/abs/2104.00673)

The CMU course lecture [notes 1](https://www.stat.cmu.edu/~ryantibs/datamining/lectures/18-val1.pdf), [notes 2](https://www.stat.cmu.edu/~ryantibs/datamining/lectures/19-val2.pdf) on Data Mining: 36-462/36-662 with Dr. Ryan Tibshirani. 

Additionally take a look at section 7.10 of the book [Elements of Statistical Learning](https://web.stanford.edu/~hastie/ElemStatLearn//printings/ESLII_print12_toc.pdf).
```

### Confidence Intervals for Cross Validation Error Estimates

A confidence interval gives us a range of values that bound a statistic's mean (above and below). These bounds likely contain the unknown population parameter we're interested in measuring. These bounds (e.g., "confidence interval") refer to a percentage of probability ("certainty") that the confidence interval range would capture the true population parameter if we were to draw random samples from the population a lot of times.

If confidence level refers to "percentage of probability" of certainty, then for a 95% confidence interval we can assume that 95% of the time our accuracy should be between the lower and upper bound of the estimate.

Returning to our confidence interval equations:

```{math}
\bar{e} - z_{1-\alpha/2}\cdot\hat{SE}, \\
\bar{e} + z_{1-\alpha/2}\cdot\hat{SE} \\
```

Substituting 1.96 for the z-score for the 95% confidence interval gives us:


```{math}
\bar{e} - 1.96\cdot\hat{SE}, \\
\bar{e} + 1.96\cdot\hat{SE} \\
```

This will give a high CI and a low CI around the mean accuracy for the Cross Validation process
<!--
<a href="https://en.wikipedia.org/wiki/Standard_error#:~:text=is%20much%20simpler.-,Assumptions,-and%20usage%5Bedit">SE is equal to the standard error for the sample mean</a>, and 1.96 is the approximate value of the 97.5 percentile point of the normal distribution:
-->
<!--
Check out p.264 in 

The <a href="https://web.stanford.edu/~hastie/ElemStatLearn//printings/ESLII_print12_toc.pdf">book "The Elements of Statistical Learning" by Hastie, Tibshirani and Friedman</a> for an example of how this number is used in computing a confidence interval.
-->

We can see this in action in the live notebook: [ link ]

<!--
#### Notes from JD
> “so what's going on with both the t-dist and the sqrt(n) adjustment is an attempt to consider variation that comes from sample size”
> “t-dist is really just a Gaussian distribution with some uncertainty built in bc. of sample size (degrees of freedom) but they are slightly different ways of getting there “
-->


<p>
<iframe width="800" height="500" src="https://nbviewer.jupyter.org/github/pattersonconsulting/predictive_maintenance/blob/main/notebooks/confidence_intervals/ml_sklearn_breastcancer_cross_validation_standard_error_nov2021.ipynb?flush_cache=true"></iframe>

</p>

(using-bootstrap-calc-err-estimate-ci)=
## Using Bootstrap to Calculate Error Estimate Confidence Intervals

Another variant of calculation for the error estimate is to use bootstrap to calculate our model's error estimate confidence intervals.

```{note}
For more information on what is bootstrap, check out the following resources:


* [https://www.stat.cmu.edu/~ryantibs/advmethods/notes/bootstrap.pdf](https://www.stat.cmu.edu/~ryantibs/advmethods/notes/bootstrap.pdf)
* [https://www.stat.cmu.edu/~ryantibs/advmethods/shalizi/ch06.pdf](https://www.stat.cmu.edu/~ryantibs/advmethods/shalizi/ch06.pdf)
* The book "Regression Modeling Strategies" by Harrell 
* The book ["An Introduction to the Bootstrap"](http://www.ru.ac.bd/stat/wp-content/uploads/sites/25/2019/03/501_02_Efron_Introduction-to-the-Bootstrap.pdf) by Efron and Tibshirani 

```

We can see this in action in the live notebook: [ link ]

<p>
<iframe width="800" height="500" src="https://nbviewer.jupyter.org/github/pattersonconsulting/predictive_maintenance/blob/main/notebooks/confidence_intervals/ml_sklearn_breastcancer_mlxtend_632bootstrap_nov2021.ipynb?flush_cache=true"></iframe>

</p>


(using-student-t-calc-err-estimate-ci)=
## Using the Student's t-Distribution to Calculate Cross Validation Error Estimate Confidence Intervals

Another way to compute the 95% Confidence Intervals for 10-Fold Cross Validation is with the Student's t-Table.

The standard error is the standard deviation of the Student t-distribution. T-distributions are slightly different from Gaussian, and vary depending on the size of the sample.

### Calculating a 95% confidence interval for a population mean

(Step 1) determine if you need to use:     
* the normal distribution
* the student's t-distribution

(Step 2) if we have the sample standard deviation
* this is an indication to use the student's t distribution

(Step 3) sample size as another indicator
* when n >= 30 then we use the normal distribution
* when n < 30 we use the student t distribution

(Step 4) Compute confidence intervals for the population mean

The equation to compute the low and high confidence intervals is:

```{math}
CIs = \bar{e} \pm EBM
```

where EBM stands for error bound for a population mean:

```{math}
EBM = t_{v, \alpha/2} * \frac{s}{\sqrt(n)}
```

where:
* t is the t-score
* v is the degrees of freedom (df), df = n – 1 degrees of freedom
* $\alpha$ ("significance level") is the probability that the interval does not contain the unknown population parameter
* s is the sample standard deviation
* n is the number of samples

The error bound (EBM) depends on the confidence level (abbreviated CL).

The confidence level is often considered the probability that the calculated confidence interval estimate will contain the true population parameter. Also, the $\alpha$ variable is the probability that the interval does not contain the unknown population parameter:

$cl = 1 - \alpha$

```{note}
The most commonly used significance level is $\alpha$ = 0.05. 

From the section above, we recall that to calculate alpha we use a confidence level. For a 95% confidence level we'd use 0.95:

$\alpha = 1 - cl$

$\alpha = 1 - 0.95$

$\alpha = 0.05$

For a two-sided test, we compute:

$1 - \frac{\alpha}{2}$

or 

$1 - \frac{0.05}{2} = 0.975$

And so we use 0.975 as our lookup column in the Student's t-table, as we'll see below.
```

If we substitute EBM back into the original confidence intervals equation we get:

```{math}
CIs = \bar{e} \pm t_{v, \alpha/2} * \frac{s}{\sqrt(n)}
```

To calculate the value of t, we need to first calculate the value of v and $\alpha$ where $\alpha$ is the significance level.

The v parameter is the "degrees of freedom", and is calculated as number of samples minus 1:

```{math}
v = n - 1
```

Now we can lookup t in student's t-distribuion table. The table gives t-scores that correspond to the confidence level (column) and degrees of freedom (row). From above, we have degrees of freedom (v: 9) and confidence level (0.975):

<pre>
  ν         0.90    0.95   0.975    0.99   0.995   0.999

  1.       3.078   6.314  12.706  31.821  63.657 318.313
  2.       1.886   2.920   4.303   6.965   9.925  22.327
  3.       1.638   2.353   3.182   4.541   5.841  10.215
  4.       1.533   2.132   2.776   3.747   4.604   7.173
  5.       1.476   2.015   2.571   3.365   4.032   5.893
  6.       1.440   1.943   2.447   3.143   3.707   5.208
  7.       1.415   1.895   2.365   2.998   3.499   4.782
  8.       1.397   1.860   2.306   2.896   3.355   4.499
 <b> 9.       1.383   1.833   <span style="color:red;">2.262</span>   2.821   3.250   4.296</b>
 10.       1.372   1.812   2.228   2.764   3.169   4.143
</pre>

In the table above we find the value 2.262 for these parameters. Let's now substitute this value back into the original confidence intervals equation:

```{math}
CIs = \bar{e} \pm 2.262 * \frac{s}{\sqrt(n)}
```

Let's also change n to k, because we have k-folds:

```{math}
CIs = \bar{e} \pm 2.262 * \frac{s}{\sqrt(k)}
```

```{note}
It's worth mention how similar this equation ends up looking to the "Standard Error" version of calculating confidence intervals. The difference is that the student-t version factors in a wider range with its larger 2.262 value (where 2.262 is larger than 1.96 from above).
```
<!--
What does this confidence interval mean?

This confidence interval means that we are 95% sure that the "average accuracy for this model on of all breast cancer data in the full population of breast cancer data is somewhere between 93.7% and 97.1%"
-->
In the example notebook below, you can see the 95% confidence intervals calculated with the student-t method.

<p>
<iframe width="800" height="500" src="https://nbviewer.jupyter.org/github/pattersonconsulting/predictive_maintenance/blob/main/notebooks/confidence_intervals/ml_sklearn_breastcancer_cross_validation_student_T_CI_nov2021.ipynb?flush_cache=true"></iframe>

</p>

