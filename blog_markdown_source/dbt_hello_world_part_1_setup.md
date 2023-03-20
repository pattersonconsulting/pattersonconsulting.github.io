---
layout: post
published-on: February 15th 2023
author: Josh Patterson
title: DBT Hello World with DuckDB
subtitle: Part 1 of 3 - Setting up a Local Data Stack with DBT and DuckDB
description: Part 1 of 3 - In this post we'll set up a local data stack with DBT and DuckDB to prepare for building our first DBT workflow in Part 2 of this series.
keywords: snowflake, duckdb, dbt, data engineering, cicd, sql
meta_og_image: pct_dbt_duckdb_og_card.jpg
---

# Introduction

[DBT](https://www.getdbt.com/) (Data Build Tool) is an open-source command-line tool that allows data analysts and data engineers a way to manage a collection of data transformations written in SQL or Python for analytics and data science. It provides a framework for creating and executing complex SQL queries and transforms, and it helps manage the entire data transformation process.

More simply, DBT is focused on transforming data --- the 'T' in ELT.

[DuckDB](https://duckdb.org/) is an embedded database (think "SQLite"), but designed for OLAP-style analytics instead of OLTP. DuckDB is exceptionally fast and lets you work directly with data stored in files such as CSV and Parquet files directly, without forcing you to do any load operations first.

Together, with the [`dbt-duckdb`](https://github.com/jwills/dbt-duckdb) project, they form a ["Modern Data Stack In A Box"](https://duckdb.org/2022/10/12/modern-data-stack-in-a-box.html) --- or a simple and powerful data lakehouse (sans Java and Scala).

This is part 1 in a 3 part series on using DBT and DuckDB

* Part 1: [Setup Environment](./dbt_hello_world_part_1_setup.html)
* Part 2: [Build the Pipeline](./dbt_hello_world_part_2_pipeline.html)
* Part 3: Epilogue: What is DBT?

In Part 1 of 3 of this tutorial you will:

* prepare an intermediate dbt data model from raw patient checkup visit data for use by data engineers downstream in a machine learning pipeline
* use DBT to produce the summary aggregation as a data model from the raw data sitting in DuckDB
* use DuckDB here as a simple local option so as to not force the reader to set up any cloud infrastructure

Further, you'll learn:

* a gentle introduction to DBT and DuckDB
* an understanding of how DBT fits into modern data pipelines
* an understanding of how DuckDB and DBT together can create a simple data stack for local analysis

We'll build our DBT "Hello World" project with synthetic patient data.

## Building Our DBT Hello World Project with Synthetic Patient Data

In our "hello world" scenario, we want to build a summarization of how often a set of patients get their yearly physical checkup. The hypothetical company here is an insurance company ("InsurCo") evaluating a set of customers and building forecasts with machine learning to predict how much the customer will potentially cost in terms of healthcare while under an insurance policy.

## The Scenario

The data engineering team has requested that the analysts pull the data from the (cloud) data warehouse and provide the a consistent calculation per customer for use in their modeling experiments as a feature.

In this exercise you'll take synthetic patient checkup history data (which insurance companies are able to access) and use DBT to build data models and produce the patient checkup summary data model (e.g., "cached table in the database"). We'll use DuckDB for our database as its a quick and easy database to use locally and keeps us from having to provision cloud infrastructure for a simple Hello World example.

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

So let's dig into building a local data stack.

# Building a Local Data Stack with DBT and DuckDB

Our tasks for this exercise are listed below:

* Part 1: Setup
   * Create a new conda environment
   * install DuckDB and connector dbt-duckdb
   * load raw synthetic patient checkup data into DuckDB
* In Part 2: Build the Pipeline
   * Create a new DBT project
   * Configure/Test the DBT project for access to DuckDB
   * Run our DBT pipeline

Let's start off by building a new environemnt in Conda for our project.

## Create Environment in Conda

To create an environment in Conda, you can follow these steps:

1. Open your terminal (or Anaconda Prompt on Windows).

2. Type the following command to create a new environment named my_env (you can replace my_env with your preferred name):

```
conda create --name [my_env]
```

3. Conda will ask you to confirm the installation of any additional packages that are required to create the environment. Type y and press Enter to proceed.

4. Once the environment is created, activate it by typing:

```
conda activate [my_env]
```

5. Your prompt should now show the name of the environment in parentheses, indicating that it's active.

6. You can now install any packages you need for your project using conda install or pip install.

7. When you're done working in the environment, you can deactivate it by typing:

```
conda deactivate
```

Now that we have an environment to work in, let's get started with using DuckDB.

## Working with DuckDB

DuckDB sits in an interesting spot as it offers an excellent way to solve complex problems using SQL while keeping things simple. DuckDB is a columnar, in-memory SQL database designed for analytical workloads. It's key features are:

* Fast query performance with low memory overhead for large datasets
* SQL interface making it easy to use for the broadest audience
* Lightweight database that can be easily installed and run on a local machine, without the need for a separate server or cluster
* Open-source project, which means that it is free to use and can be modified and extended by the community

DuckDB is compelling because you only have to point it at the data file you'd like to work with, giving you a short-cut to running SQL against CSV, Parquet, and other data files. Ease of use and time to insight are two key properties of why DBT has become a key tool for experimenting in the data "lab".

In a conversation with me, JD Long commented that he prefers DuckDB "when the data fits on a single machine so that he doesn't have to stand up a cluster for Spark".

As stated by the DuckDB Website:

> DuckDB is an embedded database, similar to SQLite, but designed for OLAP-style analytics. It is crazy fast and allows you to read and write data stored in CSV and Parquet files directly, without requiring you to load them into the database first.

### What is DuckDB Typically Used For?

A recent article at dlthub.com, ["As DuckDB crosses 1M downloads / month, what do its users do?"](https://dlthub.com/docs/blog/duckdb-1M-downloads-users), had some interesting notes on how DuckDB is being used. Among the use cases, they were seeing DuckDB being used as a processing enging for local data workflows.

They also called out how many users ("Normies") enjoyed the simplicity of the DuckDB user experience . I found both of those usage trends worth of note.

With those points noted, let's move on and install DBT and the dbt-duckdb connector.

## Install DBT and DuckDB Connector

As [described on the website](https://github.com/jwills/dbt-duckdb):

> dbt is the best way to manage a collection of data transformations written in SQL or Python for analytics and data science. dbt-duckdb is the project that ties DuckDB and dbt together, allowing you to create a [Modern Data Stack In A Box](https://duckdb.org/2022/10/12/modern-data-stack-in-a-box.html) or a simple and powerful data lakehouse- no Java or Scala required.

You can also read further about the connector on dbt's website as well:

https://docs.getdbt.com/reference/warehouse-setups/duckdb-setup


This project is hosted on PyPI so we can use pip to install the connector and dependencies:


```

pip3 install dbt-duckdb

```

Once that is installed, we'll need the DuckDB CLI to work directly with DuckDB from the local command line to load our dataset.

### DuckDB CLI

The DuckDB CLI (Command Line Interface) is a single, dependency free executable.

Download it from:

https://duckdb.org/docs/api/cli.html

Make sure and get the version of the CLI that matches the version of DuckDB you have installed locally via pip.

Now let's load some data for analysis.

### Load Some Synthetic Patient Data Into DuckDB

Let's crank up the local DuckDB CLI with the command:

```
./duckdb dbt_patient_visits.duckdb
```

Note: if you don't give it a database name at start, for some ODD REASON, DuckDB will not let you save the in-memory db later.

Once we're inside the CLI the first command you want to know about is how to quit:

```
.q [enter]
```

Typing .q or .quit will quit the CLI and get you back to your shell.

Now, once we're back inside the CLI, let's see if we can access our local patient data in CSV form with the command:

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

The interesting part about the command we just executed is that we used a SQL command to query a raw file as we would a table. DuckDB is quite flexible like that.

Let's quickly load the checkup visit csv file into DuckDB and let DuckDB automatically infer the schema with the `read_csv_auto()` command:


```
CREATE TABLE patient_visits AS SELECT * FROM read_csv_auto ('./patient_checkup_logs.csv');

select * from patient_visits;
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

We now have a table loaded into our DuckDB database, as we can see when we type the following `describe` command:

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

Lastly, let's configure our DBT profile to see DuckDB as a database it can connect to for data processing.

## Configure DBT Profile to Connect to DuckDB Database

To configure DBT to connect to a database, you need to create a configuration file called `profiles.yml`. This file should contain the necessary connection information for each database you want to connect to.

On OSX for example, the DBT profile.yml file lives at:

```
~/.dbt/profiles.yml
```

Let's now edit our `profiles.yml`

### Configure the Profile for DuckDB

In the code listing below, we can see some sample contents of a type `profiles.yml` file:

```

...

dbt_duckdb_patient_visits:
  outputs:
   dev:
     type: duckdb
     path: /Users/josh/Documents/PattersonConsulting/workspaces/dbt_demos/dbt_hello_world/patient_db.duckdb
  target: dev

...

```

The connection we'll use for this demo is `dbt_duckdb_patient_visits` and we'll reference that in our dbt project in a moment. Let's now create a new DBT project.

Now that we have our raw data loaded into DuckDB, we can start building our DBT pipeline in [part 2 of 3](./dbt_hello_world_part_2_pipeline.html) in this blog series.

# Summary / On to Part 2

In this blog post we showed you have to setup a local data stack environment based on DBT and DuckDB. For more information on DBT, check out their documentation. For more information on cloud infrastructure, check out the rest of the articles in our blog.

We also offer private workshops for companies on topics such as creating and running DBT pipelines (on multiple platforms such as Snowflake and Fivetran), please feel free to [reach out](../contact.html) if you'd like to discuss attending one of our workshops.