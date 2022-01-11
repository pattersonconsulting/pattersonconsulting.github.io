# A ML Workflow for Dealing with Class Imbalance in Tabular Data

What is our goal with this project? To maximize line of business value

What contributes to business success/value?

Model accuracy
Tuning the model decision threshold based on the class distribution and cost matrix

Foundationally we want to collect data about how well a model learns the structure in the general population of data by looking at how the model makes predictions. Based on this data we build a confusion matrix for this version of the model.

Out of the box models assume a 50/50 (binary classification model) decision boundary. This built-in assumption is based on the idea that the class priors are all balanced. In practice, this is not true of most datasets.


Class imbalance tends to come up in most tabular datasets in the wild

we care about it because...

I wanted to put this article together because I felt many workflows on class imbalance methods were either too simplistic (e.g., "downsampling") or were tied to some specific problem implementation (what do we mean here?)

This article is meant to take information from my article on [Exploratory Data Analysis Workflows](exploratory_data_analysis_workflows.md) and then segue into the article on [Forecasting the Business Value of a Model](forecasting_model_value.md). Together, these 3 articles should allow you to find solid ground approaching imbalanced data problems such as

* predictive maintenace
* predicting disease
* churn predicton (note: generally modeled as survivor analysis)
* click prediction
* fraud detection
* anomaly detection


The previous (companion) article on [EDA workflows](exploratory_data_analysis_workflows.md) will provide you with the understanding you need to make decisions about how to customize and run the workflow in this article.


(intro-class-imbalance-workflow)=
## Introduction and Motivations


> Research on imbalanced classes often considers imbalanced to mean a minority class of 10% to 20%. In reality, datasets can get far more imbalanced than this. Here are some examples: About 2% of credit card accounts are defrauded per year1. (Most fraud detection domains are heavily imbalanced.) Medical screening for a condition is usually performed on a large population of people without the condition, to detect a small minority with it (e.g., HIV prevalence in the USA is ~0.4%). Disk drive failures are approximately ~1% per year. The conversion rates of online ads has been estimated to lie between 10-3 to 10-6. Factory production defect rates typically run about 0.1%.

> In the real world, imbalanced domains are the rule, not the exception! Outside of academia, I have never dealt with a balanced dataset. The reason is fairly straightforward. In many cases, machine learning is used to process populations consisting of a large number of negative (uninteresting) examples and a small number of positive (interesting, alarm-worthy) examples.

> Examples of such domains are fraud detection (1% fraud is a huge problem; 0.1% is closer), HIV screening (prevalence in the USA is ~0.4%), predicting disk drive failures (~1% per year), click-through advertising response rates (0.09%), factory production defect rates (0.1%) — the list goes on. Imbalance is everywhere.

> That said, here is a rough outline of useful approaches. These are listed approximately in order of effort: Do nothing. Sometimes you get lucky and nothing needs to be done. You can train on the so-called natural (or stratified) distribution and sometimes it works without need for modification. Balance the training set in some way: Oversample the minority class. Undersample the majority class. Synthesize new minority classes. Throw away minority examples and switch to an anomaly detection framework. At the algorithm level, or after it: Adjust the class weight (misclassification costs). Adjust the decision threshold. Modify an existing algorithm to be more sensitive to rare classes. Construct an entirely new algorithm to perform well on imbalanced data.



[ todo: why do we care about grid search? ]

we dont know entirely which threshold we're going to use on the ROC curve, so building models that are optimized for our task as best as we can is a key focus for our modeling workflows

[ todo: why do we care about specific eval metrics? ]

> Don’t use accuracy (or error rate) to evaluate your classifier! There are two significant problems with it. Accuracy applies a naive 0.50 threshold to decide between classes, and this is usually wrong when the classes are imbalanced. Second, classification accuracy is based on a simple count of the errors, and you should know more than this. You should know which classes are being confused and where (top end of scores, bottom end, throughout?).

https://www.svds.com/tbt-learning-imbalanced-classes/

```{admonition} Segue

> "When you get probability estimates, don’t blindly use a 0.50 decision threshold to separate classes. Look at performance curves and decide for yourself what threshold to use (see next section for more on this). Many errors were made in early papers because researchers naively used 0.5 as a cut-off.
"
https://www.svds.com/tbt-learning-imbalanced-classes/
```

(ovr-class-imbalance-workflow)=
## Overview of Our Class Imbalance Modeing Workflow

[ todo: what are we going to do here? whats our general workflow? ]

  
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


### Threshold Tuning

> "Nevertheless, many machine learning algorithms are capable of predicting a probability or scoring of class membership, and this must be interpreted before it can be mapped to a crisp class label. This is achieved by using a threshold, such as 0.5, where all values equal or greater than the threshold are mapped to one class and all other values are mapped to another class."

https://machinelearningmastery.com/threshold-moving-for-imbalanced-classification/

https://developers.google.com/machine-learning/crash-course/classification/precision-and-recall


[ HOW do we delineate "threshold tuning" from "model training"? ]

* how do we show when one starts and the other stops???

Key steps in tuning a threshold

* "The default threshold for interpreting probabilities to class labels is 0.5, and tuning this hyperparameter is called threshold moving.""
* "How to calculate the optimal threshold for the ROC Curve and Precision-Recall Curve directly."
* "How to manually search threshold values for a chosen model and model evaluation metric."

outline

* most classification models can output labels or probabilities for a given label
* we use a threshold (default: 0.5) to divide the probability value into 1 of 2 classes
* in many cases, such as under severe class imbalance, or a specific business situation, this default threshold works poorly for our business case
* while there are many methods for dealing with class imbalance in machine learning, the most direct approach for optimizing the model for a business goal is to optimize the threshold informed by business costs and benefits

Reasons to choose different threshold than default:

* using ROC Curves and probabilites
  * ROC curves are useful when analyzing the predicted probabilities of a model
  * ROC AUC scores are useful for selecting the best model
  * we want to choose a threshold on the ROC Curve that gives us the best tradeoff between TPR and FPR
* PR and PR-AUC can be used similarly
  * but we still need to choose the best threshold
* TPs and FPs, etc, may all have different associated costs ("cost benefit matrix")
  * need to choose the best threshold for maximizing business case profit

we need to search the range of threshold values and find the best one for our use case or business needs

(modeling-class-imbalance-workflow)=
## Building a Group of Models with Grid Search

what are we doing and where do we start?

(baseline-class-imbalance-workflow)=
### Baselining Our Data with a Simple Model

we use DummyModel from sklearn

it will pick the majority class for every prediction

its accuracy will be high, but in this case this is misleading

```{attention} Accuracy fails with imbalanced datasets where the distribution of examples across the classes is not equal. accuracy is often used earlier in machine learning when dealing with examples where the distribution of the classes is equal, so that's why practitioners tend to start with it as an evaluation metric
```


> Achieving 90 percent classification accuracy, or even 99 percent classification accuracy, may be trivial on an imbalanced classification problem. One limitation of these metrics is that they assume that the class distribution observed in the training dataset will match the distribution in the test set and in real data when the model is used to make predictions. This is often the case, but when it is not the case, the performance can be quite misleading

"even with slightly skewed class distributions accuracy can be usefl metric however, in practice many practical problems in machine learning deal with highly imbalanced datasets"

```{admonition} Segue
[ segue: if not accuracy, then what do we use ]
```


(select-metric-class-imbalance-workflow)=
### Select an Evaluation Metric to Guide Grid Search

Accuracy doesnt work when evaluating classifiers built from imbalanced datasets

> Unlike standard evaluation metrics that treat all classes as equally important, imbalanced classification problems typically rate classification errors with the minority class as more important than those with the majority class. 

> As such performance metrics may be needed that focus on the minority class, which is made challenging because it is the minority class where we lack observations required to train an effective model.


> For imbalanced classification problems, the majority class is typically referred to as the negative outcome (e.g. such as “no change” or “negative test result“), and the minority class is typically referred to as the positive outcome (e.g. “change” or “positive test result“).

* Majority Class: Negative outcome, class 0.
* Minority Class: Positive outcome, class 1.

For the purposes of this modeling exercise we denote a prediction of “failure” with numeric value 1 in the “Failure” column.



this is the tricky part, and this is where we need specific information from the line of business

[ discuss: predictive maintenance doesnt work the same across companies, nor industries ]

[ discuss: what are we most sensitive to? ]

> The two-dimensional graphs in the first bullet above are always more informative than a single number, but if you need a single-number metric, one of these is preferable to accuracy:

> The Area Under the ROC curve (AUC) is a good general statistic. It is equal to the probability that a random positive example will be ranked above a random negative example.
> The F1 Score is the harmonic mean of precision and recall. It is commonly used in text processing when an aggregate measure is sought.
Cohen’s Kappa is an evaluation statistic that takes into account how much agreement would be expected by chance.

> Unlike the ROC Curve, a precision-recall curve focuses on the performance of a classifier on the positive (minority class) only.

> There are two groups of metrics that may be useful for imbalanced classification because they focus on one class; they are

* Sensitivity-specificity
  * G-Mean
* Precision-recall

### The Role of EDA in Choosing an Evaluation Metric

todo

### Choosing an Evaluation Metric



[ how do we choose one of these? ]

> Examples of measures that are a combination of precision and recall are the F-measure (the weighted harmonic mean of precision and recall), or the Matthews correlation coefficient, which is a geometric mean of the chance-corrected variants: the regression coefficients Informedness (DeltaP') and Markedness (DeltaP).

[ explain: PR-AUC ]

Making a Decision on which eval to use:

Is the positive class more important?
Use Precision-Recall AUC

Are both classes important?
Use ROC AUC


What about other options?
* Use Brier Score and Brier Skill Score
* f1-measure, f2-measure, etc
* G-Mean


> The two-dimensional graphs in the first bullet above are always more informative than a single number, but if you need a single-number metric, one of these is preferable to accuracy:

> The Area Under the ROC curve (AUC) is a good general statistic. It is equal to the probability that a random positive example will be ranked above a random negative example.
> The F1 Score is the harmonic mean of precision and recall. It is commonly used in text processing when an aggregate measure is sought.
Cohen’s Kappa is an evaluation statistic that takes into account how much agreement would be expected by chance.


  <!-- --------------------------------- START: Sidebar --------------------------------- -->
  <div style=" border: 1px solid; padding: 12px; padding-left: 18px; margin-left: 6px; font-size: 12px; background-color: #eeeeee;">
    <h4>Understanding Evaluation of Machine Learning Models</h4>
    <p>
      Machine learning has its own metrics that are useful when evaluating the performance of a model. We share some relevant measures and their definitions below.
    </p>
    <p>
        <table>
          <thead>
            <tr>
              <th>Metric</th>
              <th>Meaning</th>
            </tr>
          </thead>
          <tbody>
            <tr><td>True Positive (TP)</td><td>samples that were correctly classified</td></tr>
            <tr><td>True Negative (TN)</td><td>samples that were correctly classified</td></tr>
            <tr><td>False Positive (FP)</td><td>samples that were <span style="color: red;">incorrectly</span> classified</td></tr>
            <tr><td>False Negative (FN)</td><td>samples that were <span style="color: red;">incorrectly</span> classified</td></tr>
            <tr><td>Accuracy</td><td>percentage of examples correctly classified; Note: <i>accuracy is not a good way to evaluate a classifier trained on an imbalanced dataset</i></td></tr>
            <tr><td>Precision</td><td>percentage of predicted positives that were correctly classified: TP / (TP + FP)</td></tr>
            <tr><td>Recall</td><td>percentage of actual positives that were correctly classified: TP / (TP + FN)</td></tr>
            <tr><td>Sensitivity</td><td>refers to the <b>true positive rate</b> and summarizes how well the positive class was predicted (same formula as Recall): TP / (TP + FN)</td></tr>
            <tr><td>Specificity</td><td> the complement to sensitivity, or the <b>true negative rate</b>, and summarises how well the negative class was predicted: TP / (FP + TN)</td></tr>
            <tr><td>F-Measure</td><td>a single score that seeks to balance both concerns of precision and recall: (2 * Precision * Recall) / (Precision + Recall)</td></tr>
            <tr><td>Area Under the Curve (AUC)</td><td>refers to the Area Under the Curve of a Receiver Operating Characteristic curve (ROC-AUC)</td></tr>
          </tbody>
        </table>
    </p>
    <div style="border: 1px solid #cccccc; width: 440px; padding: 6px; text-align: center;">
      <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/5a/Sensitivity_and_specificity_1.01.svg/683px-Sensitivity_and_specificity_1.01.svg.png" style="width: 380px; margin: 2px; margin-bottom: 12px;"/>
      <p>Image Source: Wikipedia article on <a href="https://en.wikipedia.org/wiki/Sensitivity_and_specificity">Sensitivity and Specificity</a>
      </p>
    </div>
  </div>
  <!-- --------------------------------- END: Sidebar --------------------------------- -->


(select-models-class-imbalance-workflow)=
### Select a Group of Promising Model Types for Grid Search

why do we care about grid search?

we're searching not only multiplde model types, but also parameters within those model types

we want to start with some model architectures that are known to perform well:

* Logistic Regression
* Neural network
* Gradient Boosting Classifier
* Random Forests
* xgBoost

For each of these model architectures we'll scan regions of hyperparameter space to get a general idea of how well they will work for a given problem

once we find a few good models, we'll narrow our focus to tuning those 2-3 models

(run-gridsearch-class-imbalance-workflow)=
### Run Grid Search



Plot the distribution of accuracies of the models



[ TODO: how do we handle cross validation in this context? ]

Take the top 3 models
* examine the confusion matrix of each of the [best] models
* Manually check the [ Train, Validation, Test ] scores for each one

optionally: do further feature analysis here
* look at feature importance for random forests
* for tree-based methods, use Recursive feature elimination and Cross Validation selection (RFECV)
* Principal Component Analysis


[ TODO: how do we make the case to transition from analyzing performance on validation data to analyzing performance on test data? ]


### Select the Top 3 Models for Refinement

compare scores, select top model based on scoring parameter ("average_precision")

Fine tune each model by hand a bit -- this is where we'd do feature selection further (whereas before we'd use all the features)

### Perform Feature Selection

[ here we analyze which features work best for which models ]

> "A benefit of using ensembles of decision tree methods like gradient boosting is that they can automatically provide estimates of feature importance from a trained predictive model."

> "Tree based algorithms like random forest, gradient boosting decision tree and even vanilla decision tree give us useful information about feature importance when we fit the classifier. However we are not entirely sure on the number of features to retain (or feature importance threshold). Recursive feature elimination and Cross Validation selection (RFECV) can help us to quantitatively decide the number of features to retain based on the highest cross validation score we get."

* random forest, gradient boosting decision tree, decision tree: RFECV
* xgboost: plot_importance() method
* NNs: just let network learn features
* all: PCA

### Check Learning Curves

Calculate "Learning Curves" for each model

Why? examine bias / variance of models

[ helps understand overfitting ] 


(eval-gridsearch-class-imbalance-workflow)=
### Evaluate the Trained Classifiers


Model selection conclusion

* show the best N models used (with hyperparams)
  * show the features used
  * show validation [score]
  * show test [score]

[ more here ]




### Visually Evaluating a Classifier
[ discuss: when to use ROC Curves, when to use PR Curves ]

* what is a ROC curve best for?
* what is a PR curve best for?

> "ROC Curves summarize the trade-off between the true positive rate and false positive rate for a predictive model using different probability thresholds."

> "Precision-Recall curves summarize the trade-off between the true positive rate and the positive predictive value for a predictive model using different probability thresholds."

> "ROC curves are appropriate when the observations are balanced between each class, whereas precision-recall curves are appropriate for imbalanced datasets."


## Threshold Moving and Model Evaluation

> "One last thing to note is that when we performed the Grid Search, we selected the best model using average_precision , which is important. If we had used the f1 score then for example, we would have relied on the default threshold only and therefore could have missed a combination of hyperparameters that yield a better f1 score at a different threshold. Therefore, I made sure to select the model using a metric agnostic to the threshold, and only then tuned the threshold."

https://towardsdatascience.com/how-to-add-decision-threshold-tuning-to-your-end-to-end-ml-pipelines-7077b82b71a

Working with Average Precision

https://sanchom.wordpress.com/tag/average-precision/


[ explain: the default threshold concept, the inherent assumptions, and how this breaks with class imbalance ]

### Rank with Classifier Probabilities

[ we want to rank here, so we need the probabilities from the model ]

### Thresholds and Confusion Matricies

[ discuss: each threshold point on the ROC curve is a new Confusion Matrix ]

[ how do we think of ROC curves in the context of using only the 50-50 threshold? ]

### Choosing a Threshold on the Profit Curve

[ explain ]

## Further Reading

* Learning from Imbalanced Data Sets
  * https://www.amazon.com/Learning-Imbalanced-Data-Alberto-Fern%C3%A1ndez/dp/3319980734/ref=as_li_ss_tl?keywords=Learning+from+Imbalanced+Data+Sets&qid=1568679479&s=books&sr=1-1&linkCode=sl1&tag=inspiredalgor-20&linkId=214f8d8144c94e7f48543e0200abdbdf&language=en_US

* Machine Learning from Imbalanced Datasets 101
  * https://www.aaai.org/Papers/Workshops/2000/WS-00-05/WS00-05-001.pdf
