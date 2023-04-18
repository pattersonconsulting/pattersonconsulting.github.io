---
layout: post
published-on: March 27th 2023
author: Josh Patterson
title: Appendix B - Data Roles
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

This article is part of a larger series:

* [Prologue (Don't Panic)](hitchhikers_guide_modern_data_products_1_prologue.html)
* [The Evolution of Modern Data Platforms](hitchhikers_guide_modern_data_products_2_evolution_data_platforms.html)
* [Revisting The Lab and the Factory](hitchhikers_guide_modern_data_products_3_lab_and_factory_redux.html)
* [A Methodology for Building Data Products](hitchhikers_guide_modern_data_products_4_methodology_for_data_products.html)
* [Appendix A: Definitions](hitchhikers_guide_modern_data_products_5_appendix_A_definitions.html)
* [Appendix B: Roles](hitchhikers_guide_modern_data_products_6_appendix_B_roles.html)

# Overview

In this appendix we breakdown the specific roles involved in analytics and machine learning. There are many skills required of roles in the data platform space and each role has some overlap with other roles in terms of skills required. In the infographic below, we show a comparison of the skills (rated 1-5 per skill per role) in a polar plot:

![Data Roles Polar Plot](./images/polar_plot_roles_20230413.png "Data Roles Polar Plot")

Note: This diagram was inspired by a similar digram in the Data Captain's article ["Guide to Data roles"](https://www.datacaptains.com/blog/guide-to-data-roles).

In the sections that follow I breakdown specific details about each role and what kind of tools are commonly used in the role.

# Data Scientist

A data scientist is a professional who uses their skills in statistical analysis, machine learning, data mining, and data visualization to extract insights from large and complex sets of data. They possess technical skills in programming languages such as Python or R, and data manipulation tools such as SQL and Excel. Additionally, they must have strong communication skills to effectively present their findings to non-technical stakeholders.

Data scientists work with data engineers to build machine learning models based on datasets extracted from the data warehouse and from other souces such as log files, tabular data in flat files, etc.

## Common Data Scientist Tools Used

* Python, Pandas, Jupyter Notebooks
* Scikit-learn, TensorFlow, PyTorch, more
* SAS
* R

# Data Engineer

A data engineer is a professional who designs and builds the infrastructure to store, process, and analyze large and complex data sets. They work closely with data scientists to identify the data requirements and ensure that the necessary data is available in a usable format.

Data engineers are skilled in data architecture, database design, and distributed systems. They are responsible for developing and implementing data pipelines, transforming data into a usable format, and loading it into a data warehouse. They also optimize data processing systems to ensure efficiency and scalability. 

We list key tasks and the required skills for a data engineer below based on the article [The Rise of the Data Engineer](https://www.freecodecamp.org/news/the-rise-of-the-data-engineer-91be18f1e603/).

## Key Tasks

* data ingestion
* metric computation
* anomaly detection
* metadata management
* experimentation
* instrumentation
* sessionization

## Required Skills

* SQL
* Data modeling techniques
* ETL design
* System architecture

# Machine Learning Engineer

A machine learning engineer is responsible for designing, building, and deploying machine learning systems that can learn from and make predictions on large and complex sets of data. They work closely with data scientists to develop and implement machine learning algorithms and are skilled in programming languages such as Python or Java, as well as machine learning frameworks such as TensorFlow or PyTorch.

Machine learning engineers are responsible for selecting and preparing data sets, tuning the parameters of machine learning models, and designing and developing the software infrastructure needed to support machine learning systems. They work with data scientists and other stakeholders to identify business problems that can be solved with machine learning and to deliver solutions that can provide business value. 

Overall, machine learning engineers are highly technical professionals who are critical to the development and implementation of machine learning systems.

# Analytics Engineer

Analytics engineer is a role [defined by DBT Labs](https://www.getdbt.com/what-is-analytics-engineering/):

> Analytics engineers provide clean data sets to end users, modeling data in a way that empowers end users to answer their own questions. While a data analyst spends their time analyzing data, an analytics engineer spends their time transforming, testing, deploying, and documenting data. Analytics engineers apply software engineering best practices like version control and continuous integration to the analytics code base.

## Key Tasks

We list the key tasks for an analytics engineer from [Preset's blog](https://preset.io/blog/reshaping-data-engineering/):

* owning core datasets: as analytics engineers cover more specific subject areas, data engineers may cover the mission-critical datasets that are heavily shared across teams
* data modeling: define and refine best practices around modeling data
* coding standards: define and defend naming conventions, coding conventions, and testing standards.
* abstractions: create and manage reusable components in the form of jinja macros libraries and computation frameworks
* metadata management: data assets documentation, discoverability, metadata integration, etc
* data operations: SLAs, data warehouse cost management, data quality monitoring, anomaly detection, and garbage collecting unused resources


# Data Analyst

A data analyst is a professional who examines large and complex sets of data to identify patterns, trends, and insights that can be used to inform business decisions. They use statistical and analytical techniques such as regression analysis, hypothesis testing, and data visualization to extract insights from data. They are skilled in programming languages such as SQL, Python, or R, and data manipulation tools such as Excel or Tableau.

Data analysts are responsible for collecting and cleaning data, preparing it for analysis, and presenting their findings to stakeholders through reports or visualizations. They play a critical role in informing business decisions by providing insights based on data analysis. Overall, data analysts are highly analytical professionals who are responsible for extracting insights from data and communicating their findings to stakeholders.

DBT Labs has a [great article comparing the Data Analyst role](https://www.getdbt.com/what-is-analytics-engineering/) with other data roles:

> While a data analyst spends their time analyzing data, an analytics engineer spends their time transforming, testing, deploying, and documenting data. 

Analytics engineers apply software engineering best practices like:

* version control
* continuous integration 

to the analytics code base.

# Cloud DevOps

* TODO: more writing on how this role deploys infrastructure as contrasted to roles who "use the infrastructure"

<!-- 

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
-->
