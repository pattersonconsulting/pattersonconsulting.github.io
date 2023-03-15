---
layout: post
published-on: February 15th 2023
author: Josh Patterson
title: DBT Hello World
subtitle: Understanding the Basics of Building a Data Pipeline with DBT
description: In this post we'll .....
keywords: snowflake, snowpark, automl, AutoGluon, pandas, dataframe, whl, pip, anaconda, dependency
meta_og_image: pct_autogluon_dep_og_card.jpg
---

# Introduction to DBT

Other entries in this series:


## What is DBT?

DBT (Data Build Tool) is an open-source command-line tool that allows data analysts and engineers to transform and manipulate data in their data warehouse. It provides a framework for creating and executing complex SQL queries and transforms, and it helps manage the entire data transformation process.

DBT is designed to work with a variety of data warehouses, including Snowflake, BigQuery, Redshift, and others. It allows users to define data models and transformations in a modular way, and it supports version control and collaboration through Git.

With DBT, analysts can define reusable SQL code and maintain a consistent data model across their organization. They can also build automated testing and validation into their data pipelines, ensuring data accuracy and consistency. Overall, DBT helps organizations build data pipelines that are maintainable, scalable, and easy to understand.

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


# Building Our DBT Hello World Project with Synthetic Patient Data

* conda env creation
* install duckDB and connector
* load raw data into DuckDB
* dbt init [project]
* configuring connection to snowflake

## The Synthetic Patient Doctor Visit Data

* [ describe the data here ]

## Create Environment in Conda


To create an environment in Conda, you can follow these steps:

1. Open your terminal (or Anaconda Prompt on Windows).

2. Type the following command to create a new environment named my_env (you can replace my_env with your preferred name):

```
conda create --name my_env
```

3. Conda will ask you to confirm the installation of any additional packages that are required to create the environment. Type y and press Enter to proceed.

4. Once the environment is created, activate it by typing:

```

```

5. Your prompt should now show the name of the environment in parentheses, indicating that it's active.

6. You can now install any packages you need for your project using conda install or pip install.

7. When you're done working in the environment, you can deactivate it by typing:

```
conda deactivate
```


## Install DBT and DuckDB Connector

[ DuckDB and DBT for this one locally? ]

https://github.com/jwills/dbt-duckdb

Quote from the website:

`DuckDB is an embedded database, similar to SQLite, but designed for OLAP-style analytics. It is crazy fast and allows you to read and write data stored in CSV and Parquet files directly, without requiring you to load them into the database first.`

`dbt is the best way to manage a collection of data transformations written in SQL or Python for analytics and data science. dbt-duckdb is the project that ties DuckDB and dbt together, allowing you to create a Modern Data Stack In A Box or a simple and powerful data lakehouse- no Java or Scala required.`

Install duckdb, dbt, and the connector:

```
https://duckdb.org/docs/installation/index

pip3 install dbt-duckdb

```

The latest supported version targets dbt-core 1.1.x and duckdb 0.3.2.

### DuckDB CLI

We still need the CLI to load some data into DuckDB:


The DuckDB CLI (Command Line Interface) is a single, dependency free executable.

( todo: explain why the CLI is seperate )

### Load our Synthetic Insurance Data into DuckDB


`create table fips_test (fips_code VARCHAR, county VARCHAR, state VARCHAR);`

Confirm we can get to the data:

`select * from './data/test_fips_data.csv';`

Now copy the raw data into our table:

`copy fips_test from './data/test_fips_data.csv' (AUTO_DETECT TRUE);`

and then:

`show tables;`

### Connecting to our local DuckDB Install with the `dbt-duckdb` Connector:

https://docs.getdbt.com/reference/warehouse-setups/duckdb-setup

`DuckDB is an embedded database, similar to SQLite, but designed for OLAP-style analytics instead of OLTP. The only configuration parameter that is required in your profile (in addition to type: duckdb) is the path field, which should refer to a path on your local filesystem where you would like the DuckDB database file (and it's associated write-ahead log) to be written. You can also specify the schema parameter if you would like to use a schema besides the default (which is called main).`


### Using DBT Locally vs Using DBT in the Cloud

* need to reference [ exploratory vs enterprise data pipelines here ]
* Josh Wills notes on why he used DBT with DuckDB

### Load Some Synthetic Patient Data Into DuckDB


* working with raw data with duckdb

```
select * from './march_2023_patient_data_load/patient_checkup_logs.csv';
┌────────────┬────────────┐
│    Date    │ Patient ID │
│    date    │  varchar   │
├────────────┼────────────┤
│ 2016-09-05 │ pid-001    │
│ 2015-08-17 │ pid-002    │
│ 2013-07-18 │ pid-003    │
│ 2015-09-22 │ pid-003    │
│ 2015-10-13 │ pid-003    │
│ 2019-01-08 │ pid-003    │
│ 2021-07-24 │ pid-003    │
│ 2014-04-12 │ pid-004    │
│ 2014-06-01 │ pid-004    │
│ 2020-10-22 │ pid-004    │
│ 2020-10-29 │ pid-004    │
│ 2021-01-01 │ pid-004    │
│ 2022-03-12 │ pid-004    │
│ 2022-05-15 │ pid-004    │
│ 2014-02-05 │ pid-005    │
│ 2016-04-24 │ pid-005    │
│ 2016-08-27 │ pid-005    │
│ 2016-12-13 │ pid-005    │
│ 2017-01-25 │ pid-005    │
│ 2018-07-31 │ pid-005    │
│     ·      │    ·       │
│     ·      │    ·       │
│     ·      │    ·       │
│ 2019-12-19 │ pid-1336   │
│ 2020-01-14 │ pid-1336   │
│ 2020-09-23 │ pid-1336   │
│ 2021-02-07 │ pid-1336   │
│ 2022-09-12 │ pid-1336   │
│ 2014-02-07 │ pid-1337   │
│ 2018-01-04 │ pid-1337   │
│ 2018-11-14 │ pid-1337   │
│ 2019-05-22 │ pid-1337   │
│ 2020-01-10 │ pid-1337   │
│ 2020-04-13 │ pid-1337   │
│ 2021-01-30 │ pid-1337   │
│ 2021-11-17 │ pid-1337   │
│ 2022-03-27 │ pid-1337   │
│ 2022-07-22 │ pid-1337   │
│ 2016-01-29 │ pid-1338   │
│ 2019-05-24 │ pid-1338   │
│ 2019-12-11 │ pid-1338   │
│ 2020-02-26 │ pid-1338   │
│ 2020-10-02 │ pid-1338   │
├────────────┴────────────┤
│  6808 rows (40 shown)   │
└─────────────────────────┘
```

* load the doctor visit csv file into DuckDB


```
CREATE TABLE t1 AS SELECT * FROM read_csv_auto ('./march_2023_patient_data_load/patient_checkup_logs.csv');
D select * from t1;
┌────────────┬────────────┐
│    Date    │ Patient ID │
│    date    │  varchar   │
├────────────┼────────────┤
│ 2016-09-05 │ pid-001    │
│ 2015-08-17 │ pid-002    │
│ 2013-07-18 │ pid-003    │
│ 2015-09-22 │ pid-003    │
│ 2015-10-13 │ pid-003    │
│ 2019-01-08 │ pid-003    │
│ 2021-07-24 │ pid-003    │
│ 2014-04-12 │ pid-004    │
│ 2014-06-01 │ pid-004    │
│ 2020-10-22 │ pid-004    │
│ 2020-10-29 │ pid-004    │
│ 2021-01-01 │ pid-004    │
│ 2022-03-12 │ pid-004    │
│ 2022-05-15 │ pid-004    │
│ 2014-02-05 │ pid-005    │
│ 2016-04-24 │ pid-005    │
│ 2016-08-27 │ pid-005    │
│ 2016-12-13 │ pid-005    │
│ 2017-01-25 │ pid-005    │
│ 2018-07-31 │ pid-005    │
│     ·      │    ·       │
│     ·      │    ·       │
│     ·      │    ·       │
│ 2019-12-19 │ pid-1336   │
│ 2020-01-14 │ pid-1336   │
│ 2020-09-23 │ pid-1336   │
│ 2021-02-07 │ pid-1336   │
│ 2022-09-12 │ pid-1336   │
│ 2014-02-07 │ pid-1337   │
│ 2018-01-04 │ pid-1337   │
│ 2018-11-14 │ pid-1337   │
│ 2019-05-22 │ pid-1337   │
│ 2020-01-10 │ pid-1337   │
│ 2020-04-13 │ pid-1337   │
│ 2021-01-30 │ pid-1337   │
│ 2021-11-17 │ pid-1337   │
│ 2022-03-27 │ pid-1337   │
│ 2022-07-22 │ pid-1337   │
│ 2016-01-29 │ pid-1338   │
│ 2019-05-24 │ pid-1338   │
│ 2019-12-11 │ pid-1338   │
│ 2020-02-26 │ pid-1338   │
│ 2020-10-02 │ pid-1338   │
├────────────┴────────────┤
│  6808 rows (40 shown)   │
└─────────────────────────┘

```

* make note of the path


```
describe table t1;

┌─────────────┬─────────────┬─────────┬─────────┬─────────┬─────────┐
│ column_name │ column_type │  null   │   key   │ default │  extra  │
│   varchar   │   varchar   │ varchar │ varchar │ varchar │ varchar │
├─────────────┼─────────────┼─────────┼─────────┼─────────┼─────────┤
│ Date        │ DATE        │ YES     │         │         │         │
│ Patient ID  │ VARCHAR     │ YES     │         │         │         │
└─────────────┴─────────────┴─────────┴─────────┴─────────┴─────────┘
```


## Configure DBT Profile to Connect to DuckDB Database

To configure DBT to connect to a database, you need to create a configuration file called profiles.yml. This file should contain the necessary connection information for each database you want to connect to.

On OSX, the DBT profile.yml file lives at:

```
cat ~/.dbt/profiles.yml
```

### General Notes on Editing profile.yml

Here are the general steps to configure DBT to connect to a database:

1. Open a text editor and create a new file called profiles.yml in the root directory of your DBT project.

2. Inside the profiles.yml file, define a profile for each database you want to connect to. The profile should include the database type (e.g., postgres, redshift, etc.), host, port, database name, username, and password. Here's an example profile for a PostgreSQL database:

```
my_database:
  target: dev
  outputs:
    dev:
      type: postgres
      host: myhostname.com
      port: 5432
      dbname: mydatabase
      user: myusername
      password: mypassword
      schema: myschema
      threads: 4
      keepalives_idle: 0
```

3. Save the profiles.yml file.

4. In your DBT project, you can now reference the profile name in your dbt_project.yml file. For example, if your profile is called my_database, you can reference it like this:

```
# dbt_project.yml
...
profile: my_database
...
```

5. Once you've configured your profiles, you can run DBT commands like dbt run or dbt test to execute your DBT project against the specified database.

That's it! With these steps, you can configure DBT to connect to a database and start building data models and pipelines.

### Configure the Profile for DuckDB

```
dbt_duckdb_test:
  target: dev
  outputs:
    dev:
      type: duckdb
      path: '...../workspaces/snowpark_demos/duckdb/fips_test_db'
      #optional fields
      #schema: schema_name 
```

## Initialize DBT Project

From:
https://docs.getdbt.com/docs/building-a-dbt-project/projects

```
dbt init [project_name]
```

So here we can just use:

```
dbt init
20:04:41  Running with dbt=1.1.1
20:04:41  Setting up your profile.
The profile dbt_duckdb_test already exists in /Users/josh/.dbt/profiles.yml. Continue and overwrite it? [y/N]: N
```

And then let's check out what was generated:

```
ls -la

total 24
drwxr-xr-x  12 josh  staff   384 Jul 28 16:04 .
drwxr-xr-x   7 josh  staff   224 Jul 28 16:02 ..
-rw-r--r--   1 josh  staff    29 Jul 27 15:00 .gitignore
-rw-r--r--   1 josh  staff   571 Jul 27 15:00 README.md
drwxr-xr-x   3 josh  staff    96 Jul 27 15:00 analyses
-rw-r--r--   1 josh  staff  1349 Jul 28 16:02 dbt_project.yml
drwxr-xr-x   3 josh  staff    96 Jul 28 16:04 logs
drwxr-xr-x   3 josh  staff    96 Jul 27 15:00 macros
drwxr-xr-x   3 josh  staff    96 Jul 27 15:00 models
drwxr-xr-x   3 josh  staff    96 Jul 27 15:00 seeds
drwxr-xr-x   3 josh  staff    96 Jul 27 15:00 snapshots
drwxr-xr-x   3 josh  staff    96 Jul 27 15:00 tests
```




## Run DBT Pipeline

### Confirm DBT Profile Connection Works


Try the following command:

```
dbt debug

20:04:52  Running with dbt=1.1.1
dbt version: 1.1.1
python version: 3.8.13
python path: /Users/josh/opt/anaconda3/envs/hurricane_analytics/bin/python
os info: macOS-10.16-x86_64-i386-64bit
Using profiles.yml file at /Users/josh/.dbt/profiles.yml
Using dbt_project.yml file at /Users/josh/Documents/PattersonConsulting/workspaces/snowpark_demos/dbt/dbt_duckdb_test/dbt_project.yml

Configuration:
  profiles.yml file [OK found and valid]
  dbt_project.yml file [OK found and valid]

Required dependencies:
 - git [OK found]

Connection:
  database: main
  schema: main
  path: /Users/josh/Documents/PattersonConsulting/workspaces/snowpark_demos/duckdb/fips_test_db
  Connection test: [OK connection ok]

All checks passed!
```

### Write Our First Data Model

What does our data model look like?

```
--- other dbt stuff ---

select count(Date) as visits, "Patient ID" from t1 group by "Patient ID";

--- other dbt stuff ---

```




### Run DBT Pipeline Locally

```
dbt run
```



### Run DBT Pipeline from Github


# Summary

In this blog post we gave you an overview of DBT and then showed how to build a simple "Hello World"-style of application. For more information on DBT, check out their documentation. For more information on cloud infrastructure, check out the rest of the articles in our blog.

We also offer private workshops for companies on topics such as creating and running DBT pipelines, please feel free to reach out if you'd like to discuss attending one of our workshops.