---
layout: post
published-on: February 15th 2023
author: Josh Patterson
title: DBT Hello World with DuckDB
subtitle: Understanding the Basics of Building a Data Pipeline with DBT
description: In this post we'll .....
keywords: snowflake, duckdb, dbt, data engineering, cicd, sql
meta_og_image: pct_autogluon_dep_og_card.jpg
---

# Introduction

DBT is ...

DuckDB is ...

Together, with the `dbt-duckdb` project, they form a "Modern Data Stack In A Box" --- or a simple and powerful data lakehouse (sans Java and Scala).

> dbt is the best way to manage a collection of data transformations written in SQL or Python for analytics and data science. dbt-duckdb is the project that ties DuckDB and dbt together, allowing you to create a Modern Data Stack In A Box or a simple and powerful data lakehouse- no Java or Scala required.


https://duckdb.org/2022/10/12/modern-data-stack-in-a-box.html

What will we do in this article:

* prepare some metrics from raw patient checkup visit data for use in a machine learning pipeline
* we'll use DBT to produce the summary statistics, or metrics, from the raw data sitting in DuckDB
* We use DuckDB here as a simple local option so as to not force the reader to set up any cloud infrastructure


What will I learn from this article?

* a gentle introduction to DBT and DuckDB
* an understanding of how DBT fits into modern data pipelines
* an understanding of how DuckDB and DBT together can create a simple data stack for local analysis



## Building Our DBT Hello World Project with Synthetic Patient Data

In our "hello world" scenario, we want to build some metrics about how often a set of patients get their yearly physical checkup. The hypothetical company here is an insurance company evaluating a set of customers and building forecasts with machine learning to predict how much the customer will potentially cost in terms of healthcare while under an insurance policy.


Patient Metrics

> "The most granular form of data, Metrics describe the exact numbers that make up the data. Put more simply, they are the raw ingredients that make analytics possible. On their own, they may not actually be very helpful, but studied in the right context (foreshadow alert -- this is analysis), they can be used to give fact-based direction to your decision-making.""

Examples of metrics in the Marketing Data world: 

* Number of Users
* Sessions
* Pageviews
* Event actions

> "All of these units of measurement report activity or results of very specific user interactions in your marketing efforts"


The data engineering team has requested that the analysts pull the data from the (cloud) data warehouse and provide the metrics per customer for use in their modeling experiments as a feature.

In this exercise you'll take synthetic patient checkup history data (which insurance companies are able to access) and use DBT to build data models and produce the patient metrics. We'll use DuckDB for our database as its a quick and easy database to use locally and keeps us from having to provision cloud infrastructure for a simple Hello World example.


# Building a Local Data Stack with DBT and DuckDB

So let's get started by first describing our data.

The Synthetic Patient Doctor Visit Data is shown below:


```
Date,PatientID
2016-09-05,pid-001
2015-08-17,pid-002
2013-07-18,pid-003
2015-09-22,pid-003
2015-10-13,pid-003
2019-01-08,pid-003
2021-07-24,pid-003

```


Using DBT Locally vs Using DBT in the Cloud

* need to reference [ exploratory vs enterprise data pipelines here ]
* Josh Wills notes on why he used DBT with DuckDB


Our tasks for this exercise are listed below:
 
* Create a new conda environment
* install DuckDB and connector dbt-duckdb
* load raw synthetic patient checkup data into DuckDB
* Create a new DBT project
* Configure/Test the DBT project for access to DuckDB
* Run our DBT pipeline

Let's start off by building a new environemnt in Conda for our project.

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

## Working with DuckDB

JD Long: 

> "DuckDB on a single large machine doing transformations against parquet files with SQL"


From MotherDuck Post: https://www.linkedin.com/feed/update/urn%3Ali%3Aactivity%3A7037465343019147265/?origin=SHARED_BY_YOUR_NETWORK

> Combining #duckdb with #dbt for a small side project that is purely SQL-based can be a game-changer.
> DuckDB offers an excellent way to solve complex problems using SQL, while dbt provides an effective structure to the project. Using dbt with DuckDB allows you to add tests to ensure your solution works even after refactoring.
> Plus, you can easily share the whole code project next to the data, could it be CSVs or standing on a public S3 bucket.

### What is DuckDB Typically Used For?

https://dlthub.com/docs/blog/duckdb-1M-downloads-users

* Normie Use Cases -- this is compelling 
* Local Data Workflows Are Going Mainstream, and DuckDB Is at the Center

### Install DBT and DuckDB Connector

[ DuckDB and DBT for this one locally? ]

https://github.com/jwills/dbt-duckdb


https://docs.getdbt.com/reference/warehouse-setups/duckdb-setup

> DuckDB is an embedded database, similar to SQLite, but designed for OLAP-style analytics instead of OLTP. The only configuration parameter that is required in your profile (in addition to type: duckdb) is the path field, which should refer to a path on your local filesystem where you would like the DuckDB database file (and it's associated write-ahead log) to be written. You can also specify the schema parameter if you would like to use a schema besides the default (which is called main).



Quote from the website:

> DuckDB is an embedded database, similar to SQLite, but designed for OLAP-style analytics. It is crazy fast and allows you to read and write data stored in CSV and Parquet files directly, without requiring you to load them into the database first.

> dbt is the best way to manage a collection of data transformations written in SQL or Python for analytics and data science. dbt-duckdb is the project that ties DuckDB and dbt together, allowing you to create a Modern Data Stack In A Box or a simple and powerful data lakehouse- no Java or Scala required.


https://duckdb.org/2022/10/12/modern-data-stack-in-a-box.html

https://docs.getdbt.com/reference/warehouse-setups/duckdb-setup

Install duckdb, dbt, and the connector:

https://duckdb.org/docs/installation/index


```

pip3 install dbt-duckdb

```

The latest supported version targets dbt-core 1.1.x and duckdb 0.3.2.

### DuckDB CLI

We still need the CLI to load some data into DuckDB:


The DuckDB CLI (Command Line Interface) is a single, dependency free executable.

( todo: explain why the CLI is seperate )




### Load Some Synthetic Patient Data Into DuckDB


crank up the local DuckDB instance with the command:

```
./duckdb my_db_name.duckdb
```

Note: if you don't give it a database name at start, for some ODD REASON, DuckDB will not let you save the in-memory db later.

* working with raw data with duckdb

```
select * from './patient_checkup_logs.csv';
```

This should show:

```console

┌────────────┬────────────┐
│    Date    │ Patient ID │
│    date    │  varchar   │
├────────────┼────────────┤
│ 2016-09-05 │ pid-001    │
│ 2015-08-17 │ pid-002    │
│ 2013-07-18 │ pid-003    │
│ 2015-09-22 │ pid-003    │
│ 2015-10-13 │ pid-003    │
│     ·      │    ·       │
│     ·      │    ·       │
│     ·      │    ·       │
│ 2019-12-19 │ pid-1336   │
│ 2020-01-14 │ pid-1336   │
│ 2020-09-23 │ pid-1336   │
├────────────┴────────────┤
│  6808 rows (40 shown)   │
└─────────────────────────┘
```

* load the doctor visit csv file into DuckDB


```
CREATE TABLE patient_visits AS SELECT * FROM read_csv_auto ('./patient_checkup_logs.csv');
D select * from patient_visits;
┌────────────┬────────────┐
│    Date    │ PatientID  │
│    date    │  varchar   │
├────────────┼────────────┤
│ 2016-09-05 │ pid-001    │
│ 2015-08-17 │ pid-002    │
│ 2013-07-18 │ pid-003    │
│ 2015-09-22 │ pid-003    │
│ 2015-10-13 │ pid-003    │
│     ·      │    ·       │
│     ·      │    ·       │
│     ·      │    ·       │
│ 2019-12-11 │ pid-1338   │
│ 2020-02-26 │ pid-1338   │
│ 2020-10-02 │ pid-1338   │
├────────────┴────────────┤
│  6808 rows (40 shown)   │
└─────────────────────────┘

```

* make note of the path


```
describe table patient_visits;

┌─────────────┬─────────────┬─────────┬─────────┬─────────┬─────────┐
│ column_name │ column_type │  null   │   key   │ default │  extra  │
│   varchar   │   varchar   │ varchar │ varchar │ varchar │ varchar │
├─────────────┼─────────────┼─────────┼─────────┼─────────┼─────────┤
│ Date        │ DATE        │ YES     │         │         │         │
│ PatientID   │ VARCHAR     │ YES     │         │         │         │
└─────────────┴─────────────┴─────────┴─────────┴─────────┴─────────┘
```

Now that we have our raw data loaded into DuckDB, we can start building our DBT pipeline.

# Building Our First DBT Pipeline for Patient Metrics

We need to do 3 things before we can run our DBT pipeline:

1. Configure our DBT Profile so that the dbt-duckdb connector can talk to our duckdb database
2. Create an initial DBT project to hold our DBT pipeline SQL code
3. Write our specific SQL data modeling code in the DBT project

Once we have these 3 things done, we can run our project and have it produce the materialized tables inside duckdb that hold the Patient checkup data metrics.

Let's dig into how to configure our DBT profile next.


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




### Confirm DBT Profile Connection Works


Try the following command:

```
dbt debug
```

we'll see:

```
18:45:48  Running with dbt=1.4.5
dbt version: 1.4.5
python version: 3.9.2
python path: /usr/local/opt/python@3.9/bin/python3.9
os info: macOS-10.16-x86_64-i386-64bit
Using profiles.yml file at /Users/josh/.dbt/profiles.yml
Using dbt_project.yml file at /Users/josh/Documents/PattersonConsulting/workspaces/dbt_demos/dbt_hello_world/dbt_hello_world/dbt_project.yml

Configuration:
  profiles.yml file [OK found and valid]
  dbt_project.yml file [OK found and valid]

Required dependencies:
 - git [OK found]

Connection:
  database: dbt_patient_visits
  schema: main
  path: /tmp/dbt_patient_visits.duckdb
  Connection test: [OK connection ok]

All checks passed!
```

### DuckDB and Raw File Materializations

from JWills github:

```
One of DuckDB's most powerful features is its ability to read and write CSV and Parquet files directly, without needing to import/export them from the database first. In dbt-duckdb, we support creating models that are backed by external files via the external materialization strategy:
```


## Write Our First DBT Data Model

What does our data model look like?

```
{{ config(materialized='table') }}

with patient_data as (

    select count(Date) as visits, PatientID from patient_visits group by PatientID

)

select *
from patient_data

```

### Configuring the Models to Materialize in 'dbt_project.yml'


```
# Configuring models
# Full documentation: https://docs.getdbt.com/docs/configuring-models

# In this example config, we tell dbt to build all models in the example/ directory
# as tables. These settings can be overridden in the individual model files
# using the `{{ config(...) }}` macro.
models:
  dbt_duckdb_test:
    # Config indicated by + and applies to all files under models/example/
    housing:
      +materialized: view
```

where:

* 'dbt_duckdb_test': this is the name of the project
* 'housing': maps to a subdirectory named 'housing' under the 'models' subdirectory (e.g., "dbt_duckdb_test/models/housing/")

and inside the 'housing/' subdirectory, there should be at least:

* `schema.yml`: contains the names of the models represented by .sql files in the same subdirectory
* 1 or more .sql files referenced in `schema.yml`


#### Schema.yml



```

version: 2

models:
  - name: patient_visits_summed_model
    description: "A starter duckdb dbt model"
    columns:
      - name: PatientID
        description: "The primary key for this table"
        tests:
          - unique
          - not_null
      - name: visits
        description: "the summed visits across time for this patient"
  - name: patient_visits_summed_over_5
    description: "Only Patients who made at least 5 visits"
    columns:
      - name: PatientID
        description: "The primary key for this table"
        tests:
          - unique
          - not_null
      - name: visits
        description: "the summed visits across time for this patient"

```

#### patient_visits_summed_model.sql

```
{{ config(materialized='table') }}

with patient_data as (

    select count(Date) as visits, PatientID from patient_visits group by PatientID

)

select *
from patient_data
```

#### patient_visits_summed_over_5.sql

```

{{ config(materialized='table') }}

with patient_data_summed as (

    select * from {{ref('patient_visits_summed_model')}} where visits >= 5

)

select *
from patient_data_summed
```

if you'll notice in the second model (patient_visits_summed_over_5.sql), we are referring to the first model (patient_visits_summed_model.sql). 


As explained in the dbt docs:

https://docs.getdbt.com/reference/dbt-jinja-functions/ref

```
The most important function in dbt is ref(); it's impossible to build even moderately complex models without it. ref() is how you reference one model within another. This is a very common behavior, as typically models are built to be "stacked" on top of one another.
```



## Run DBT Pipeline Locally

```
dbt run
```

and we should see:

```
20:39:59  Running with dbt=1.4.5
20:39:59  Found 2 models, 4 tests, 0 snapshots, 0 analyses, 296 macros, 0 operations, 0 seed files, 0 sources, 0 exposures, 0 metrics
20:39:59  
20:39:59  Concurrency: 1 threads (target='dev')
20:39:59  
20:39:59  1 of 2 START sql table model main.patient_visits_summed_model .................. [RUN]
20:39:59  1 of 2 OK created sql table model main.patient_visits_summed_model ............. [OK in 0.08s]
20:39:59  2 of 2 START sql table model main.patient_visits_summed_over_5 ................. [RUN]
20:39:59  2 of 2 OK created sql table model main.patient_visits_summed_over_5 ............ [OK in 0.03s]
20:39:59  
20:39:59  Finished running 2 table models in 0 hours 0 minutes and 0.19 seconds (0.19s).
20:39:59  
20:39:59  Completed successfully
20:39:59  
20:39:59  Done. PASS=2 WARN=0 ERROR=0 SKIP=0 TOTAL=2
```

### Check DuckDB Materialized Tables

```
select * from patient_visits_summed_over_5;
┌────────┬───────────┐
│ visits │ PatientID │
│ int64  │  varchar  │
├────────┼───────────┤
│      5 │ pid-003   │
│      7 │ pid-004   │
│      7 │ pid-005   │
│      8 │ pid-006   │
│      8 │ pid-008   │
│      5 │ pid-009   │
│      5 │ pid-010   │
│      7 │ pid-012   │
│      6 │ pid-013   │
│      5 │ pid-015   │
│     10 │ pid-016   │
│      8 │ pid-017   │
│      6 │ pid-018   │
│      6 │ pid-019   │
│     10 │ pid-020   │
│      5 │ pid-021   │
│      5 │ pid-022   │
│     10 │ pid-023   │
│      8 │ pid-025   │
│     10 │ pid-027   │
│      · │    ·      │
│      · │    ·      │
│      · │    ·      │
│      7 │ pid-1271  │
│      7 │ pid-254   │
│      8 │ pid-795   │
│      7 │ pid-1126  │
│      5 │ pid-940   │
│      7 │ pid-986   │
│      8 │ pid-1135  │
│      6 │ pid-1141  │
│     10 │ pid-1208  │
│      7 │ pid-1235  │
│     10 │ pid-1302  │
│     10 │ pid-556   │
│     10 │ pid-695   │
│      9 │ pid-1123  │
│      6 │ pid-1332  │
│      9 │ pid-617   │
│      6 │ pid-1112  │
│     10 │ pid-1308  │
│      8 │ pid-979   │
│      6 │ pid-889   │
├────────┴───────────┤
│      758 rows      │
│     (40 shown)     │
└────────────────────┘

```



### Run DBT Pipeline from Github


# Summary

In this blog post we gave you an overview of DBT and then showed how to build a simple "Hello World"-style of application. For more information on DBT, check out their documentation. For more information on cloud infrastructure, check out the rest of the articles in our blog.

We also offer private workshops for companies on topics such as creating and running DBT pipelines, please feel free to reach out if you'd like to discuss attending one of our workshops.