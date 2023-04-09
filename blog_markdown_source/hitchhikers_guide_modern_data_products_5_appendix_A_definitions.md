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

TODO:
* create a key visualization to represent the core ideas of the page
* this will also serve as the meta og card image

# Roles

## Data Scientist

Reddit:

> Data Scientist: Uses data for more in-depth analysis and visualizations. Typically the work is more research based and sometimes one will work on a product like a machine learning model.

## Data Engineer

DBT definitions of role:

* build custom data integrations
* manage overall pipeline orchestration
* develop and deploy machine learning endpoints
* build and maintain the data platform
* data warehouse performance optimizations

## Analytics Engineer

DBT definitions of role:

* Provide clean, transformed data ready for analysis
* apply software engineering best practices to analytics code (eg., version control, testing, continuous integration)
* maintain data documentation and definitions
* train business users on how to use data visualization tools

Reddit:

> BI Engineer/BI Developer: Uses primarily GUI tools like SSIS to build ETL pipelines, build data models for reports, and even may build the reports themselves. This role is similar in many ways to a Data Engineer but differs in tooling and skillsets required. It is sometimes seen as a pathway to becoming a Data Engineer.

## Data Analyst

DBT definitions of role:

* Deep insights work (e.g., "why did churn spike last month? what are the best acquisition channels?")
* work with business users to understand data requirements
* build critical dashboards
* forecasting

DBT:

https://www.getdbt.com/what-is-analytics-engineering/

> Analytics engineers provide clean data sets to end users, modeling data in a way that empowers end users to answer their own questions. 
> While a data analyst spends their time analyzing data, an analytics engineer spends their time transforming, testing, deploying, and documenting data. 

Analytics engineers apply software engineering best practices like:

* version control
* continuous integration 

to the analytics code base.


Reddit:

> Uses data for basic to medium complexity analysis and builds reports and dashboards. This role will typically require a good grasp of SQL and reporting tools but relies on an engineer for the data.

## Database Administrator

Reddit: 

> Database Administrator: Focuses on making sure the database and infrastructure is available and secure (i.e. backing up data, user management, server usage). They do not typically build within the database itself.



# Analytics Terms Definitions

Some good definitions on reddit blog:

https://dataengineering.wiki/FAQ/What+is+the+difference+between+a+Data+Engineer+and+X

## Table

alpha

## View

beta


## Metrics

For this marketing activity, relevant metrics may be: 

1. Total visitors to the landing page
2. Total visitors broken down by acquisition channel (organic search, referral, cpc, etc.)
3. Total time spent on the page
4. Total form submissions

Again, these are just the data building blocks.


## KPIs

Key Performance Indicators

> Of the metrics, you -- as the marketer or analyst -- need to select those indicators of success. You may not actually care about the total visitors to the landing page, but rather, focus solely on the number of total form submissions (As as all know, more traffic is not always a positive thing, if your visitors aren't taking the action you want them to take). So, your KPIs may break down as follows: 

1. Total form submissions
2. Form conversion rate (submissions/total visits)
3. Form conversion rate broken down by acquisition source

These three metrics are examples of numbers that can be *directly* bound to definitions of success or failure from a business perspective.


### Metrics vs KPIs

> We take these terms seriously because there is real business value tied to each term in different ways. 
> For example, your intern may be qualified to pull metrics from your Google Analytics account, but until those metrics are studied and summarized into business insights, they are nothing more than numbers in a spreadsheet. 
> Similarly, the same intern might be able to pull hundreds of different metrics to report to your senior leadership, but if they aren't aligned behind a set of KPIs, the usefulness of the data will fall short.



## Analytics

https://www.foxgr.com/insights/blog-analytics-vs-metrics-vs-kpis-data-terminology-defined

> Arguably the most misused term of them all, Analytics refers to the systematic study and analysis of data (i.e. Metrics and KPIs). That is, the output of information by a person or system who studied the Metics and worked to extract insights and/or conclusions about what they mean for a business. 

> "Analytics" in their truest form, are not data points that can be pulled directly from an analytics system. 
Rather, they are the interpretations of data that transform numbers and metrics into actionable ideas and insights.

(Refactor)
* Analytics, on the other hand, involves the use of statistical and quantitative methods to identify and interpret patterns and relationships in data. 
* Analytics can be used to answer specific questions or solve particular problems by analyzing data sets and identifying trends, patterns, and correlations that might not be immediately apparent. 
* Analytics can be used to gain insights into customer behavior, improve operational efficiency, and drive business growth.


> Outlining the metrics and KPIs was actually the first step in proper analysis -- it's understanding what you're measuring and why. Next, it's your job as the marketer or analyst to provide context and ultimately draw insights out of the data you see. 

For example:

1. You know that previous landing pages have achieved an average form conversion rate of 6%. How far above or below this benchmark does your current landing page perform?
2. What's your hypothesis for why it is under performing or over performing? What's different about this landing page when compared to your past efforts? Can you narrow down the success/failure to specific content attributes?
3. Based on your study, what do you recommend to change about the current tactic, or what attributes should you include in future tactics to build upon your positive outcomes?


https://preset.io/blog/introducing-entity-centric-data-modeling-for-analytics/?

### What are 3 Examples of Analytics?

1. a
2. b
3. c

## Business Intelligence (BI)

> Business Intelligence (BI) involves the collection, integration, analysis, and presentation of business data in order to inform decision-making. 
> BI tools allow organizations to gather and store data from various sources, clean and transform it into a usable format, and then analyze it to identify patterns and insights. 
> The goal of BI is to provide business leaders with the information they need to make data-driven decisions that improve organizational performance.

### BI vs Analytics

While BI focuses on collecting and presenting data in a way that is easy to understand and use, 
Analytics focuses on using statistical and quantitative techniques to uncover insights and make predictions. 

In short, 
BI provides the information necessary for decision-making, 
while Analytics provides the tools and techniques necessary for analysis and interpretation of that information.


## Data Modeling

> "This is the process of producing a data model, an abstract model to describe the data and relationships between different parts of the data.[27]"

### What are 3 Examples of Data Modeling?

1. a
2. b
3. c

## Data Warehouse

* todo: clearly state the purpose of the data warehouse

## Data Products

* downstream from the core data models of the data warehouse

### What are Some Examples of Data Products?

1. Data for a Business Intelligence Dashboard
2. Aggregated dataset for downstream machine learning
3. Operational Data (todo: differentiate this from BI data)
4. Monitoring Data
5. Data for Exploratory Discovery
6. Analytical Dataset


## Dimensions

## Cubes



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

## Matrix

asdf

## Tensor

asdf

## Feature

> "In machine learning and pattern recognition, a feature is an individual measurable property or characteristic of a phenomenon.[1] Choosing informative, discriminating and independent features is a crucial element of effective algorithms in pattern recognition, classification and regression. Features are usually numeric, but structural features such as strings and graphs are used in syntactic pattern recognition. The concept of "feature" is related to that of explanatory variable used in statistical techniques such as linear regression."

 Bishop, Christopher (2006). Pattern recognition and machine learning. Berlin: Springer. ISBN 0-387-31073-8.

TODO: This book was published in 2006, but when did this term become widely used?

> Features are usually numeric, but structural features such as strings and graphs are used in syntactic pattern recognition. The concept of "feature" is related to that of explanatory variable used in statistical techniques such as linear regression.

### Numeric Feature

A numeric feature can be conveniently described by a feature vector.


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

### Discussion on Feature Engineering

 The definition for "Feature Engineering" is always some form of:


"Feature engineering or feature extraction or feature discovery is the process of using domain knowledge to extract features (characteristics, properties, attributes) from raw data.[1]"


https://en.wikipedia.org/wiki/Feature_engineering


However, it feels like many people in the analytics / ML world bleed this into "data extraction" or "data munging" type activities. They arent doing the "last step" and converting the tabular-dataset into an n-dimensional array of numeric features (imho)


SIDE NOTE: in my DL book we wrote, we call the chapter on this topic "Vectorization", and we used that a lot of places, and it seemed to pass muster (in 2016-ish, at least. times change?). I FEEL as if we were more referring to the stage of the transforms where we convert data into its final pre-modeling form of numeric features, and less of the "lets go do transforms and junk and create new features"...


So


My question: "should we consider the final step of feature engineering to be 'vectorization' or 'feature encoding' ?"

Susan Says:

> I feel like vectorization or feature encoding are both fine terms to describe the process of going from something that is not numeric to numeric. I definitely think about it as separate from feature engineering. Feature encoding/vectorization has to happen always (ie everything has to have a numeric representation). But feature engineering is something that might be useful but not always necessary (maybe a neural net will learn all these relationships..aka automatic feature extraction). 

TODO:

* reference weka book (as early practitioner guide)
* check terminology in Bishop book

## Vectorization

From our book:

> “take each data type and represent it as a numerical vector (or in some cases, a multidimensional array of numbers)”

From Geron:

> “We already discussed two of these layers: the keras.layers.Normalization layer that will perform feature standardization (it will be equivalent to the Standardization layer we defined earlier), and the TextVectorization layer that will be capable of encoding each word in the inputs into its index in the vocabulary. In both cases, you create the layer, you call its adapt() method with a data sample, and then you use the layer normally in your model. The other preprocessing layers will follow the same pattern.”

## Data Engineer

> (redit) "Uses a combination of software engineering best practices and database design to build scalable data pipelines, data integrations, and data models for use in applications and reports"

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


