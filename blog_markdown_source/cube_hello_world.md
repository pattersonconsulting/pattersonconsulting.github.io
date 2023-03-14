---
layout: post
published-on: February 15th 2023
author: Josh Patterson
title: Cube Hello World
subtitle: Understanding the Basics of Building a Data Application with Cube
description: In this post we'll .....
keywords: cube, snowflake, snowpark, automl, AutoGluon, pandas, dataframe, whl, pip, anaconda, dependency
meta_og_image: pct_autogluon_dep_og_card.jpg
---

# Introduction to Cube

Other entries in this series:


## What is Cube?

[ todo ]

Cube.js is an open-source framework for building analytical web applications. It provides a set of tools and APIs to create customizable dashboards, reports, and data visualizations, allowing developers to quickly build interactive applications that can access and query data from multiple sources.

The main goal of Cube.js is to simplify the process of building analytical applications and provide a consistent, efficient way of accessing and processing data. It supports various data sources such as SQL databases, MongoDB, Google BigQuery, and many more. It also provides features for data modeling, schema definition, and query optimization, allowing developers to quickly iterate on their data models and queries to achieve better performance and accuracy.

With Cube.js, developers can create interactive dashboards and visualizations using popular frontend frameworks like React, Angular, and Vue.js. It also provides a set of APIs to enable advanced analytics functionality such as real-time data processing, predictive analytics, and machine learning.

Overall, Cube.js is a powerful tool for building analytical web applications and enables developers to quickly create interactive and data-driven applications with ease.

## Role in Analytics


* why would we use Cube?

[ Todo ]

### what does Cube replace?

[ Todo ]

## Anatomy of a Cube Project

[ Todo ]


## Core Concepts in Cube Data Modeling

* Data Model -- what is it?
* [ TODO: Diagram HERE ]

[ Todo ]

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

```
https://duckdb.org/docs/installation/index

pip3 install dbt-duckdb

```

The latest supported version targets dbt-core 1.1.x and duckdb 0.3.2.

### Using DBT Locally vs Using DBT in the Cloud

* need to reference [ exploratory vs enterprise data pipelines here ]
* Josh Wills notes on why he used DBT with DuckDB

### Load Some Synthetic Patient Data Into DuckDB

* load the doctor visit csv file into DuckDB
* make note of the path



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




### Run DBT Pipeline Locally

```
dbt run
```



### Run DBT Pipeline from Github


# Summary

In this blog post we gave you an overview of DBT and then showed how to build a simple "Hello World"-style of application. For more information on DBT, check out their documentation. For more information on cloud infrastructure, check out the rest of the articles in our blog.

We also offer private workshops for companies on topics such as creating and running DBT pipelines, please feel free to reach out if you'd like to discuss attending one of our workshops.