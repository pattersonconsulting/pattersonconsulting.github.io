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
* [Appendix B: Roles](hitchhikers_guide_modern_data_products_6_appendix_B_roles.html)


# Overview

In this appendix we define key terms used throughout the series on data platforms. Many of these terms are commonly known by a subset of data practitioners, but its good to have them all in once place and then be able to compare and relate the terms. In the diagram below we kick off the appendix with a diagram relating how the worlds of SQL and Python are linked together through the dataframe concept.

![Intersection of SQL and Python](./images/sql_df_python.png "Intersection of SQL and Python")

# Data Platform Definitions


## Data Warehouse

Ralph Kimball describes a data warehouse as:

> "A data warehouse is a copy of transaction data specifically structured for query and analysis."

Bill Inmon describes a data warehouse as:

> "A data warehouse is a subject-oriented, integrated, time-variant and non-volatile collection of data in support of management’s decision making process."

**A Data Warehouse is a large and centralized repository of data that is designed to support business intelligence (BI) activities, such as reporting, analytics, and data mining.**

The data in a Data Warehouse is typically extracted from multiple, heterogeneous sources, transformed to conform to a common schema, and loaded into the warehouse for analysis.

Data Warehouses are designed to support the efficient storage, retrieval, and analysis of large volumes of data, typically over a period of several years. They are optimized for read-intensive workloads and support complex queries, reporting, and analytics. Data Warehouses are typically organized around subject areas, such as sales, inventory, or customer data, and may include multiple data marts or data cubes that provide a multidimensional view of the data.


### The Kimball Data Warehouse Architecture

The [Kimball Data Warehouse Architecture](https://www.kimballgroup.com/data-warehouse-business-intelligence-resources/kimball-techniques/dimensional-modeling-techniques/), also known as the Dimensional Data Warehouse Architecture, is a popular approach to building data warehouses that was pioneered by Ralph Kimball in the 1990s. 

It is based on the principles of dimensional modeling and is designed to support the efficient retrieval and analysis of large volumes of data.

The Kimball Data Warehouse Architecture is characterized by the following features:

1. Dimensional modeling: This involves organizing data into dimensions and facts, where dimensions are descriptive attributes of the data, such as time, geography, and product, and facts are the numeric measurements that are being analyzed, such as sales, revenue, and profit.

2. Star schema: This is a type of dimensional modeling that uses a central fact table surrounded by dimension tables, where each dimension table is linked to the fact table through a foreign key relationship.

3. Data integration: This involves the process of extracting data from multiple source systems, transforming it to conform to a common data model, and loading it into the data warehouse.

4. Data aggregation: This involves the process of summarizing data at different levels of granularity, such as by day, week, or month, to support different types of analysis.

5. Business intelligence tools: These are tools used to analyze and report on the data in the data warehouse, such as OLAP (Online Analytical Processing) tools, reporting tools, and dashboards.

The Kimball Data Warehouse Architecture is designed to support the efficient retrieval and analysis of large volumes of data, and to enable business users to easily explore and analyze the data using a variety of tools and techniques. It has become a widely adopted approach to building data warehouses and is used in a variety of industries and domains.

## Data Lake

A data lake is a large centralized repository that stores a vast amount of structured and unstructured data in its native format, without requiring pre-defined schema or organization. Unlike a traditional data warehouse, a data lake allows data to be ingested and stored as-is, making it easier to store and analyze large amounts of data, as well as allowing users to ask new questions and perform ad-hoc analyses without worrying about data modeling. Data lakes are used for big data analytics, machine learning, and other advanced analytics applications, but can also pose challenges such as data governance, data quality, and data security.

Apache Hadoop was an early version of the Data Lake. Hadoop was popular in the first half of the 2010s before data lakes began moving to the cloud.

## Data Lakehouse

A data lakehouse combines the advantages of a data warehouse and a data lake, allowing for the storage of raw, unstructured data in its native format, while also including organizational structure and performance optimization capabilities. It enables organizations to efficiently store and manage large amounts of data while maintaining data quality and governance, and allows for the use of various data analytics tools and techniques to gain insights and drive business value.

Key architecture components of the data lakehouse:

1. Metadata Layers for Data Management
2. SQL Performance
3. Efficient support for machine learning

**The data lakehouse architecture seeks to give the best of both worlds for the data warehouse user and the machine learning practictioner.**

# Analytics Terms Definitions

In the section below I give some quick definitions on common terms in the analytics space.

## Table

**In a database, a table is a collection of related data organized into rows and columns.**

Tables are used to store and manage structured data, which is data that is organized into a specific format, such as a spreadsheet or database.


## View

**In a database, a view is a virtual table that presents data from one or more underlying tables in a specific way.**

A view does not actually contain any data itself; it simply provides a way to access and display data that is already stored in the database.

Views are used to simplify complex queries by presenting the data in a more easily understandable format, or to provide a subset of the data that is relevant to a particular application or user. For example, a view could be created to display only the names and phone numbers of customers who have made a purchase in the last 30 days.


## Data Modeling

**Data modeling in the context of a data warehouse is the process of creating a conceptual, logical, and physical representation of the data that will be stored in the warehouse.**

Data modeling involves identifying the key entities and relationships that exist within the data, and creating a structure that can be used to efficiently store and retrieve the data.

The data modeling process typically involves several steps:

1. Conceptual modeling: This involves identifying the key business entities and their relationships, as well as the high-level data requirements of the business. The result of this step is a conceptual data model that represents the business requirements in a simplified and abstracted form.

2. Logical modeling: This involves refining the conceptual model to create a logical data model that can be implemented in a database management system. The logical model includes the definition of tables, columns, relationships, constraints, and other attributes.

3. Physical modeling: This involves creating a physical data model that maps the logical model to the physical storage structures of the database management system. This includes decisions around storage formats, indexing, partitioning, and other database-specific attributes.

The goal of data modeling in a data warehouse is to create a structure that can efficiently store and retrieve large volumes of data, while also supporting the analytical and reporting requirements of the business. Data modeling is critical to the success of a data warehouse initiative, as it provides the foundation for all subsequent activities, such as ETL (Extract, Transform, Load), data integration, and reporting.

In our other [blog article on data modeling with dbt](http://www.pattersonconsultingtn.com/blog/dbt_hello_world_part_2_pipeline.html) we describe data modeling as:

> In dbt (Data Build Tool), a data model is a logical representation of a specific type of data that you want to analyze or work with in your database. It describes the structure, relationships, and constraints of the data in a way that can be easily understood by both humans and computers. A DBT workflow is a directed acyclic graph (DAG) of DBT data models.

> A data model in dbt is typically defined as a SQL query that defines the relationships between tables or other data sources. It specifies how data should be transformed and aggregated to create a particular view of the data. This view can then be used as a source for further analysis or reporting.

> In dbt, a data model is created using a “model” statement in a SQL file. This statement defines the columns of the model, any relationships with other models or tables, and any transformations that should be applied to the data. Once defined, a data model can be used as a building block for creating more complex data structures and analyses.


## Metrics

**In data modeling, a metric is a quantifiable measure of a specific aspect of a business or application.**

Metrics are used to evaluate performance, track progress towards goals, and make data-driven decisions. Metrics can take many forms, depending on the context and purpose of the data modeling exercise. 

For example, in an e-commerce application, metrics might include 

* the number of orders processed
* the average order value
* and the conversion rate from site visits to purchases. 

In a marketing campaign, metrics might include 

* the number of leads generated
* the click-through rate of an advertisement
* or the cost per acquisition.

**Metrics are typically defined in terms of a specific unit of measurement, such as dollars, hours, or clicks.** They are often accompanied by targets or benchmarks that represent the desired level of performance, as well as historical data that can be used to identify trends and patterns over time.

Metrics should be considered the data building blocks. In data modeling, metrics are often used as the basis for developing dashboards, reports, and other data visualizations that allow stakeholders to monitor performance and make informed decisions. Effective metric selection and tracking is critical to the success of any data-driven initiative, as it provides a common language for evaluating progress and identifying areas for improvement.

## KPIs

**A Key Performance Indicator (KPI) is a measurable value that is used to assess the performance of an organization, a business unit, a project, or an individual in achieving specific objectives or goals.**

You -- as the marketer or analyst -- need to select those indicators of success.

KPIs are used to evaluate progress and make data-driven decisions, and are typically tied to strategic or operational objectives.

KPIs can take many forms, depending on the nature of the organization and the goals being pursued. Examples of KPIs might include:

* Revenue growth rate
* Customer retention rate
* Net promoter score (NPS)
* Time to market for new products or services
* Employee satisfaction and engagement
* Website traffic and conversion rates
* On-time delivery rate

KPIs are typically chosen based on their relevance to the objectives being pursued, as well as their measurability and their ability to drive behavior and decision-making. KPIs should be clearly defined, and should be tracked and reported on a regular basis to ensure that progress is being made towards the desired outcomes.

Comparing metrics to KPIs:

* Util metrics are studied and summarized into business insights, they are nothing more than numbers in a spreadsheet
* If metrics aren't aligned behind a set of KPIs, the usefulness of the data will fall short

## Analytics

**Analytics is the process of analyzing and interpreting data in order to gain insights, inform decision-making, and improve performance.**

Analytics refers to the systematic study and analysis of data (i.e. Metrics and KPIs). In analytics we want to study metics and work to extract insights and/or conclusions about what they mean for a business. 

We can answer specific questions with analytics or solve particular problems by analyzing data sets and identifying trends, patterns, and correlations that might not be immediately apparent.

Analytics are the interpretations of data that transform numbers and metrics into actionable ideas and insights --- and not data points that can be pulled directly from an analytics system.

Analytics can be used to answer a variety of questions, such as:

* What are the patterns and trends in our data?
* What factors are driving changes in our business?
* What are the key drivers of customer behavior?
* What are the best ways to allocate resources to achieve our goals?
* What is the likelihood of a specific outcome, such as a purchase or a churn event?

Analytics can be applied in a variety of domains, including business, finance, healthcare, education, and many others. Analytics is often used to inform decision-making at various levels of an organization, from operational decisions to strategic planning.

We start by outlining the metrics and KPIs as first step in the analysis process to understand what we're measuring and why.

Then we need to provide context and generate analytic results out of the data we are examining.


## Business Intelligence (BI)

**Business Intelligence (BI) is a process of transforming raw data into actionable insights that can inform decision-making and improve business performance.**

BI involves a range of activities, including data mining, analytics, reporting, and visualization, among others.

The goal of BI is to help organizations make data-driven decisions by providing insights into key business metrics, such as sales, customer behavior, market trends, and operational efficiency. BI tools and technologies enable users to explore data from multiple sources, create reports and dashboards, and share insights with stakeholders across the organization.

BI can be used for a variety of purposes, such as:

* Monitoring and analyzing key performance indicators (KPIs)
* Identifying trends and patterns in data
* Improving operational efficiency
* Identifying new opportunities for growth
* Optimizing marketing and sales strategies
* Enhancing customer experiences

BI tools and technologies include data warehouses, data marts, online analytical processing (OLAP), dashboards, and data visualization tools. These tools enable users to access and analyze data from multiple sources, such as databases, spreadsheets, and external data sources.

### BI vs Analytics

* BI focuses on collecting and presenting data in a way that is easy to understand and use (providing the information for decision making)
* Analytics focuses on using statistical and quantitative techniques to uncover insights and make predictions

## Dimensions

**A dimension is a categorical variable or attribute that provides context for the measures or numerical values in a dataset.**

Dimensions are used to categorize or group the data, and are often used to filter, aggregate, and analyze the data in various ways.

Examples of dimensions might include 

* time
* geography
* product
* customer
* sales channel

These dimensions can be used to group and categorize the measures, such as sales revenue, profit margin, or units sold.

Dimensions are typically hierarchical, meaning that they have levels or layers of granularity. For example, a time dimension might have levels such as year, quarter, month, week, and day, which can be used to aggregate or drill down into the data as needed.

Dimensions can also have attributes, which provide additional information about the dimension. For example, a product dimension might have attributes such as product name, product category, manufacturer, and price.

## Cubes

**In data warehousing, a cube is a multi-dimensional data structure that allows for efficient and flexible querying and analysis of large datasets.**

A cube is sometimes also referred to as a data cube or OLAP (Online Analytical Processing) cube.

A cube consists of dimensions and measures. Dimensions are the categorical variables or attributes that define the data, such as time, location, or product category. Measures are the numerical values that are being analyzed, such as sales revenue, units sold, or profit margin.

The cube organizes the data along these dimensions, creating a multi-dimensional view of the data. This allows for fast and flexible querying of the data along multiple dimensions, as well as the ability to perform complex analysis and calculations.

For example, consider a retail company that wants to analyze their sales data. They could create a cube with dimensions such as time, location, and product category, and measures such as sales revenue and units sold. The cube would allow them to easily query and analyze the sales data by different dimensions, such as sales by location and product category, or sales over time.


## Data Products

**A data product is a software application or service that is designed to deliver insights and value from data.**

Data products are created by leveraging data analytics, machine learning, and other techniques to derive insights from data, and then delivering those insights to users through a user-friendly interface or API.

While there are other datasets generated during the data modeling phase of a data warehouse, data products are generally downstream from the core data models of the data warehouse. Examples include:

1. Data for a Business Intelligence Dashboard
2. Aggregated dataset for downstream machine learning
3. Operational Data (todo: differentiate this from BI data)
4. Monitoring Data
5. Data for Exploratory Discovery
6. Analytical Dataset


# Machine Learning Terms Definitions

![From Scalars to Tensors](./images/scalar_to_tensor.jpg )

In this section I cover key terms in machine learning and explain how they are different.

## Scalar

In mathematics and computer science, a scalar is a single, real-valued number that is used to measure the magnitude or size of a quantity, such as distance, temperature, or speed.

## Vector

In machine learning, a vector is a one-dimensional array or list of numbers<sup>1</sup>. Vectors are commonly used to represent data points or features in a dataset. For example, in image recognition, each image can be represented as a vector of pixel values, where each element of the vector represents the intensity of a specific pixel.

Vectors can be used to perform various mathematical operations in machine learning, such as dot products, element-wise multiplication, and addition. These operations can be used to compute similarities between vectors, transform data, and build models.

## Matrix

In machine learning, vectors and matrices are both fundamental data structures used to represent and manipulate data.

A vector is a one-dimensional array or list of numbers, **while a matrix is a two-dimensional array of numbers. A matrix can be thought of as a collection of vectors arranged in rows and columns.**

In machine learning, matrices are commonly used to represent datasets, where each row represents a data point or sample, and each column represents a feature or attribute of the data. For example, in a dataset of housing prices, a matrix could be used to represent the prices of different houses, where each row represents a house, and each column represents a feature such as the number of bedrooms, square footage, or location.

## Tensor

In machine learning, **tensors are multi-dimensional arrays or matrices that can have any number of dimensions. They are used to represent and manipulate large amounts of data, especially in deep learning.**

Tensors are used to represent a wide variety of data, such as images, audio, video, text, and time-series data. For example, in image recognition, an image can be represented as a tensor of pixel values, where each dimension represents a different aspect of the image, such as its width, height, and color channels.

Tensors can be manipulated using tensor operations, which are similar to matrix operations, but are extended to handle multi-dimensional arrays. Some common tensor operations used in machine learning include tensor addition, multiplication, and convolution.

Tensors are used extensively in deep learning frameworks like TensorFlow and PyTorch, where they form the backbone of neural network models. Neural networks consist of layers of interconnected nodes, or neurons, that perform tensor operations on input data to produce output predictions.


## Attribute

**An attribute is an aspect of an instance (e.g. temperature, humidity).**

Attributes are often called features in Machine Learning. We note this difference because of the order of key machine learning books published around the year 2000:

1. The Weka book (1999)<sup>1</sup>
2. The ESL book (2001)<sup>2</sup>

In the late 1990's in machine learning terminology it was [common to see the term "attribute" used](https://ai.stanford.edu/~ronnyk/glossary.html). Towards the later 2000's the term "feature" became more common. 

Other commons terms that have been used interchangably for attribute are:

* field
* variable
* feature

Based on the context and usage, the terms "attribute" and "feature" have been used at times as synonyms and other times having different meanings.

## Feature

The book "Pattern recognition and machine learning" (2006, Bishop) defines feature<sup>3</sup> as:

> "In machine learning and pattern recognition, a feature is an individual measurable property or characteristic of a phenomenon.

The idea of a "feature" is related to statistical techniques and explanatory variables in methods such as linear regression. Features are part of an input, record, or sample.

Examples of features include:

* a pixel in an image
* the euclidean distance to a place in a geographical location
* a bank account balance
* a person's height

Features are usually numeric, but certain features (e.g., strings, graphs) are used in syntactic pattern recognition. The concept of "feature" is related to that of explanatory variable used in statistical techniques such as linear regression.

> A feature is a measurable property of the object you’re trying to analyze. In datasets, features appear as columns.

> Features are the basic building blocks of datasets. The quality of the features in your dataset has a major impact on the quality of the insights you will gain when you use that dataset for machine learning. Additionally, different business problems within the same industry do not necessarily require the same features, which is why it is important to have a strong understanding of the business goals of your data science project.

> You can improve the quality of your dataset’s features with processes like feature selection and feature engineering, which are notoriously difficult and tedious. If these techniques are done well, the resulting optimal dataset will contain all of the essential features that might have bearing on your specific business problem, leading to the best possible model outcomes and the most beneficial insights.


https://stats.stackexchange.com/questions/192873/difference-between-feature-feature-set-and-feature-vector

https://stats.stackexchange.com/questions/351514/usage-of-the-term-feature-vector-in-lindsay-i-smiths-pca-tutorial?rq=1


## Vectorization

The term "vectorization" in the context of machine learning is defined as:

> “take each data type and represent it as a numerical vector (or in some cases, a multidimensional array of numbers)”

Vectorization in machine learning refers to the process of converting a set of data points or features into a mathematical vector or matrix format, which can be easily understood and processed by a computer.

Vectorization is required in the case that a "feature" is not numeric; there is a final process between data engineering and machine learning modeling where the practitioner needs to convert any non-numeric data into numeric data. (Note that some modern machine learning libraries provide APIs to model raw non-numeric data in certain cases)

There are multiple methods used in vectorization such as:

* one-hot encoding
* normalization
* standardization

Vectorization is a crucial step in many machine learning tasks, such as image recognition, natural language processing, and recommender systems, where large amounts of data need to be processed quickly and accurately. By using vectorization techniques, we can reduce the complexity of the data and make it more manageable for machine learning algorithms to work with.

Many core machine learning libraries have vectorization classes. These libraries include:

* keras
* weka
* scikit-learn

TODO: https://www.pinecone.io/learn/time-series-vectors/#:~:text=Time%20series%20embeddings%20are%20a,but%20uncommon%20within%20time%20series.

> Once your time series are vectorized, you can use Pinecone to store and search for them in an easy-to-use and efficient environment. Check out this example showing how to perform time-series “pattern” matching to find out the most similar stock trends.



## Feature Vector

**A feature vector is a vector that stores the features for a particular observation in a certain order.**

A feature vector holds all of the features (e.g., "attributes") that we're interested in using as independent variables in our model.

The order of the elements in the vector is only important as long as they are consistent.

We are assuming the data is tabular implicitly when we use the terminology "feature vector", as the rows in the tabular data represent observations we wish to model with methods such as "linear regression". Other non-tabular data takes more engineering work to represent as features in most types of machine learning modeling algorithms.

Most algorithms in machine learning require a tabular, numerical representation of objects, since such representations are the the API contract for the mathematical processing and statistical analysis.

Many times in machine learning literature the [term "feature vector" is used in different ways](https://stats.stackexchange.com/questions/351514/usage-of-the-term-feature-vector-in-lindsay-i-smiths-pca-tutorial?rq=1).

## Feature Engineering

Feature engineering is [defined on wikipedia](https://en.wikipedia.org/wiki/Feature_engineering) as:

> "Feature engineering or feature extraction or feature discovery is the process of using domain knowledge to extract features (characteristics, properties, attributes) from raw data. The motivation is to use these extra features to improve the quality of results from a machine learning process, compared with supplying only the raw data to the machine learning process."

It's worth noting that the term "feature engineering" doesn't seem to gain popularity until around 2015 based on google trends:

![Feature Engineering on Google Trends](./images/google_trends_feature_engineering.png )

The term "feature construction" is another term that is sometimes used interchangably with the term "Feature engineering".

In some cases in literature you will see the term "vectorization" used to mean "feature construction" as well; It's worth noting that some folks believe "vectoriation" to be the final step in a feature engineering pipeline --- the step where you convert any non-numeric features to numeric representation. 

<!--
### Discussion on Feature Engineering

 The definition for "Feature Engineering" is always some form of:


"Feature engineering or feature extraction or feature discovery is the process of using domain knowledge to extract features (characteristics, properties, attributes) from raw data."


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

-->

## Dataframe

A DataFrame is a tabular data structure that organizes data into a 2-dimensional table of rows and columns. The most well-known implementation is the [Pandas DataFrame](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.html
) which is based directly on the R dataframe concept.

The dataframe construct directly mimics a relational database table or a spreadsheet and is one of the most common data structures in more recent data analytics.

Dataframes are popular because they allow data engineers and data scientists to work with tabular data from raw files and from relational database tables in an intuitive way with an API focused on tasks (e.g., column operations, joins, etc) that are relevant to those roles.

Dataframes are generally used in Python or R and allow Data Engineers to quickly join and filter datasets from the data warehouse. Data frames can also process raw file-based datasets for consumption by data scientists. Data scientists can quickly perform feature engineering operations with libraries such as Pandas and efficiently prepare data for machine learning modeling operations.

The dataframe is widely considered key abstraction between the worlds of analytics and machine learning. The graph below shows the popularity of the dataframe, which quickly began rising in 2014.

!["Dataframe" on Google Trends](./images/google_trends_dataframe.png )

<https://ponder.io/pandas-is-now-as-popular-as-python-was-in-2016/?utm_campaign=meetedgar&utm_medium=social&utm_source=meetedgar.com>
   
## Data Engineering

Data engineering is a practice focused on defining ETL for data coming from a variety of sources and may be expressed in different workflow or orchestration systems (e.g., Airflow, DBT).

Data engineering is responsible for ensuring that data is available, accessible, and usable for a variety of purposes, such as business intelligence, analytics, and machine learning. Maxime Beauchemin wrote a key article on the role of the data engineering in 2017 called [The Rise of the Data Engineer](https://www.freecodecamp.org/news/the-rise-of-the-data-engineer-91be18f1e603/). In this article Max defines Data Engineering as:

> "data engineers build tools, infrastructure, frameworks, and services. In fact, it’s arguable that data engineering is much closer to software engineering than it is to a data science"

Max attributes the evolution (2010-2015) of the data engineering role to the growth of:

> “big data” distributed systems, along with concepts around the extended Hadoop ecosystem, stream processing, and in computation at scale.

He further adds that in smaller companies that DevOps may be a part of the data engineering role:

> "the data engineering role may also cover the workload around setting up and operating the organization’s data infrastructure. This includes tasks like setting up and operating platforms like Hadoop/Hive/HBase, Spark, and the like."

* note/thought: in the age of the cloud data platforms, how much devops does the data engineer really have to do? Most of the infra are cloud-offered managed systems, so there is really only self-serve operations to be done

Foundationally data engineering is based in ETL techniques that have evolved and split into new sub-categories over time. Much of computer science is based in "games of view materialization" and ETL is exactly that --- view materialization.

In the age of Hadoop, Apache Oozie was the workflow orchestrator of the time. In the year 2023, data product workflow orchestration has moved to tools such as DBT, Airflow, and others.

### Key Tasks

Services and infrastructure a data engineering may operate and build include:

* data ingestion
* metric computation
* anomaly detection
* metadata management
* experimentation
* instrumentation
* sessionization

Data engineering is also focused on ways to automate the above tasks.

### Required Skills

* SQL
* Data modeling techniques
* ETL design
* System architecture

### Other Selected Articles on Data Engineering

* [The Downfall of the Data Engineer](https://maximebeauchemin.medium.com/the-downfall-of-the-data-engineer-5bfb701e5d6b)
* [Reshaping Data Engineering](https://preset.io/blog/reshaping-data-engineering/)
<!--
### Other Definitions

Data engineering involves a range of activities, including:

1. Data integration: This involves the process of extracting data from multiple source systems, transforming it to conform to a common data model, and loading it into a data warehouse or other storage system.

2. Data modeling: This involves designing and creating data models that represent the structure and relationships of data, such as entity-relationship models or dimensional models.

3. Data pipeline development: This involves building and maintaining the data pipelines that move data from source systems to storage systems, and from storage systems to analytics or machine learning systems.

4. Data quality management: This involves ensuring that data is accurate, complete, and consistent, and that it meets the needs of the organization.

5. Infrastructure management: This involves designing, building, and maintaining the hardware and software infrastructure needed to support data processing, storage, and analysis.

6. Performance optimization: This involves tuning and optimizing data processing and storage systems to ensure that they can handle large volumes of data and support the needs of the organization.

Data engineering requires a range of technical skills, including programming, database management, data modeling, and distributed systems. Data engineers must also have a strong understanding of the business needs and goals of the organization, and must be able to collaborate effectively with other stakeholders, such as data analysts, data scientists, and business leaders.
-->

### Data Engineering vs Cloud Dev Ops

Comparing the specific skills of the 2 roles in context of "The Modern Data Stack":

![Data Engineering vs Cloud Dev Ops](./images/radar_plot_data_eng_vs_cloud_devops.png )

## Machine Learning Modeling

Machine learning modeling is the process of using machine learning algorithms to build a model based on training data. A machine learning model is a mathematical representation of the patterns and relationships in the data that the algorithm has learned, and it can be used to make predictions or decisions on new data.

The process of building a machine learning model typically involves the following steps:

1. Data preparation
2. Feature engineering
3. Model training
4. Model evaluation
6. Model deployment

Machine learning modeling is used in a wide range of applications, such as image recognition, natural language processing, fraud detection, and recommendation systems. 

### What are 3 Examples of Machine Learning Modeling?

1. Training a linear regression model on a tabular dataset to predict the price of a house
2. Training a neural network model to predict when a specific manufacturing machine will fail
3. Using K-means clustering to discover relationships in a dataset

# References

* [1]: "Data Mining: Practical Machine Learning Tools and Techniques", 1st Edition, (1999), Witten and Frank, <https://www.cs.waikato.ac.nz/ml/weka/book.html>
* [2]: "The Elements of Statistical Learning: Data Mining, Inference, and Prediction", (2001), Hastie, Tibshirani, and Friedman
* [3]: "Pattern recognition and machine learning", (2006), Bishop, Christopher
* [4]: "An Introduction to Statistical Learning", https://www.statlearning.com/



