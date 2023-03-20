---
layout: post
published-on: February 15th 2023
author: Josh Patterson
title: DBT Hello World with DuckDB
subtitle: Part 2 of 3 - Building Our First DBT Pipeline for Patient History Data Summarization
description: In this post we'll build our first DBT pipelineto summarize patient history data for downstream data engineers
keywords: snowflake, duckdb, dbt, data engineering, cicd, sql
meta_og_image: pct_dbt_duckdb_og_card.jpg
---

# Introduction

In this post we'll build our first DBT pipelineto summarize patient history data for downstream data engineers

This is part 2 in a 3 part series on using DBT and DuckDB

* Part 1: [Setup Environment](./dbt_hello_world_part_1_setup.html)
* Part 2: [Build the Pipeline](./dbt_hello_world_part_2_pipeline.html)
* Part 3: Epilogue: What is DBT?

We need to do 3 things before we can run our DBT pipeline:

1. Configure our DBT Profile (`profiles.yml`) so that the dbt-duckdb connector can talk to our duckdb database
2. Create an initial DBT project to hold our DBT pipeline SQL code
3. Write our specific SQL data modeling code in the DBT project

Once we have these 3 things done, we can run our project and have it produce the materialized tables inside duckdb that hold the patient checkup data summarizations.

Let's dig into how to configure our DBT profile next.

# Setting Up a DBT Project

Before we can build our data models, we need to create a new DBT project to represent our DBT workflow. Let's start out by configuring 

## Initialize DBT Project

The top level of a dbt workflow is the [project](https://docs.getdbt.com/docs/building-a-dbt-project/projects). There is a dbt_project.yml file in the main project directory.

The project file tells dbt the project context, and the defined models let dbt know how to build a specific data set.

We can create a project with the `dbt init [name]` as shown below:

```
dbt init [project_name]
```

We'll use a project name of `dbt_hello_world`, and in the directory listing below we can see what was generated inside the directory (`./dbt_hello_world`) created:

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

As DBT themselves state: 

> A dbt project, at its core, is just a folder structure for organizing your individual SQL models. Within the `/models/` folder of a project, any .sql files you publish will be materialized as tables or views to your data warehouse.

In your DBT project, you can now reference the profile name (`dbt_duckdb_patient_visits`) in your `dbt_project.yml` file. In our example you can reference it like this:

```
# dbt_project.yml

...
profile: dbt_duckdb_patient_visits
...

```

Now let's move on to testing our dbt-duckdb connection.

## Confirm DBT Profile Connection Works

Try the following command:

```
dbt debug
```

we should see:

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

If your output looks similar to above, then your `dbt-duckdb` connector was configured correctly and DBT can communicate with DuckDB. Now let's work on writing our first DBT data model.

# Write Our First DBT Workflow

In dbt (Data Build Tool), a data model is a logical representation of a specific type of data that you want to analyze or work with in your database. It describes the structure, relationships, and constraints of the data in a way that can be easily understood by both humans and computers. A DBT workflow is a directed acyclic graph (DAG) of DBT data models.

A data model in dbt is typically defined as a SQL query that defines the relationships between tables or other data sources. It specifies how data should be transformed and aggregated to create a particular view of the data. This view can then be used as a source for further analysis or reporting.

In dbt, a data model is created using a "model" statement in a SQL file. This statement defines the columns of the model, any relationships with other models or tables, and any transformations that should be applied to the data. Once defined, a data model can be used as a building block for creating more complex data structures and analyses.

Data modeling in DBT is meant to replace a large, monolithic SQL file with a DAG of smaller SQL operations that can be used by group of people and orchestrated properly.

https://www.getdbt.com/analytics-engineering/modular-data-modeling-technique/

Moving to this method over the monolithic SQL file style allows us to standardize on transforms for analytics between people or teams and bring consistency to the analytical data output. This allows producers or consumers of data models to start from the foundational data modeling work others have already done.

## Some Quick Notes on Data Modeling Naming Conventions

The data modeling naming conventions in DBT can take some work to figure out, especially depending on what part of the data universe you come from (In another converation with JD Long, he off-handed commented: "all of DBT would make more sene to me if they just used terms like *data flow with cached intermediate data* or something"). Yet, I digress.

Data modeling conventions vary, but 3 common ideas are:

1. [Sources](https://docs.getdbt.com/docs/build/sources): raw tables in the database
1. Staging models: clean up and standardize the raw data coming from the warehouse
2. Intermediate models: where we start applying more complex transformations

In dbt, a staging model is typically used to extract and load data from source systems into a data warehouse or other target system. Staging models often involve basic data transformations, such as renaming columns, filtering rows, or casting data types, but they are primarily focused on moving data from the source to the target.

On the other hand, an intermediate model in dbt is typically used for more complex data transformations that are necessary to create analytical models or other downstream data models. Intermediate models often involve complex SQL queries, joins, and other operations that combine data from multiple sources, perform calculations, or reshape data structures.

In general, the flow of data through a dbt project might involve the following steps: extract data from source systems using staging models, transform the data into a format suitable for analysis using intermediate models, and finally, load the transformed data into analytical models that provide insights and value to end-users.

We can also refer to the raw data as a "source" model, as well, that will feed into the a "staging" model.

With all of that in mind, let's take a quick look at the generated `dbt_project.yml` file for our dbt project.

## Configuring the Models to Materialize in 'dbt_project.yml'

In dbt (Data Build Tool), the `dbt_project.yml` file is a configuration file that defines the settings and parameters for a dbt project. This file is typically located in the root directory of a dbt project, and it controls how dbt operates and interacts with your data sources.

In the code listing below we see the `dbt_project.yml` file for our hello world project:

```

# Name your project! Project names should contain only lowercase characters
# and underscores. A good package name should reflect your organization's
# name or the intended use of these models
name: 'dbt_hello_world'
version: '1.0.0'
config-version: 2

# This setting configures which "profile" dbt uses for this project.
profile: 'dbt_duckdb_patient_visits'

# These configurations specify where dbt should look for different types of files.
# The `model-paths` config, for example, states that models in this project can be
# found in the "models/" directory. You probably won't need to change these!
model-paths: ["models"]
analysis-paths: ["analyses"]
test-paths: ["tests"]
seed-paths: ["seeds"]
macro-paths: ["macros"]
snapshot-paths: ["snapshots"]

target-path: "target"  # directory which will store compiled SQL files
clean-targets:         # directories to be removed by `dbt clean`
  - "target"
  - "dbt_packages"


# Configuring models
# Full documentation: https://docs.getdbt.com/docs/configuring-models

# In this example config, we tell dbt to build all models in the example/
# directory as views. These settings can be overridden in the individual model
# files using the `{{ config(...) }}` macro.
models:
  dbt_hello_world:
    # Config indicated by + and applies to all files under models/example/
    patient_visits_models:
      +materialized: view
```

where:

* `dbt_hello_world`: this is the name of the project
* `patient_visits_models`: maps to a subdirectory named 'patient_visits_models' under the 'models' subdirectory (e.g., "dbt_hello_world/models/patient_visits_models/")

and inside the `patient_visits_models/` subdirectory, there should be at least:

* `schema.yml`: contains the names of the models represented by .sql files in the same subdirectory
* 1 or more .sql files referenced in `schema.yml`

Files with a .sql extension contain SQL code that defines tables, views, and other database objects. These files are used to define the data models that make up a dbt project.


### Schema.yml

In dbt (Data Build Tool), the schema.yml file is used to define the structure and constraints of tables and columns in a database schema. This file is typically located in the same directory as the SQL file that defines a particular table or model, and it provides a way to document and validate the schema of your data.

In the code listing below, we see the file `schema.yml`'s contents:

```


version: 2

sources:
  - name: patient_visits
    schema: main
    description: "The main patient visits raw data table"
    tables:
      - name: patient_visits
        columns:
          - name: PatientID
          - name: Date

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

We can see 2 models listed ("patient_visits_summed_model" and "patient_visits_summed_over_5"), along with a "source"; This source represents the raw tables in our database, DuckDB, and we are listing our table `patient_visits` as a source to work with in our DBT workflow. We'll see that used in a DBT model in a moment.

Overall, the schema.yml file provides a way to define and document the schema of your data in a structured and consistent way, making it easier to understand, maintain, and validate your data over time.

Now let's take a look at the first model, `patient_visits_summed_model`.

### patient_visits_summed_model.sql

In the code listing below, we see the contents of the data model file `patient_visits_summed_model.sql`:

```

{{ config(materialized='table') }}

with patient_data as (

    select count(Date) as visits, PatientID from {{source('patient_visits', 'patient_visits')}} group by PatientID

)

select *
from patient_data

```

We can see it is to be materialized as a table in target database (DuckDB), and we're reading data `from {{source('patient_visits', 'patient_visits')}}`. Since this is a simple Hello World example, we're going ahead and building the aggregation in this "intermediate" model with a `group by` and `count()` operation. The results of this data modeling operation in our DBT workflow give us a list of all patients with how many times total they got a checkup. This intermediate aggregation can be used by other data models in the rest of our DBT workflow, as we'll see next.

### patient_visits_summed_over_5.sql

Now that we have an aggregation of the total checkups for each patient as a data model, we'll create another data model that references the previuos intermediate stage with a new data model that shows only Patients that had more than 5 visits, as seen in the code listing below:


```

{{ config(materialized='table') }}

with patient_data_summed as (

    select * from {{ref('patient_visits_summed_model')}} where visits >= 5

)

select *
from patient_data_summed
```

if you'll notice in the second model (patient_visits_summed_over_5.sql), we are referring to the first model (patient_visits_summed_model.sql) not by file name --- but by logical data model name, `{{ref('patient_visits_summed_model')}}`.

You'll notice the logical name of the data model is the filename without the .sql extension.

We refer to other logical data models in DBT with the `ref` function, as explained in the dbt docs:

https://docs.getdbt.com/reference/dbt-jinja-functions/ref


> The most important function in dbt is ref(); it's impossible to build even moderately complex models without it. ref() is how you reference one model within another. This is a very common behavior, as typically models are built to be "stacked" on top of one another.

These models are stacked on top of one another, linked with the ref() function, creating a DAG that can be executed on different type of backend data warehouse systems (e.g., cloud, MPP, embedded, etc).

Now, let's run our full DBT workflow DAG locally.

## Run DBT Pipeline Locally

Let's now crank up our DBT workflow.

It's worth noting that you are running a model that will transform your data without that data ever leaving your warehouse when you run a DBT workflow.

We can run our current DBT Hello World project by running the command below inside the main directory of our project:

```
dbt run
```

and we should see:

```
19:44:11  Running with dbt=1.4.5
19:44:11  Found 2 models, 4 tests, 0 snapshots, 0 analyses, 296 macros, 0 operations, 0 seed files, 1 source, 0 exposures, 0 metrics
19:44:11  
19:44:11  Concurrency: 1 threads (target='dev')
19:44:11  
19:44:11  1 of 2 START sql table model main.patient_visits_summed_model .................. [RUN]
19:44:11  1 of 2 OK created sql table model main.patient_visits_summed_model ............. [OK in 0.09s]
19:44:11  2 of 2 START sql table model main.patient_visits_summed_over_5 ................. [RUN]
19:44:11  2 of 2 OK created sql table model main.patient_visits_summed_over_5 ............ [OK in 0.03s]
19:44:11  
19:44:11  Finished running 2 table models in 0 hours 0 minutes and 0.20 seconds (0.20s).
19:44:11  
19:44:11  Completed successfully
19:44:11  
19:44:11  Done. PASS=2 WARN=0 ERROR=0 SKIP=0 TOTAL=2
```

We can confirm that DBT read from 1 source and then created 2 models, as we expected. Now let's confirm that is what happened inside the DuckDB database locally.

### Check DuckDB Materialized Tables

If we open our previous DuckDB database up with the CLI command:


```
./duckdb dbt_patient_visits.duckdb
```

We can then check out the models materialed with the SQL:

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
│      · │    ·      │
│      · │    ·      │
│      · │    ·      │
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

Confirming that DBT did run correctly.

# Summary / On to Part 3

In this blog post we showed you build your first DBT workflow to process CSV data in DuckDB. In our 3rd and final article in this series, we'll discuss "What is DBT?" more in-depth to better understand its role in the cloud data warehouse world.

We also offer private workshops for companies on topics such as creating and running DBT pipelines (on multiple platforms such as Snowflake and Fivetran), please feel free to [reach out](../contact.html) if you'd like to discuss attending one of our workshops.
