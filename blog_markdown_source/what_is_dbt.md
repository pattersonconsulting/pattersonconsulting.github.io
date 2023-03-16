---
layout: post
published-on: February 15th 2023
author: Josh Patterson
title: What is DBT?
subtitle: Understanding DBT and What it is Used For
description: In this post we'll .....
keywords: snowflake, duckdb, dbt, data engineering, cicd, sql
meta_og_image: pct_autogluon_dep_og_card.jpg
---

# What is DBT?

DBT is ...

> dbt is the best way to manage a collection of data transformations written in SQL or Python for analytics and data science. a required.

DBT (Data Build Tool) is an open-source command-line tool that allows data analysts and engineers to transform and manipulate data in their data warehouse. It provides a framework for creating and executing complex SQL queries and transforms, and it helps manage the entire data transformation process.

DBT is designed to work with a variety of data warehouses, including Snowflake, BigQuery, Redshift, and others. It allows users to define data models and transformations in a modular way, and it supports version control and collaboration through Git.

With DBT, analysts can define reusable SQL code and maintain a consistent data model across their organization. They can also build automated testing and validation into their data pipelines, ensuring data accuracy and consistency. Overall, DBT helps organizations build data pipelines that are maintainable, scalable, and easy to understand.

## What Does DBT Do?

Can dbt be used to load data? 
No, dbt does not extract or load data. 

It focuses on the transformation step only.

> dbt is a workflow orchestrator for SQL. 
> In other words, it’s a fancy Make for data analytics. 
> What makes dbt special is that it is the first workflow orchestrator that is dedicated to the SQL language. 
> It said out loud what many data teams were thinking: you can get a lot done with SQL.

dbt encourages you to massage your data in SQL rather than in, say, Python. 


Tristian Hardy Quote:

> "My primary MO as a data product thinker is stealing best practices from the world of software engineering and porting them to the world of data"

> Dbt brings the software engineering world to the SQL-savvy ELT developer. 
> It treats SQL queries as models — aka a SELECT script within a package. All models — in dbt— represent tables and views within the data warehouse. 
> These models can be versioned, and their schema and data can be tested — much as one would write unit tests for a piece of software code. 


## DBT Core Concepts

* Expressing transforms with SQL select
* Automatically build the DAG with ref(s)
* Tests ensure model accuracy
* Documentation is accessible and easily updated
* Use macros to write reusable SQL

## Why is DBT Popular?

> “standardizing their SQL transformation layers on dbt as they moved their data warehousing to the cloud.”
> dbt is the framework for modern cloud data warehouse development. It lets you build out a new kind of data pipeline that was never practical before. All while embracing today's best data practices: encapsulate business logic, check it into git, test your data, connect it in a DAG
> But dbt exists today for a reason. Cloud data warehouses demanded a new way of working. dbt met that need by doing all-in on SQL. The result is pretty cool.

> These talks reflect the implicit ethos behind Snowflake and dbt: 
> Our problems aren’t new, we don’t want to reimagine, reinvent, or revolutionize how we work to solve them, and we don’t want to be hit in the face with new innovations. 
> We just want the same tools we’ve always had—a database and some SQL—with some modern new magic quietly tucked behind them. 


# Why Would I Use DBT?

* A small company can’t afford those tools (e.g., Informatica, SQL Server Integration Services) -- And they dont want to use Microsoft

* Want to allow analysts who know only SQL to build transform pipelines -- analysts can build their own data pipelines, allowing them to work like software engineers
* Want version control, unit testing, environment handling 

* Don't want to use more expensive tools, or GUI tools

* can use SQL to scale out complex data modeling operations on modern cloud parallel SQL engines



## Role in Analytics


* why would we use dbt?

DBT plays a critical role in an enterprise analytics pipeline by providing a scalable and maintainable way to transform and manipulate data in a data warehouse. Here are some specific ways that DBT can support an analytics pipeline:

Transforming and modeling data: DBT allows data analysts and engineers to define data models and transformations in a modular way using SQL, making it easy to build complex data pipelines. DBT also supports incremental loads, allowing analysts to quickly update their data without having to reprocess the entire dataset.

Data validation and testing: DBT has built-in support for automated testing and validation, allowing analysts to ensure data accuracy and consistency. DBT can automatically run tests on data models and transformations as part of a continuous integration and deployment (CI/CD) pipeline.

Collaboration and version control: DBT integrates with Git, allowing analysts to collaborate on data models and transformations using a familiar version control system. This makes it easy to track changes to data pipelines over time and maintain a consistent codebase.

Documentation and lineage tracking: DBT includes built-in documentation features that allow analysts to document data models, transformations, and pipelines, making it easier for other team members to understand the data and how it's transformed. DBT also supports lineage tracking, allowing analysts to track data from its source to its destination and ensure data quality.

Overall, DBT provides a scalable and maintainable way to transform and manipulate data in a data warehouse, making it an essential tool for enterprise analytics pipelines.

### what does DBT replace?

DBT is not designed to replace any specific tool or technology, but rather to complement and enhance existing data warehousing and analytics tools. DBT can be used alongside ETL tools, such as Apache Airflow or Apache Nifi, and data visualization tools, such as Tableau or Looker, to provide a more complete data analytics solution.

However, DBT does offer some unique features that can replace certain manual or ad-hoc data transformation processes. For example, DBT can replace custom SQL scripts that are used to transform data, as it provides a more modular and reusable way to define data transformations. DBT also provides a more scalable way to transform data compared to traditional ETL tools, which may require significant maintenance and updates as the data pipeline grows in complexity.

Overall, DBT is a powerful tool that can enhance and streamline existing data analytics pipelines, but it's not designed to replace any specific tool or technology outright.


### We want to transform the raw data into a shape that’s ready for analytics

The solution: transform the raw data into a shape that’s ready for analytics. At the time, there were only two widely-used options:
1. Looker’s Persistent Derived Tables
2. Get a data engineer involved

However: DBT may replace a system that has a lot of transforms in Looker (As PDTs)



# How Do You Get Started with DBT?

## Anatomy of a DBT Project

* core files
* directory structure
* configuring a dbt project
* connecting to databases

A DBT project is typically organized into several folders and files, each with a specific purpose. Here is a breakdown of the typical structure of a DBT project:

1. Models: This folder contains the SQL code that defines data models and transformations. Each model is typically defined in a separate SQL file.

2. Data: This folder contains any data files or SQL scripts needed to support data modeling and transformation.

3. Macros: This folder contains reusable SQL code that can be called from data models or transformations.

4. Analysis: This folder contains SQL scripts that perform data analysis or generate reports.

5. Tests: This folder contains SQL scripts that test the validity of data models or transformations.

6. dbt_project.yml: This file defines the configuration settings for the DBT project, such as the target database and credentials, and other project-specific settings.

7. profiles.yml: This file contains the database connection information, such as the host, username, password, and database name.

8. Documentation: This folder contains documentation generated by DBT about the data models, tests, and macros defined in the project.

By organizing a DBT project in this way, it becomes easier to manage and maintain data pipelines, collaborate with other team members, and implement automated testing and validation.

## Core Concepts in DBT Data Modeling

* Data Model -- what is it?
* [ TODO: Diagram HERE ]

This is a nice article:

https://www.getdbt.com/analytics-engineering/modular-data-modeling-technique/

<img src="https://www.getdbt.com/ui/img/guides/analytics-engineering/intermediate_data_models.png" width="50%" height="50%" />

A DBT data model is a SQL query that defines a specific view of data in a data warehouse. The data model can include joins, filters, aggregations, and other transformations that shape the data into a format that's easier to work with for downstream analysis and reporting.

DBT models are defined using SQL syntax and can be composed of other models or database tables. Models are defined in separate SQL files, and DBT provides a mechanism for organizing models into a modular structure.

DBT models are incremental, which means that DBT only processes the new or changed data since the last time the model was run. This makes DBT models more efficient than traditional ETL processes that require processing all of the data each time.

DBT data models are part of a larger data pipeline that transforms raw data into a format that's more useful for data analysis and reporting. By using DBT to define data models, analysts can build complex data pipelines that are modular, maintainable, and easy to test and validate.






# Summary

In this blog post we gave you an overview of DBT and then showed how to build a simple "Hello World"-style of application. For more information on DBT, check out their documentation. For more information on cloud infrastructure, check out the rest of the articles in our blog.

We also offer private workshops for companies on topics such as creating and running DBT pipelines, please feel free to reach out if you'd like to discuss attending one of our workshops.