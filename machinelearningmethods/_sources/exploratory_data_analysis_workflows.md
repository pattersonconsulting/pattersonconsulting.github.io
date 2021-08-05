# Exploratory Data Analysis Workflows

This is some sample text.

(what-is-eda)=
## What is Exploratory Data Analysis (EDA)?


(purpose-of-eda)=
## The Purpose of EDA

"It’s always good to have some hypotheses in mind before diving into modeling, and exploratory analysis can help in generating them."


(data-cleaning-guiding-principles)=
## Data Cleaning Guiding Principles




(our-eda-workflow)=
## A Generalized EDA Worfklow


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
* Split data into training, validation, test sets
* Separately, look at the distribution of classes in our dataset
  * Apply a dummy classifier to give us a baseline (e.g., “pick largest class”)
* Normalize the features
* Train multiple classifiers
  * Tune the top 2-3 classifiers
* For NNs / AutoKeras
  * Use all features
* For LR, GB, RF
  * Perform feature selection
    * how? 
    * What is methodology here?
  * Feature selection
    * How is EDA information used to do feature selection?
    * How are preliminary modeling results used to do feature selection?


### Working Conclusions

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



Here is a [reference to the intro](intro.md). Here is a reference to [](what-is-eda).
