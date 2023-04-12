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

Series:

* [Prologue (Don't Panic)](hitchhikers_guide_modern_data_products_1_prologue.html)
* [The Evolution of Modern Data Platforms](hitchhikers_guide_modern_data_products_2_evolution_data_platforms.html)
* [Revisting The Lab and the Factory](hitchhikers_guide_modern_data_products_3_lab_and_factory_redux.html)
* [A Methodology for Building Data Products](hitchhikers_guide_modern_data_products_4_methodology_for_data_products.html)
* [Appendix A: Definitions](hitchhikers_guide_modern_data_products_5_appendix_A_definitions.html)
* [Appendix B: Roles](hitchhikers_guide_modern_data_products_6_appendix_B_roles.html)

We spend the first 3 posts of this series providing background and definitions to set the stage for our methodology and in part 4 we lay out our step by step process.

TODO:
* create a key visualization to represent the core ideas of the page
* this will also serve as the meta og card image



# Data Scientist

Reddit:

> Data Scientist: Uses data for more in-depth analysis and visualizations. Typically the work is more research based and sometimes one will work on a product like a machine learning model.

# Data Engineer

DBT definitions of role:

* build custom data integrations
* manage overall pipeline orchestration
* develop and deploy machine learning endpoints
* build and maintain the data platform
* data warehouse performance optimizations


# Machine Learning Engineer

* MLOps
* Model Building
* Model Deployment
* Inference

# Analytics Engineer

DBT definitions of role:

* Provide clean, transformed data ready for analysis
* apply software engineering best practices to analytics code (eg., version control, testing, continuous integration)
* maintain data documentation and definitions
* train business users on how to use data visualization tools

Reddit:

> BI Engineer/BI Developer: Uses primarily GUI tools like SSIS to build ETL pipelines, build data models for reports, and even may build the reports themselves. This role is similar in many ways to a Data Engineer but differs in tooling and skillsets required. It is sometimes seen as a pathway to becoming a Data Engineer.

# Data Analyst

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

# Database Administrator (DBA)

Reddit: 

> Database Administrator: Focuses on making sure the database and infrastructure is available and secure (i.e. backing up data, user management, server usage). They do not typically build within the database itself.



