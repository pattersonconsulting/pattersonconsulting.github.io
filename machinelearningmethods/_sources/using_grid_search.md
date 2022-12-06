# Using Grid Search

This article is meant to provide a set of general best practice notes on grid search in machine learning.

(what-is-grid-search)=
## What is Grid Search?

Wikipedia defines [grid search](https://en.wikipedia.org/wiki/Hyperparameter_optimization#Grid_search) as:

> The traditional way of performing hyperparameter optimization has been grid search, or a parameter sweep, which is simply an exhaustive searching through a manually specified subset of the hyperparameter space of a learning algorithm. A grid search algorithm must be guided by some performance metric, typically measured by [cross-validation](https://en.wikipedia.org/wiki/Cross-validation_(statistics)) on the training set or evaluation on a hold-out validation set.

Grid search is useful because normally you'd have to experiment with the hyperparameters manually until you find a great combination of hyperparameter values. 
This ends up being quite time consuming and boring to do manually.

A great method to do grid search is [Scikit-Learn’s `GridSearchCV`](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html). You can set up which hyperparameters you want it to experiment with and what values to try out, and it will use cross validation to evaluate all the possible combinations of hyperparameter values.

## Dataset Management for Grid Search

In grid search workflows, three data sets are commonly used in different stages of the creation of the model: 

1. training
2. validation
3. test sets.

You can see this in machine learning literature such as [Pattern Recognition and Neural Networks](https://www.amazon.com/Pattern-Recognition-Neural-Networks-Ripley/dp/0521460867/ref=as_li_ss_tl?dchild=1&keywords=Pattern+Recognition+and+Neural+Networks&qid=1597365594&sr=8-3&linkCode=sl1&tag=inspiredalgor-20&linkId=2507606de5f6bab2d4dba3e797eac0e2&language=en_US) where training, validation, and test sets are defined as follows:

> * Training set: A set of examples used for learning, that is to fit the parameters of the classifier.
> * Validation set: A set of examples used to tune the parameters of a classifier, for example to choose the number of hidden units in a neural network.
> * Test set: A set of examples used only to assess the performance of a fully-specified classifier.

— Brian Ripley, page 354, [Pattern Recognition and Neural Networks](https://www.amazon.com/Pattern-Recognition-Neural-Networks-Ripley/dp/0521460867/ref=as_li_ss_tl?dchild=1&keywords=Pattern+Recognition+and+Neural+Networks&qid=1597365594&sr=8-3&linkCode=sl1&tag=inspiredalgor-20&linkId=2507606de5f6bab2d4dba3e797eac0e2&language=en_US), 1996


Note that in some literature the terms "validation" and "test" datasets may be used differently or swapped. However, when we use grid search with Cross Validation how we use datasets may change.

## General Workflow for Cross Validation

We use [cross validation](notes_on_using_kfold_cv.md) to estimate the extra-sample ("training data") accuracy (or "error estimate") for a given model. This error metric gives us a good estimation on how well the model will likely perform on data it has not yet seen (e.g., the greater population of data).

[Cross-validation](https://en.wikipedia.org/wiki/Cross-validation_(statistics)) is viewed as being a better way to evaluate a model on validation data than just using a standard single validation data split.

The general workflow for data management in grid search using cross validation is as follows:

* the dataset is split into training and validation datasets.
* cross validation then splits the dataset into k-folds, where commonly a single fold will be "held out" as the test set for the run
* the model is trained on the k-1 other folds of the data, and then tested on the held out fold of data
* the error (or evaluation metric) of the model is the average of the errors of the models trained on each fold
* the final model is trained on all of the folds with the average of the folds' models error as the estimated error for the model
* we can the test the final model against the held out test set, which the model has never seen during training

So while we initially split the data into training and validation datasets, the cross validation workflow creates splits of the training data per run that generates its own test dataset for each run. 

Why do we do this? Because a dataset is a sample of the true population of the data, and any test or validation split of the dataset may not contain a true representation of the distribution of the data. So its pragmatic to split the data in multiple ways, test our model, and then average the errors together to get a better estimate of how the model will perform on data it has yet to encounter.

Note: In some cases you will see workflows that use the final estimated error as the score for the model. However, in other cases you may see a held out "test set" and then also a "validation set" as well, where the validation set is used throughout the experimentation phase of modeling to find good hyperparameters. In today's best practices both methods seem to be acceptable.

## How Does Cross Validation Inform the Grid Search Process?

Cross-validation is known to give a better model error estimate, especially on smaller datasets. Cross-validation creates k sets of validation datasets as part of its workflow and averages the errors for each model produced in the workflow. This average error estimate [represents the error of the model trained on all of the splits at the end of the cross-validation training run](notes_on_using_kfold_cv.md).

Better error estimates for model variations during hyperparameter searches helps the grid search process find better sets of hyperparameters for each model type.

