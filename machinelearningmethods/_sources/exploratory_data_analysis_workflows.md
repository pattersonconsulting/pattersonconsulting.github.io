# Exploratory Data Analysis Workflows

This article is meant to provide a generalized exploratory data analysis workflow. It's a great workflow to get you started with EDA. In some cases you'll also want to consider variations on this workflow to better accomodate different data challenges.

This article is meant to be a precursor to my [article on a workflow for dealing with class imbalance in tabular data](methods_class_imbalance.md).


(what-is-eda)=
## What is Exploratory Data Analysis (EDA)?

EDA is...

> Exploratory Data Analysis (EDA) is an approach to analyzing data. It’s where the researcher takes a bird’s eye view of the data and tries to make some sense of it. 
> It’s often the first step in data analysis, implemented before any formal statistical techniques are applied. Although specific statistical techniques can be used, like creating histograms or box plots, EDA is not a set of techniques or procedures; 

> the Engineering Statistics Handbook calls EDA a “philosophy.” EDA is considered by some to be more of an art form than a science.

> Exploratory data analysis is a complement to inferential statistics, which tends to be fairly rigid with rules and formulas. 
> EDA involves the analyst trying to get a “feel” for the data set, often using their own judgment to determine what the most important elements in the data set are. 
> For example, multidimensional scaling is an EDA that uses visual representations of distances or similarities between sets of objects; It’s up to the user to interpret exactly what the distances represent.


Segue? EDA informs the modeling process in the following ways...

(purpose-of-eda)=
### The Purpose of EDA

"It’s always good to have some hypotheses in mind before diving into modeling, and exploratory analysis can help in generating them."

The purpose of exploratory data analysis is to:

> Check for missing data and other mistakes.
> Gain maximum insight into the data set and its underlying structure.
> Uncover a parsimonious model, one which explains the data with a minimum number of predictor variables.
> Check assumptions associated with any model fitting or hypothesis test.
> Create a list of outliers or other anomalies.
> Find parameter estimates and their associated confidence intervals or margins of error.
> Identify the most influential variables.

> ...understand the objectives of EDA as such:

> To gain an understanding of data and find clues from the data,
> -- to formulate assumptions and hypothesis for our modelling; and
> -- to check the quality of data for further processing and cleaning if necessary.
> To better illustrate the concept of EDA, we shall be using the Rossmann store sales “train.csv” data from Kaggle. Keeping in mind that the problem statement is to forecast store sales, our EDA objectives are, therefore:
> -- To check for features that can help in forecasting sales; and
> -- To check for anomalies or outliers that may impact our forecasting model.


(data-cleaning-guiding-principles)=
## Data Cleaning Guiding Principles

> Using three basic rules of thumb can help you avoid incorrectly making claims about your data:

> Look at your data and think about what it is you want to know. Do you want to prove that the Earth is round? Or do you want to prove that the Earth has a circumference? Framing this question is what we call stating the hypothesis.

>Estimate a Central Tendency for your Data. Examples of measures of central tendency are the mean and median. Which one you use will depend on your hypothesis in Step 1. For example, if you wanted to prove the Earth was round, you might choose to look at the average volume, or the average circumference.

> Consider the exceptions to the central tendency. If you’ve measured the average, look at the figures that are not average. If you’ve measured a median, look at the figures that don’t meet that expectation. Exceptions can help you spot problems with your conclusion. A simple example: your child’s average score in school is 70. Not bad, right? But if you look at the exceptions, you might find they are getting 100 in three classes (great!) and 40 in three other classes (uh oh). In this case, the average is completely misleading.


### Pitfalls of EDA

> Why do so many cases of data analysis end with faulty claims? One of the main reasons is that analyzing data is a complicated and tedious process. It’s never as easy as plugging numbers into a computer. Some issues that can lead to faulty data analysis include:

>Not having the right analysis skills.
> Using the wrong tools to analyze data. For example, using a z score when your data doesn’t have a normal distribution.
> Letting bias influence your results.
> Not figuring out statistical significance.
> Incorrectly stating the null hypothesis and alternate hypothesis.
> Using misleading graphs and charts.



(our-eda-workflow)=
## A Generalized EDA Worfklow

[ Formulate this like an SoW ]

State: What is our starting Point

State: What is process

State: What is our exit / completion / acceptance state?


* Preliminary data analysis
  * Check shape, see if any extra data is included
  * Change target variable into right format if needed
  * Drop unneeded columns
  * Check columns for NA values
    * Get counts of NAs
    * For columns with lots of NAs: drop column
    * For columns with few NAs: replace with median or mean
      * Use variable boxplots to decide which method of replacement
* Split data on dependent / y column
  * Calculate the mean of all features for both classes
  * Plot the frequency distributions of the features to visualize which features capture the most variability
* Compare distributions of features
  * Some features will have different distributions per class
  * Some features will not
  * Features with different distributions will be better predictors of the dependent variable in our model
  * Continue on with all of the features (for now)

[ TODO : check against these steps ]

1. Preview data
2. Check total number of entries and column types
3. Check any null values
4. Check duplicate entries
5. Plot distribution of numeric data (univariate and pairwise joint distribution)
6. Plot count distribution of categorical data
7. Analyse time series of numeric data by daily, monthly and yearly frequencies



### Preliminary Data Analysis: Correlation

> James: "The first thing I like to do when analyzing my variables is visualizing it through a correlation matrix because it’s the fastest way to develop a general understanding of all of my variables. A correlation matrix is a table that shows the correlation coefficients between many variables. 
I used sns.heatmap() to plot a correlation matrix of all of the variables in the used car dataset."

James: pair plots between each independent and the dependent 
* to see how they move together... 
* and if I have categorical data it gets more complex
* as I might want pairs for each category
* this gets impossible with 10 categorical variables... too many slices

Other notes:

* Check shape, see if any extra data is included
* Change target variable into right format if needed
* Drop unneeded columns
* Check columns for NA values

### Split Off Label or Dependent Variable Column

* Calculate the mean of all features for both classes
* Plot the frequency distributions of the features to visualize which features capture the most variability


### Compare distributions of features

* Some features will have different distributions per class
* Some features will not
* Features with different distributions will be better predictors of the dependent variable in our model
* Continue on with all of the features (for now)


## Variable Analysis Methods

In this section we document ways to analyze correlation between different types of variables

### Numeric vs Numeric

todo

### Numeric vs Categorical

todo

### Categorical vs Categorical

todo

### HexPlots to Combat Overplotting

todo


### Using T-Tests to Check Distributions

todo: T-test for Difference in Means

## EDA Visualization Methods

[ when and where to use each? ]

* frequency histogram
* pair plots
* correlation matrix
* box plots

## Working Conclusions

* if you have two "independent" variables that are not independent but rather are correlated with each other 
  * they will each show up lower levels of significance than they would if the other correlated variable were removed. One variable "steals" prediction from the other
* With NNs
  * Throw all features in there, let it sort them out
  * But we lose the ability to interpret the output
* With linear models
  * Need to do some feature selection to get better results
* Models we’ll try
  * Dummy Classifier (sklearn)
  * Logistic regression
  * Neural Network
  * Gradient Boosting Decision Tree
  * Random Forest Classifier

## Reference Topics and More Reading

* Boxplot Analysis
* The Normal Distribution
* Analyzing Distribution Shape
* Zero Mean and Unit Variance
* Class Priors
* P-Values and Coefficients in Regression
* F-stat
* T-tests


Here is a [reference to the intro](intro.md). Here is a reference to [](what-is-eda).
