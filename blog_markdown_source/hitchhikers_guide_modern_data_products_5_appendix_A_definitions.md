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

* If the pandas dataframe is the key api here --- need to note how the work done under pandas with Arrow and Parquet are key areas of development
* Wes McKinney ported the R dataframe to python to create the pandas implementation

# Analytics Terms Definitions

Some good definitions on reddit blog:

https://dataengineering.wiki/FAQ/What+is+the+difference+between+a+Data+Engineer+and+X

## Table

In a data warehouse, a table is a collection of related data organized into rows and columns. Tables are used to store and manage structured data, which is data that is organized into a specific format, such as a spreadsheet or database.


## View

In a database, a view is a virtual table that presents data from one or more underlying tables in a specific way. A view does not actually contain any data itself; it simply provides a way to access and display data that is already stored in the database.

Views are used to simplify complex queries by presenting the data in a more easily understandable format, or to provide a subset of the data that is relevant to a particular application or user. For example, a view could be created to display only the names and phone numbers of customers who have made a purchase in the last 30 days.


## Metrics

In data modeling, a metric is a quantifiable measure of a specific aspect of a business or application. Metrics are used to evaluate performance, track progress towards goals, and make data-driven decisions.

Metrics can take many forms, depending on the context and purpose of the data modeling exercise. For example, in an e-commerce application, metrics might include the number of orders processed, the average order value, and the conversion rate from site visits to purchases. In a marketing campaign, metrics might include the number of leads generated, the click-through rate of an advertisement, or the cost per acquisition.

Metrics are typically defined in terms of a specific unit of measurement, such as dollars, hours, or clicks. They are often accompanied by targets or benchmarks that represent the desired level of performance, as well as historical data that can be used to identify trends and patterns over time.

In data modeling, metrics are often used as the basis for developing dashboards, reports, and other data visualizations that allow stakeholders to monitor performance and make informed decisions. Effective metric selection and tracking is critical to the success of any data-driven initiative, as it provides a common language for evaluating progress and identifying areas for improvement.

For this marketing activity, relevant metrics may be: 

1. Total visitors to the landing page
2. Total visitors broken down by acquisition channel (organic search, referral, cpc, etc.)
3. Total time spent on the page
4. Total form submissions

Again, these are just the data building blocks.


## KPIs

A Key Performance Indicator (KPI) is a measurable value that is used to assess the performance of an organization, a business unit, a project, or an individual in achieving specific objectives or goals. KPIs are used to evaluate progress and make data-driven decisions, and are typically tied to strategic or operational objectives.

KPIs can take many forms, depending on the nature of the organization and the goals being pursued. Examples of KPIs might include:

* Revenue growth rate
* Customer retention rate
* Net promoter score (NPS)
* Time to market for new products or services
* Employee satisfaction and engagement
* Website traffic and conversion rates
* On-time delivery rate

KPIs are typically chosen based on their relevance to the objectives being pursued, as well as their measurability and their ability to drive behavior and decision-making. KPIs should be clearly defined, and should be tracked and reported on a regular basis to ensure that progress is being made towards the desired outcomes.

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

Analytics is the process of analyzing and interpreting data in order to gain insights, inform decision-making, and improve performance. Analytics involves a range of techniques and tools, including statistical analysis, data mining, machine learning, and predictive modeling, among others.

Analytics can be used to answer a variety of questions, such as:

* What are the patterns and trends in our data?
* What factors are driving changes in our business?
* What are the key drivers of customer behavior?
* What are the best ways to allocate resources to achieve our goals?
* What is the likelihood of a specific outcome, such as a purchase or a churn event?

Analytics can be applied in a variety of domains, including business, finance, healthcare, education, and many others. Analytics is often used to inform decision-making at various levels of an organization, from operational decisions to strategic planning.

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


## Business Intelligence (BI)

Business Intelligence (BI) is a process of transforming raw data into actionable insights that can inform decision-making and improve business performance. BI involves a range of activities, including data mining, analytics, reporting, and visualization, among others.

The goal of BI is to help organizations make data-driven decisions by providing insights into key business metrics, such as sales, customer behavior, market trends, and operational efficiency. BI tools and technologies enable users to explore data from multiple sources, create reports and dashboards, and share insights with stakeholders across the organization.

BI can be used for a variety of purposes, such as:

* Monitoring and analyzing key performance indicators (KPIs)
* Identifying trends and patterns in data
* Improving operational efficiency
* Identifying new opportunities for growth
* Optimizing marketing and sales strategies
* Enhancing customer experiences

BI tools and technologies include data warehouses, data marts, online analytical processing (OLAP), dashboards, and data visualization tools. These tools enable users to access and analyze data from multiple sources, such as databases, spreadsheets, and external data sources.


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

Data modeling in the context of a data warehouse is the process of creating a conceptual, logical, and physical representation of the data that will be stored in the warehouse. Data modeling involves identifying the key entities and relationships that exist within the data, and creating a structure that can be used to efficiently store and retrieve the data.

The data modeling process typically involves several steps:

1. Conceptual modeling: This involves identifying the key business entities and their relationships, as well as the high-level data requirements of the business. The result of this step is a conceptual data model that represents the business requirements in a simplified and abstracted form.

2. Logical modeling: This involves refining the conceptual model to create a logical data model that can be implemented in a database management system. The logical model includes the definition of tables, columns, relationships, constraints, and other attributes.

3. Physical modeling: This involves creating a physical data model that maps the logical model to the physical storage structures of the database management system. This includes decisions around storage formats, indexing, partitioning, and other database-specific attributes.

The goal of data modeling in a data warehouse is to create a structure that can efficiently store and retrieve large volumes of data, while also supporting the analytical and reporting requirements of the business. Data modeling is critical to the success of a data warehouse initiative, as it provides the foundation for all subsequent activities, such as ETL (Extract, Transform, Load), data integration, and reporting.

> "This is the process of producing a data model, an abstract model to describe the data and relationships between different parts of the data.[27]"

### What are 3 Examples of Data Modeling?

1. a
2. b
3. c

## Data Warehouse

A Data Warehouse is a large and centralized repository of data that is designed to support business intelligence (BI) activities, such as reporting, analytics, and data mining. The data in a Data Warehouse is typically extracted from multiple, heterogeneous sources, transformed to conform to a common schema, and loaded into the warehouse for analysis.

Data Warehouses are designed to support the efficient storage, retrieval, and analysis of large volumes of data, typically over a period of several years. They are optimized for read-intensive workloads and support complex queries, reporting, and analytics. Data Warehouses are typically organized around subject areas, such as sales, inventory, or customer data, and may include multiple data marts or data cubes that provide a multidimensional view of the data.

Data Warehouses typically include the following components:

1. Data sources: This includes the systems and applications from which data is extracted and transformed.

2. ETL (Extract, Transform, Load) tools: These tools are used to extract data from source systems, transform it to conform to a common schema, and load it into the Data Warehouse.

3. Data storage: This includes the physical storage infrastructure used to store the data, such as disk arrays or solid-state drives.

4. Data access and analysis tools: These tools are used to query and analyze the data in the Data Warehouse, such as SQL (Structured Query Language) or OLAP (Online Analytical Processing) tools.

Data Warehouses are used in a variety of industries and domains, including finance, healthcare, retail, and manufacturing. They are used to support a range of BI activities, such as performance monitoring, trend analysis, predictive modeling, and decision support.

## Data Products

* downstream from the core data models of the data warehouse

A data product is a software application or service that is designed to deliver insights and value from data. Data products are created by leveraging data analytics, machine learning, and other techniques to derive insights from data, and then delivering those insights to users through a user-friendly interface or API.

Data products can take many forms, including dashboards, reports, APIs, and data visualizations. They can be used by businesses to monitor key metrics, identify trends and patterns, and make data-driven decisions. They can also be used by consumers to access information, such as weather forecasts, stock prices, or traffic updates.

Data products are typically designed to be scalable, reliable, and secure, and may include features such as real-time data processing, automated data quality checks, and machine learning algorithms that learn and improve over time. They may also include features such as data privacy controls, access controls, and audit trails to ensure that data is used in a responsible and ethical manner.

### What are Some Examples of Data Products?

1. Data for a Business Intelligence Dashboard
2. Aggregated dataset for downstream machine learning
3. Operational Data (todo: differentiate this from BI data)
4. Monitoring Data
5. Data for Exploratory Discovery
6. Analytical Dataset


## Dimensions

In data warehousing, a dimension is a categorical variable or attribute that provides context for the measures or numerical values in a dataset. Dimensions are used to categorize or group the data, and are often used to filter, aggregate, and analyze the data in various ways.

Examples of dimensions in a data warehouse might include time, geography, product, customer, or sales channel. These dimensions can be used to group and categorize the measures, such as sales revenue, profit margin, or units sold.

Dimensions are typically hierarchical, meaning that they have levels or layers of granularity. For example, a time dimension might have levels such as year, quarter, month, week, and day, which can be used to aggregate or drill down into the data as needed.

Dimensions can also have attributes, which provide additional information about the dimension. For example, a product dimension might have attributes such as product name, product category, manufacturer, and price.

Overall, dimensions are an important concept in data warehousing, and are used to provide context and structure to the data, making it easier to analyze and understand.

## Cubes

In data warehousing, a cube is a multi-dimensional data structure that allows for efficient and flexible querying and analysis of large datasets. A cube is sometimes also referred to as a data cube or OLAP (Online Analytical Processing) cube.

A cube consists of dimensions and measures. Dimensions are the categorical variables or attributes that define the data, such as time, location, or product category. Measures are the numerical values that are being analyzed, such as sales revenue, units sold, or profit margin.

The cube organizes the data along these dimensions, creating a multi-dimensional view of the data. This allows for fast and flexible querying of the data along multiple dimensions, as well as the ability to perform complex analysis and calculations.

For example, consider a retail company that wants to analyze their sales data. They could create a cube with dimensions such as time, location, and product category, and measures such as sales revenue and units sold. The cube would allow them to easily query and analyze the sales data by different dimensions, such as sales by location and product category, or sales over time.

Overall, cubes are an important data structure in data warehousing, and allow for efficient querying and analysis of large, complex datasets.

## The Kimball Data Warehouse Architecture

The Kimball Data Warehouse Architecture, also known as the Dimensional Data Warehouse Architecture, is a popular approach to building data warehouses that was pioneered by Ralph Kimball in the 1990s. It is based on the principles of dimensional modeling and is designed to support the efficient retrieval and analysis of large volumes of data.

The Kimball Data Warehouse Architecture is characterized by the following features:

1. Dimensional modeling: This involves organizing data into dimensions and facts, where dimensions are descriptive attributes of the data, such as time, geography, and product, and facts are the numeric measurements that are being analyzed, such as sales, revenue, and profit.

2. Star schema: This is a type of dimensional modeling that uses a central fact table surrounded by dimension tables, where each dimension table is linked to the fact table through a foreign key relationship.

3. Data integration: This involves the process of extracting data from multiple source systems, transforming it to conform to a common data model, and loading it into the data warehouse.

4. Data aggregation: This involves the process of summarizing data at different levels of granularity, such as by day, week, or month, to support different types of analysis.

5. Business intelligence tools: These are tools used to analyze and report on the data in the data warehouse, such as OLAP (Online Analytical Processing) tools, reporting tools, and dashboards.

The Kimball Data Warehouse Architecture is designed to support the efficient retrieval and analysis of large volumes of data, and to enable business users to easily explore and analyze the data using a variety of tools and techniques. It has become a widely adopted approach to building data warehouses and is used in a variety of industries and domains.

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

## Dataframe

what is it

how is it used in ml?

need to mention how we worked with data in a database pre-Dataframe

* just jdbc / odbc to query database for some data via sql
* iterate through the records, converting them into Rows in a dataset
* turn rows into vectors that could be used in machine learning -- typically a vector format that was proprietary to the machine learning lib

### The Dataframe Construct as a Bridge Between Analyitcs and Machine Learning

how is it a bridge between analytics and 


## Vector

asda

In machine learning, a vector is a one-dimensional array or list of numbers. Vectors are commonly used to represent data points or features in a dataset. For example, in image recognition, each image can be represented as a vector of pixel values, where each element of the vector represents the intensity of a specific pixel.

Vectors can be used to perform various mathematical operations in machine learning, such as dot products, element-wise multiplication, and addition. These operations can be used to compute similarities between vectors, transform data, and build models.

In addition, vectors can be represented in different spaces, such as Euclidean space, where the length and direction of the vector are important, or in feature space, where each element of the vector represents a feature of the data.

## Matrix

asdf

In machine learning, vectors and matrices are both fundamental data structures used to represent and manipulate data.

A vector is a one-dimensional array or list of numbers, while a matrix is a two-dimensional array of numbers. A matrix can be thought of as a collection of vectors arranged in rows and columns.

In machine learning, matrices are commonly used to represent datasets, where each row represents a data point or sample, and each column represents a feature or attribute of the data. For example, in a dataset of housing prices, a matrix could be used to represent the prices of different houses, where each row represents a house, and each column represents a feature such as the number of bedrooms, square footage, or location.

Matrices can be used to perform various operations in machine learning, such as matrix multiplication, which is used in linear regression and neural networks to transform and combine data.

In summary, while vectors and matrices are different data structures, they are related in that a matrix is a collection of vectors, and both are commonly used to represent and manipulate data in machine learning.

## Tensor

asdf

In machine learning, tensors are multi-dimensional arrays or matrices that can have any number of dimensions. They are used to represent and manipulate large amounts of data, especially in deep learning.

Tensors are used to represent a wide variety of data, such as images, audio, video, text, and time-series data. For example, in image recognition, an image can be represented as a tensor of pixel values, where each dimension represents a different aspect of the image, such as its width, height, and color channels.

Tensors can be manipulated using tensor operations, which are similar to matrix operations, but are extended to handle multi-dimensional arrays. Some common tensor operations used in machine learning include tensor addition, multiplication, and convolution.

Tensors are used extensively in deep learning frameworks like TensorFlow and PyTorch, where they form the backbone of neural network models. Neural networks consist of layers of interconnected nodes, or neurons, that perform tensor operations on input data to produce output predictions.

Overall, tensors are an important data structure in machine learning, and are used to represent and manipulate large, complex datasets in a wide variety of applications.

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

GPT

Vectorization in machine learning refers to the process of converting a set of data points or features into a mathematical vector or matrix format, which can be easily understood and processed by a computer.

In other words, it is a way to represent data in a structured format that is suitable for machine learning algorithms to process efficiently. This is usually done by converting the raw data into a numerical format, such as through one-hot encoding, normalization, or other methods.

Vectorization is a crucial step in many machine learning tasks, such as image recognition, natural language processing, and recommender systems, where large amounts of data need to be processed quickly and accurately. By using vectorization techniques, we can reduce the complexity of the data and make it more manageable for machine learning algorithms to work with.

From Geron:

> “We already discussed two of these layers: the keras.layers.Normalization layer that will perform feature standardization (it will be equivalent to the Standardization layer we defined earlier), and the TextVectorization layer that will be capable of encoding each word in the inputs into its index in the vocabulary. In both cases, you create the layer, you call its adapt() method with a data sample, and then you use the layer normally in your model. The other preprocessing layers will follow the same pattern.”

## Data Engineer

> (redit) "Uses a combination of software engineering best practices and database design to build scalable data pipelines, data integrations, and data models for use in applications and reports"

### Data Engineers vs Cloud DevOps

Data Engineer Role and Cloud DevOps Role are both critical roles in modern businesses that rely heavily on technology. Here are the key differences and similarities between these two roles:

Job Responsibilities:
Data Engineers are responsible for building and maintaining data pipelines that collect, process, and store large amounts of data. They are skilled in designing, building, and managing data storage systems and data processing infrastructure. They ensure that data is secure, easily accessible, and of high quality.

Cloud DevOps, on the other hand, is responsible for managing the cloud infrastructure that runs an organization's applications. They work on automating the deployment, scaling, and management of applications on the cloud infrastructure. They ensure the cloud infrastructure is secure, cost-efficient, and always available.

Skills Required:
Data Engineers need to have a strong foundation in computer science, database systems, and data modeling. They should be skilled in programming languages such as Python, SQL, and Java. Additionally, they need to have expertise in ETL (extract, transform, load) processes, data warehousing, and big data technologies like Hadoop and Spark.

Cloud DevOps require skills in cloud computing, containerization technologies like Docker and Kubernetes, and Infrastructure as Code (IaC) tools like Terraform and Ansible. They should be proficient in scripting languages like Bash, Python, and PowerShell. Additionally, they need to have strong skills in CI/CD (continuous integration and continuous deployment), monitoring, and logging tools.

Tools and Technologies:
Data Engineers work with data storage technologies like Hadoop, Spark, and NoSQL databases like Cassandra, MongoDB, and DynamoDB. They also use data processing frameworks like Apache Beam and Apache Kafka. Additionally, they use data modeling tools like ERwin and ER/Studio.

Cloud DevOps use cloud computing platforms like AWS, Azure, and Google Cloud Platform. They use containerization technologies like Docker and Kubernetes to deploy applications. They also use Infrastructure as Code (IaC) tools like Terraform and Ansible. Additionally, they use CI/CD tools like Jenkins, Travis CI, and CircleCI.

In summary, Data Engineers and Cloud DevOps are both critical roles in modern businesses that rely heavily on technology. The key differences between these two roles are in their job responsibilities, required skills, and the tools and technologies they use. However, they share some similarities in their roles, such as working to ensure security and availability of the organization's technology infrastructure.

## Data Engineering

Data engineering is the process of designing, building, and maintaining the infrastructure and systems that enable organizations to process, store, and analyze large volumes of data. Data engineering is a critical component of any data-driven organization, as it is responsible for ensuring that data is available, accessible, and usable for a variety of purposes, such as business intelligence, analytics, and machine learning.


> "Data engineering refers to the building of systems to enable the collection and usage of data. This data is usually used to enable subsequent analysis and data science; which often involves machine learning.[1][2] Making the data usable usually involves substantial compute and storage, as well as data processing and cleaning."

https://en.wikipedia.org/wiki/Data_engineering

https://www.amazon.com/Fundamentals-Data-Engineering-Robust-Systems/dp/1098108302/ref=pd_bxgy_img_sccl_2/143-2847560-0944436?pd_rd_w=BXhTE&content-id=amzn1.sym.6ab4eb52-6252-4ca2-a1b9-ad120350253c&pf_rd_p=6ab4eb52-6252-4ca2-a1b9-ad120350253c&pf_rd_r=V2C07V6S9W4WZ52VK07T&pd_rd_wg=36QXW&pd_rd_r=b1b67f23-fc07-46ff-ba58-f30f071cd2e6&pd_rd_i=1098108302&psc=1&asin=1098108302&revisionId=&format=4&depth=1

* WTF is "Data Engineering"?
   * the term has shifted over time
   * how we viewed it in the DL Book


Data engineering involves a range of activities, including:

1. Data integration: This involves the process of extracting data from multiple source systems, transforming it to conform to a common data model, and loading it into a data warehouse or other storage system.

2. Data modeling: This involves designing and creating data models that represent the structure and relationships of data, such as entity-relationship models or dimensional models.

3. Data pipeline development: This involves building and maintaining the data pipelines that move data from source systems to storage systems, and from storage systems to analytics or machine learning systems.

4. Data quality management: This involves ensuring that data is accurate, complete, and consistent, and that it meets the needs of the organization.

5. Infrastructure management: This involves designing, building, and maintaining the hardware and software infrastructure needed to support data processing, storage, and analysis.

6. Performance optimization: This involves tuning and optimizing data processing and storage systems to ensure that they can handle large volumes of data and support the needs of the organization.

Data engineering requires a range of technical skills, including programming, database management, data modeling, and distributed systems. Data engineers must also have a strong understanding of the business needs and goals of the organization, and must be able to collaborate effectively with other stakeholders, such as data analysts, data scientists, and business leaders.


## Machine Learning Modeling

Machine learning modeling is the process of using machine learning algorithms to build a model based on training data. A machine learning model is a mathematical representation of the patterns and relationships in the data that the algorithm has learned, and it can be used to make predictions or decisions on new data.

The process of building a machine learning model typically involves the following steps:

1. Data preparation: This involves selecting and cleaning the data that will be used to train the model, and transforming it into a format that can be used by the machine learning algorithm.

2. Feature engineering: This involves selecting and creating the features or attributes that will be used by the model to make predictions or decisions. This step often involves domain knowledge and creativity, as the features must be relevant and informative for the problem being solved.

3. Model selection: This involves selecting the type of machine learning algorithm that will be used to train the model, based on the problem being solved and the characteristics of the data.

4. Model training: This involves feeding the prepared data into the machine learning algorithm and adjusting the model parameters to optimize its performance on the training data.

5. Model evaluation: This involves testing the performance of the trained model on a separate set of data that was not used for training, to ensure that it is able to generalize to new data and make accurate predictions or decisions.

6. Model deployment: This involves integrating the trained model into a production system or application, where it can be used to make predictions or decisions in real-time.

Machine learning modeling is used in a wide range of applications, such as image recognition, natural language processing, fraud detection, and recommendation systems. It requires a combination of technical skills, such as programming, statistics, and mathematics, as well as domain knowledge and creativity to select and engineer the right features for the problem being solved.

A further great guide on the specific process of machine learning:

https://arxiv.org/pdf/2108.02497.pdf

### What are 3 Examples of Machine Learning Modeling?

1. Training a linear regression model on a tabular dataset to predict the price of a house
2. Training a neural network model to predict when a specific manufacturing machine will fail
3. Training a logist


## Machine Learning Model Inference

Machine learning model inference is the process of using a trained machine learning model to make predictions or decisions on new, unseen data. Once a machine learning model has been trained, it can be deployed and used to make predictions or decisions on new data in real-time.

## Artificial Intelligence

* marketing


