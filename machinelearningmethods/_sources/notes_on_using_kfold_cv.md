# Notes on Using K-Fold Cross Validation

We use K-fold cross-validation to compute point estimates of the models performance on unseen data ("out of sample data") for a given goodness of fit metric (MSE, Precision Recall AUC, etc). In this article we use the term "error" as a simple placeholder for the given metric to compute.

To evaluate a modeling workflow on building a model for the dataset with cross validation we average the metric (e.g., "error") for each of the K-fold runs of the training routine. The final averaged metric is our final "score" estimation for how well the model will perform on the population of unseen data.

In published literature five-or-tenfold cross-validation are recommended as good settings for K (Breiman and Spector (1992) and Kohavi (1995)).

Although we may use cross validation to estimate how well our model workflow performs, we do not want to choose the best performing fold in the group of K-folds as our final model. Cross validation let's us find the "best workflow" (data engineering, choice of model, hyperparameters, etc) to fit the dataset. Once we have an estimation of our models performance via cross-validation, we discard the K-fold temporary models and we use the same workflow to train a new model on ALL of the data we have to build the model to use in an application.

Relevant Resources:

* https://web.stanford.edu/~hastie/ElemStatLearn/
