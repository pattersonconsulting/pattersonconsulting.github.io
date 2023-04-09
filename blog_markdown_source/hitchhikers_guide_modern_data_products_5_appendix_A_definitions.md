---
layout: post
published-on: March 27th 2023
author: Josh Patterson
title: Appendix A - Definitions
subtitle: The Hitchhiker's Guide To Building Modern Data Products
description: In this post we'll .....
keywords: snowflake, snowpark, automl, AutoGluon, pandas, dataframe, whl, pip, anaconda, dependency
meta_og_image: pct_autogluon_dep_og_card.jpg
---

# Introduction

Purpose of this series:

> To develop a clear step-by-step process to design and operate data infrastructure for your data product.

The intended audience for this series is:

> Individual researchers, data scientists, and then also enterprise data teams as well

Series:

* [Prologue (Don't Panic)](hitchhikers_guide_modern_data_products_1_prologue.html)
* [The Evolution of Modern Data Platforms](hitchhikers_guide_modern_data_products_2_evolution_data_platforms.html)
* [Revisting The Lab and the Factory](hitchhikers_guide_modern_data_products_3_lab_and_factory_redux.html)
* [A Methodology for Building Data Products](hitchhikers_guide_modern_data_products_4_methodology_for_data_products.html)
* [Appendix A: Definitions](hitchhikers_guide_modern_data_products_5_appendix_A_definitions.html)

We spend the first 3 posts of this series providing background and definitions to set the stage for our methodology and in part 4 we lay out our step by step process.

# Analytics Terms Definitions

Some good definitions on reddit blog:

https://dataengineering.wiki/FAQ/What+is+the+difference+between+a+Data+Engineer+and+X

## Table

alpha

## View

beta

## Analytics

https://preset.io/blog/introducing-entity-centric-data-modeling-for-analytics/?

### What are 3 Examples of Analytics?

1. a
2. b
3. c

## Data Modeling

> "This is the process of producing a data model, an abstract model to describe the data and relationships between different parts of the data.[27]"

### What are 3 Examples of Data Modeling?

1. a
2. b
3. c

## Data Warehouse

* todo: clearly state the purpose of the data warehouse

## A Data Product

### What are 3 Examples of Data Products?

1. Data for a Business Intelligence Dashboard
2. Aggregated dataset for downstream machine learning
3. Operational Data (todo: differentiate this from BI data)


## Dimensions

## Cubes


## Metrics

## The Kimball Data Warehouse Architecture

# Machine Learning Terms Definitions

## Vectors, Features, and Tensors -- Oh, My

https://stats.stackexchange.com/questions/192873/difference-between-feature-feature-set-and-feature-vector

https://stats.stackexchange.com/questions/351514/usage-of-the-term-feature-vector-in-lindsay-i-smiths-pca-tutorial?rq=1

> A feature vector is a vector that stores the features for a particular observation in a specific order.

> For example, Alice is 26 years old and she is 5' 6" tall. Her feature vector could be [26, 5.5] or [5.5, 26] depending on your choice of how to order the elements. The order is only important insofar as it is consistent.

> A feature set is a set of all the attributes that you're interested in, e.g. height and age.

> The implicit assumption when using this terminology is that your data is tabular -- somehow, you have chosen to represent it as a "flat", matrix-like format. But non-tabular data formats, like network graphs, video, audio, images, binary data sequences, ... these all require some amount of engineering to represent as feature vectors.

ISLR Book

https://www.statlearning.com/

## Vector

asda


## Feature

> "In machine learning and pattern recognition, a feature is an individual measurable property or characteristic of a phenomenon.[1] Choosing informative, discriminating and independent features is a crucial element of effective algorithms in pattern recognition, classification and regression. Features are usually numeric, but structural features such as strings and graphs are used in syntactic pattern recognition. The concept of "feature" is related to that of explanatory variable used in statistical techniques such as linear regression."

 Bishop, Christopher (2006). Pattern recognition and machine learning. Berlin: Springer. ISBN 0-387-31073-8.


## Feature Vector

> "In pattern recognition and machine learning, a feature vector is an n-dimensional vector of numerical features that represent some object. Many algorithms in machine learning require a numerical representation of objects, since such representations facilitate processing and statistical analysis."

> "The vector space associated with these vectors is often called the feature space. In order to reduce the dimensionality of the feature space, a number of dimensionality reduction techniques can be employed."

Many times in ML literature the term feature vector is used differently:

https://stats.stackexchange.com/questions/351514/usage-of-the-term-feature-vector-in-lindsay-i-smiths-pca-tutorial?rq=1

## Feature Construction

> "Higher-level features can be obtained from already available features and added to the feature vector; for example, for the study of diseases the feature 'Age' is useful and is defined as Age = 'Year of death' minus 'Year of birth' . This process is referred to as feature construction.[2][3] Feature construction is the application of a set of constructive operators to a set of existing features resulting in construction of new features."

Attributes?

## Feature Engineering

> "Feature engineering or feature extraction or feature discovery is the process of using domain knowledge to extract features (characteristics, properties, attributes) from raw data.[1] The motivation is to use these extra features to improve the quality of results from a machine learning process, compared with supplying only the raw data to the machine learning process."

https://en.wikipedia.org/wiki/Feature_engineering


## Data Engineering

abc

### What are 3 Examples of Data Engineering?


abc

## Machine Learning Modeling

### What are 3 Examples of Machine Learning Modeling?

1. a
2. b
3. c


## Machine Learning Model Inference

## Artificial Intelligence

* marketing


