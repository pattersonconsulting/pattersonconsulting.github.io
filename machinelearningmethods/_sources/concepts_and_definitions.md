# Concepts and Definitions

This article is meant to provide a [ TODO ]

(what-is-probability)=
## Probability


(what-is-the-normal-distribution)=
## The Normal Distribution

> The normal distribution carries with it assumptions and can be completely specified by two parameters: the mean and the standard deviation. If the mean and standard deviation are known, you can access every data point on the curve.
> The empirical rule is a handy quick estimate of the data's spread given the mean and standard deviation of a data set that follows a normal distribution.

[ stats on standard deviations ]

> Thus, almost all the data lies within 3 standard deviations. This rule enables us to check for Outliers and is very helpful when determining the normality of any distribution.

### Relationship Between the Normal Distribution and Machine Learning

> In Machine Learning, data satisfying Normal Distribution is beneficial for model building. It makes math easier. Models like LDA, Gaussian Naive Bayes, Logistic Regression, Linear Regression, etc., are explicitly calculated from the assumption that the distribution is a bivariate or multivariate normal. Also, Sigmoid functions work most naturally with normally distributed data.

> Many natural phenomena in the world follow a log-normal distribution, such as financial data and forecasting data. By applying transformation techniques, we can convert the data into a normal distribution. Also, many processes follow normality, such as many measurement errors in an experiment, the position of a particle that experiences diffusion, etc.

> So it’s better to critically explore the data and check for the underlying distributions for each variable before going to fit the model.


[ relationship with EDA ]

> Note: Normality is an assumption for the ML models. It is not mandatory that data should always follow normality. ML models work very well in the case of non-normally distributed data also. Models like decision tree, XgBoost, don’t assume any normality and work on raw data as well. Also, linear regression is statistically effective if only the model errors are Gaussian, not exactly the entire dataset.



(what-is-class-prior)
## Class Prior

A class prior is the probability that the event occurs in a dataset.

To calculate the class event probability we divide the number of occurences of this event by the total number of events in the dataset.

> The prior is, generally speaking, a probability distribution that expresses one’s beliefs about a quantity before some evidence is taken into account. If we restrict ourselves to an ML model, the prior can be thought as of the distribution that is imputed before the model starts to see any data.

> The class prior is an estimate of the probability that randomly sampling an instance from a population will yield the given class (regardless of any attributes of the instance). Weka is assuming that your training data are randomly drawn from a population such that the proportions of classes in your training set are indicative of their relative abundance in the sampled population. 

[ how is this related to "probability priors"? ]

> Put simply, and without any mathematical symbols, prior means initial beliefs about an event in terms of probability distribution. You then set up an experiment and get some data, and then "update" your belief (and hence the probability distribution) according to the outcome of the experiment, (the posteriori probability distribution).

also:

> Prior: Probability distribution representing knowledge or uncertainty of a data object prior or before observing it

## Prior Probability

> [wikipedia] "In Bayesian statistical inference, a prior probability distribution, often simply called the prior, of an uncertain quantity is the probability distribution that would express one's beliefs about this quantity before some evidence is taken into account. For example, the prior could be the probability distribution representing the relative proportions of voters who will vote for a particular politician in a future election. The unknown quantity may be a parameter of the model or a latent variable rather than an observable variable."

<!--
  
## Injecting Prior Knowledge

> Therefore, a perhaps not so obvious way to inject prior knowledge and beliefs into the process is through the training data selection. Indeed, by selecting and labeling training samples for any supervised learning model, we encode knowledge into the learning model. The data labeling process might be trivial in some domains, but will require a good deal of domain knowledge in others. For example, to label cats and dogs we need to understand the difference between these two animals, which might seem very “common sense”, but to label medical images as “cancer” or “not cancer”, we need deep medical expertise.

also:

> incorporate prior knowledge into DL systems by using synthetic data.


## Likelihood

[ todo ]

## Odds

[ todo ]

-->
(what-are-eval-metrics)
## Evaluation Metrics

Need to reference:

https://aaaipress.org/Papers/KDD/1997/KDD97-007.pdf


<!--

(what-is-average-precision)=
### Average Precision

-->

### Majority Class

[ todo ]

## Threshold Tuning

[ why do we have to train in classifcation? -- to get a baseline set of rankings from a classifier so we can then adjust the threshold ]

> "Note: "Tuning" a threshold for logistic regression is different from tuning hyperparameters such as learning rate. Part of choosing a threshold is assessing how much you'll suffer for making a mistake. For example, mistakenly labeling a non-spam message as spam is very bad. However, mistakenly labeling a spam message as non-spam is unpleasant, but hardly the end of your job."

https://developers.google.com/machine-learning/crash-course/classification/thresholding

> "Ranking is better than classifying (or: Don’t brain-damage your classifier)"
https://www.svds.com/classifiers2/

https://towardsdatascience.com/how-to-add-decision-threshold-tuning-to-your-end-to-end-ml-pipelines-7077b82b71a

* Training Stage
  * calibration can give better scores / probs [todo:investigate further]
* we can't skip training, because it gives us a ranked list by prob. estimates
  * we need to do a good job in training, as if our ranked list is bad, our threshold tuning will be less effective
* Threshold tuning stage
  * take the ranked list and adjust the threshold until we maximize our goal (expected value, or other class-imbalance sensitive goals)
  * does this stage ever impact the training stage?

Questions
* what is the interplay between grid search and 


(what-is-expected-value)=
## Expected Value

https://www.svds.com/the-basics-of-classifier-evaluation-part-1/


* expected value == [ possible outcome 1 ] x [ weight ]
* weight == probability( occurrence )
* EV == p( outcome1 ) x v( outcome1 ) + p( outcome2 ) x v( outcome2 ) ...
  * outcome-N: possible decision outcome
  * p( outcome-N ): probability
  * v( outcome-N ): value
  * the probabilities can often be estimated from the data
  * the business values need to input from other ways (cost benefit matrix)

### Expected Value to Frame Classifier Use

* Expected benefit of targetting == Pr(x) x Vr + (1 - Pr(x)) x Vnr
  * x: feature input vector for model input
  * Pr(x): probability of response based on model and input x
  * Vr: value of the response of the offer
  * Vnr: value of no response (cost of offer)
* Example
  * our Vr == \$99
  * our Vnr == \$1 (or -\$1 as a cost)
  * do we target customer denoted by the x set of attributes?
  * mathematically: Pr(x) x \$99 - [1 - Pr(x)] x \$1
    * rearranged: Pr(x) > 0.01
  * we should target the consumer as long as the estimated probability of response is greater than 1%

### Using Expected Value to Frame Classifier Evaluation

* shifting mindset from a single decision to collections of decisions
* goal is to evaluate if one model is better than other models
* Expected Value Calculation
  * Take the Confusion Matrix -> normalize to "expected rates" (matrix of probabilities)
  * multiply the matrix times a cost/benefit matrix
  * we take the counts in the Confusion Matrix for each of the 4 entries and divide them by the total records in the test dataset
    * estimated probabilities == count( hypothesized, actual ) / [total instances]


### Rates or "Estimated Probabilities"

* Calculating probability: divide the number of occurences of an event by the total number of events
* rate: we calculate a TP Rate or a TN Rate as:
  * TP Rate == TP / Total Instances
* this is also known as the estimated probability of a TP
* Further Notes
  * wikipedia: "Sensitivity (True Positive Rate) refers to the proportion of those who have the condition (when judged by the ‘Gold Standard’) that received a positive result on this test."


### Factoring Out Class Priors

* TODO: deal with the version of the profit curve that considers class priors -- which version are they using later in the book?



(what-is-cost-benefit-matrix)=
## Cost Benefit Matrix


```python
# Define cost-benefit matrix with input from business managers, other stakeholders, etc.
# REDO THIS
costbenefit_mat = np.array([[0, 0],
                            [-150, 175]])
```


### Costs and Benefits

* to compute expected profit, we need the cost and benefit values that go with each p( hypothesized, actual ) pair in the confusion matrix
* these will form the cost benefit matrix that has the same matrix-structure (rows, columns) as the Confusion matrix
* In the table below we break down how [correct, incorrect] classifications match up to different cost-benefit cells

<table>
  <th>
    <td></td>
    <td></td>
    <td colspan="2">Actual</td>
    <td></td>
  </th>

  <tr>
    <td> </td>
    <td> </td>
    <td>p</td>
    <td>n</td>
  </tr>

  <tr>
    <td>predicted</td>
    <td>Y</td>
    <td style="border: 1px solid;">b(Y,p)</td>
    <td style="border: 1px solid;">c(Y,n)</td>
  </tr>

  <tr>
    <td></td>
    <td>N</td>
    <td style="border: 1px solid;">c(N,p)</td>
    <td style="border: 1px solid;">b(N,n)</td>
  </tr>


</table>

* correct classifications
  * TP: b(Y,p)
  * TN: b(N,n)
* incorrect classifications
  * FP: c(Y,n)
  * FN: c(N,p)
* we need to calculate the estimated probabilities for each of the 4 "decision pairs" from the data
  * estimated probability: count of each decision pair divided by the total number of examples
* while we can estimate the probabilities, we have to manually build the cost benefit matrix (next section)

### Cost Benefit Matrix

* we want to model a cost per action metric (Cost per Action)
* then we want to account for the benefit of the action if the outcome is as we hope (Value of TP)
* Predictions vs Actual
  * TP: saying the action will be true, and it is actually true
  * TN: saying the action will not occur, and the outcome does not occur
  * FP: saying the action will be true, and the outcome does actually occur
  * FN: saying the action will not be true, and the outcome actually does occur


In the table below we should the hypothetical scenario where a manufacturing company is making



| Outcome | Cost | Benefit | Outcome Value |
|---------|------|---------|---------------|
| TP      | 60   | 2500    | 2440          |
| TN      | 0    | 0       | 0             |
| FP      | 60   | 0       | -60           |
| FN      | 0    | 0       | 0             |

Rows that have a positive outcome value show how the outcome is a net benefit in the valuation of a model.

Note: mathematically there is no difference between a benefit and a cost in this context. The only difference is the sign of the outcome value. From this perspective, we can consider all outcome values as "benefits" where costs are considered "negative benefits".

This gives us a single function: benefit( predicted, actual) [TODO: more narrative here ]


<table>
  <th>
    <td></td>
    <td></td>
    <td colspan="2">Actual</td>
    <td></td>
  </th>

  <tr>
    <td> </td>
    <td> </td>
    <td>p</td>
    <td>n</td>
  </tr>

  <tr>
    <td>predicted</td>
    <td>Y</td>
    <td style="border: 1px solid;">$2440</td>
    <td style="border: 1px solid;">-$60</td>
  </tr>

  <tr>
    <td></td>
    <td>N</td>
    <td style="border: 1px solid;">$0</td>
    <td style="border: 1px solid;">$0</td>
  </tr>


</table>

Now let's take the cost benefit matrix and use it in an expected profit calculation


(what-are-profit-curves)
## Profit Curve



* Inputs
  * model object
  * cost benefit matrix in the same format as the confusion matrix above
  * predicted probabilities
  * actual labels
* 

the calculation for the profit curve is:


```python
profit = sum( sum( confusion_matrix * cost_benefit_matrix ) ) / len( examples )
```

<!--

(what-are-frequency-distributions)
## Frequency Distribution

[ todo ]


(what-are-frequency-histograms)
## Frequency Histograms

[ todo ]


(what-are-bias-and-variance)
## Bias and Variance

[ todo ]


(what-are-validation-and-learning-curves)
## Validation vs Learning Curves

[ todo ]

https://vitalflux.com/validation-curves-explained-python-sklearn-example/

"validation curves helps in assessing the model bias-variance issue (underfitting vs overfitting problem)  against the model parameters"

"A learning curve plots the score over varying numbers of training samples, while a validation curve plots the score over a varying hyper parameter."

(what-is-null-hypothesis)=
## Null Hypothesis

[ todo ]


(what-is-f-stat)=
## F-stat

[ todo ]


(what-are-p-values)=
## P-Values

[ todo ]


(what-is-calibration)=
## Calibration

[ todo ]

(what-is-t-test)=
## T-Tests

[ todo ]

-->