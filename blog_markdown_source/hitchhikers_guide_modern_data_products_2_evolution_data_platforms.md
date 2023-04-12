---
layout: post
published-on: March 27th 2023
author: Josh Patterson
title: The Evolution of Modern Data Pipelines
subtitle: The Hitchhiker's Guide To Building Modern Data Products
description: In this post we'll .....
keywords: snowflake, snowpark, automl, AutoGluon, pandas, dataframe, whl, pip, anaconda, dependency
meta_og_image: pct_autogluon_dep_og_card.jpg
---

# Introduction

Purpose of article

* set context for how things have changed (timeline: 2009-2023?)

Series:

* [Prologue (Don't Panic)](hitchhikers_guide_modern_data_products_1_prologue.html)
* [The Evolution of Modern Data Platforms](hitchhikers_guide_modern_data_products_2_evolution_data_platforms.html)
* [Revisting The Lab and the Factory](hitchhikers_guide_modern_data_products_3_lab_and_factory_redux.html)
* [A Methodology for Building Data Products](hitchhikers_guide_modern_data_products_4_methodology_for_data_products.html)
* [Appendix A: Definitions](hitchhikers_guide_modern_data_products_5_appendix_A_definitions.html)
* [Appendix B: Roles](hitchhikers_guide_modern_data_products_6_appendix_B_roles.html)

Story: Snowflake summit --- all the logos are the same, just replace Cloudera with Snowflake

Topics to reference

* unbundling of Airflow
   * rise of airflow, what it replaced, compared to Hadoop-infra
* rise of DBT
   * its hard to describe, a developer tool, and middleware --- but its super hot. and its hard to understand why.

* explosion of information
   * TVA project, PMU data --- half petabyte hadoop cluster
   * we had to try non-MS-and-Oracle vendors because they didnt have the features we needed

* as a platform gets bigger, moving data gets progressively harder, and compute jobs get pulled into its orbit
   * data has gravity

* moving fast and having flexibility is a key driver of going to the cloud even when cost is higher
   * 

# The Evolution of Data Infrastructure

Narrative and Ideas

* Refer to the trend starting around 2008 to have "everything scale" -- hadoop, big data
* story about Stonebraker telling Olson that "MapReduce wont work out"
* in terms of graphs/charts --- need to talk about late 2000's where "big data" started to emerge with data growth
* this data growth drives more BI tools, such as Tableau
* setting the stage for a tool such as DBT to emerge, 7-8 years later (2016)

mention how you cannot "solve" a particular aspect of data infrastructure, as it all continues to evolve

Why this version of the evolution of data platforms? why not just rely on the existing writing of "Modern data stack"?

--- because it misses the tectonic plates shifting

## Early OLAP Databases

* Postgres, Oracle, MySQL, etc

## The Big Data Era, Hadoop, and Cloudera

* On-Prem and the JVM
* Parallel Databases (Vertica, Greenplum)
* Spark and Databricks

Story: Watching Matei demo Spark as a Hadoop execution engine at a Hadoop User Group in 2010/2011


### Data Platform Consolidation

When enterprises are exploring data platform consolidation, how are they evaluating between cloud providers’ native offerings and cloud-agnostic solutions or on-prem solutions?

Used to be theories that customers wanted open source
But they just wanted something that let them get rolling without a long sales pitch
Easy wins
Cloudera didnt make Hadoop easy enough
Databricks came along, got cloud right
Snowflake came along, made SQL even easier, focused on that
 Now databricks playing catch up


## The Cloud Came Along, Slowly, and Then All at Once

The irony of Cloudera's name...

* Cloud Rise: IT blocking "the lab", 
   * so they just run to the cloud with a credit card
   * Story: when my hadoop hardware sat on the loading dock for weeks cause folks wouldnt unload it


## The Data Lakehouse Architecture

* what they got right

# Key Trends of the Past 15 Years


## Python and It's Ecosystem

story: i was a jvm guy from hadoop, and it had been good to me. this python thing was "just noise", like Haskel or some other bs

problem was, it was on a slow climb to beat out the other languages across the decade

* growth, chart

## Deep Learning and GPUs

story: i was a hadoop guy, a yarn guy --- parallelization was the way forward. until GPUs came along --- and it wasn't

* growth, chart
* co-evolution with Python ecosystem
* charts of models' jump in performance
   * vision models
   * voice reconition
   * large language models (jump in late 2021) --- and mention Watson having a similar moment a decade earlier

## Emergence of the Cloud

* growth, chart
* the factory is hard to manage on-premise and IT is territorial
   * eventually the data kids found a corporate credit card and cranked up cloud accounts as shadow IT


# The Tectonic Plates of Data Infrastructure

* explain the tectonic plate shifts
   * story of being at snowflake summit and thinking "this is strata --- but its not"


## Re-emergence of SQL
   * and why that spells trouble for non-SQL folks


## Cloud Consumes the On-Premise Market
   * need graph
* old stories
   * hadoop, MapReduce, and ?
   * banks only wanted Hive --- SQL --- should have known something was up

* Cloud Rise: IT blocking "the lab", 
   * so they just run to the cloud with a credit card
   * Story: when my hadoop hardware sat on the loading dock for weeks cause folks wouldnt unload it

## Emergence of Python
   * anaconda slide

## The rise of Deep Learning
   * rise of pandas
   * JVM on the decline / Deeplearning4j as jvm system
* use material from keybank slides

### Python and Pandas and Machine Learning

https://ponder.io/pandas-is-now-as-popular-as-python-was-in-2016/?utm_campaign=meetedgar&utm_medium=social&utm_source=meetedgar.com



# The Good Ideas in the Data Lake House Concept

* notes here about how they create a better multi-tenant factory design
   * one critical change is "moving from just a bunch of files" to "a logical data abstraction over the raw data"
* an understanding of the different data access patterns for analytics processing vs machine learning compute/training


# What Snowflake Got Really, Really, Right

* free data ingest -- barely think about it
* multi-tenancy
* ANSI-SQL compliance --- just throw in your old code, and it will scale as much as you need -- you dont have to chance a thing
* There are tons of SQL analysts, and a lot less programmers in the world
* caught the cloud wave at the right time
* Hadoop ops was really hard

Security? Handled.
Maintenance? Near to zero.
Managing different environments (dev/qa/prod)? Piece of cake.
Optimization and scaling? Handled.

## Snowflake vs DataBricks

https://benn.substack.com/p/the-end-of-big-data/comments

> The thing that Snowflake did really well is they pitched a product that anyone could buy. You're an enterprise with tons of wild data needs? Snowflake can help. You're a mid sized business running SQL Server? Snowflake can help. You've got an MySQL database and are looking for your first analytical warehouse? Snowflake can help.


## Platform Feature Convergence

Snowflake

* Snowflake introduced a python dataframe 
* effectively the same as PySpark dataframe API for spark
* On purpose: to onboard spark users more easily


Databricks

* Delta is basically OSS Snowflake, and since then, Databricks and Snowflake have been slowly converging. 
* Finally in the last year or so Delta feels a lot like Snowflake (with a nice UI, simplified SQL clusters like Snowflake warehouses, etc.). So it really is a big, fast database that you can program with python, scala, SQL.

DB came along to be a "better hadoop"; it was Scala-first and required programmers to think about parallelization

# Emergence of DBT

* on paper, this tool took me a long time to make sense of
   * its complicated to explain
   * its middleware (confirm)
   * it seemingly is a feature of other projects --- how is it its own product?
   * it feels sorta like Oozie on Hadoop in terms of being a DAG orchestrator


* what really dug at me was --- how did DBT come to exist? what conditions allowed this to happen? (SQL coming back en vogue, w scale for free)
* The evolution of data platforms created market conditions that were just right for a product like DBT

DBT is hot
“standardizing their SQL transformation layers on dbt as they moved their data warehousing to the cloud.”
dbt is the framework for modern cloud data warehouse development. It lets you build out a new kind of data pipeline that was never practical before. All while embracing today's best data practices: encapsulate business logic, check it into git, test your data, connect it in a DAG
But dbt exists today for a reason. Cloud data warehouses demanded a new way of working. dbt met that need by doing all-in on SQL. The result is pretty cool.

# The Modern Data Stack

provide a simple-ish definition

https://continual.ai/post/the-future-of-the-modern-data-stack

## Definition 

The Modern Data Stack commonly refers to a collection of technologies that comprise a cloud-native data platform, generally leveraged to reduce the complexity in running a traditional data platform. The individual components are not fixed, but they typically include: 
A Cloud Data Warehouse, such as Snowflake, Redshift, BigQuery, or Databricks Delta Lake
A Data Integration Service, such as Fivetran, Segment, or Airbyte
A ELT data transformation tool, almost certainly dbt
A BI layer, such as Looker or Mode 
A Reverse ETL tool, such as Census or Hightouch 

## Key Capabilities

https://continual.ai/post/the-future-of-the-modern-data-stack

Offered as a Managed Service:  
> Requires no or minimal setup and configuration from users and absolutely no engineering required. Users can get started today, and it’s not a vapid marketing promise. 

Centered around a Cloud Data Warehouse (CDW): 
> Everything “just works” off-the-shelf if companies use a popular CDW. By being opinionated about where your data is, you eliminate messy integrations and tools play well together.  

Democratizes data via a SQL-Centric Ecosystem: 
> Tools are built for data/analytics engineers and business users. These users often know the most about a company’s data, so it makes sense to try to upskill them by giving them tools that speak their language.  

Elastic Workloads: 
> Pay for what you use. Scale up instantly to handle large workloads. Money is the only scale limitation in the modern cloud. 
> Focus on Operational Workflows: 
> Point-and-click tools are nice for low-tech users, but it’s all kind of meaningless if there’s not a viable path to production. Modern data stack tools are often built with automation as a core competency. 

## Drivers of the Modern Data Stack

JWills: https://twitter.com/josh_wills/status/1522622572743073800

> In my Cloudera days, I thought that people cared about open-source principles. They do not. They cared that an open-source tool meant that they could get stuff done w/o having to sit through a sales presentation.
> This principle applies well beyond OSS- when we were choosing an initial BI tool for Slack, Mode beat Tableau because Tableau made us sit through a sales preso while Mode was just like "okay, here's the tool. Call us in 30 days if you want to keep it."
> Second principle: all technical decisions are easy until someone's fingers touch a keyboard, and then the Sunk Cost Principle comes into full effect.
By the time we had Tableau up and running, we had already built like 30+ dashboards in Mode. It was over.

## Properties of Modern Data Platforms

Tell story of ITS 

http://www.pattersonconsultingtn.com/use_case_repository/municipal_vertical.html

## What is Working in Open Source Commercialization

* open source as marketing driver for closed source cloud applications
* focus on "time to value" (less worried about cloud cost), want less Ops overhead to get started/
* need a faster close rate, something "under 18 months"

### Other Topics 

Data Platform Consolidation:

  *   To what extent are enterprises interested in consolidating around a single data platform vs. last year?
     *   How are enterprises evaluating between cloud providers' native offerings and cloud-agnostic or on-prem solutions as they explore data platform consolidation?
  *   How is the current macro environment impacting enterprises’ decisions around data platforms, including migrations?
  *   How is interest in generative AI impacting data platform decisions, including interest in platform consolidation?
     *   How is Databricks positioned relative to other cloud data platforms, including hyperscalers, to benefit from growth in generative AI workloads?

Snowflake and/or Databricks:

  *   How is the competitive landscape between Databricks and Snowflake evolving?
  *   To what extent are customers choosing just Snowflake or Databricks vs. using both?
     *   How has this changed over the past year?
  *   How compelling are the competitive products released by Databricks and Snowflake that target the others’ core capabilities?
     *   For what types of workloads do they compete? How well do they compete?
  *   How have customer conversations around consolidating workloads on Snowflake or Databricks changed over the past year?
  *   How mission-critical are the workloads moving to Databricks and Snowflake?
  *   To what extent, and for what reasons, are workload migrations from Teradata slowing?
     *   Is the current macro environment impacting this dynamic?

# A Few Predictions Going Forward

## How Predictions Go Very, Very, Wrong

you cant see the full distribution of the market

often we make inaccurate forecasts based on samples of data that do not represent the full distribution of the market

## The Red Queen Always Has it Right

Banks in the 60s and computers, the 4-day week

We just do more

We are programmed to compete, to see over that horizon, and explore new lands

## The Continued Dominance of SQL

Spark in decline, just as MapReduce before it

* analysts are sql-first
* don't ask folks to change what works
* everyone has a DW -- not everyone is doing "advanced analytics"

## The Continued Growth of Snowflake

$SNOW vs $DBX
No enterprise won’t have a cloud data warehouse
Some enterprises will not have an advanced analytic platform
If you have a DW
You have the data
And you dont have to do ETL



# References


https://www.freecodecamp.org/news/the-rise-of-the-data-engineer-91be18f1e603

https://medium.com/validio/the-rise-and-future-of-data-engineering-whats-it-all-about-a235dbb4412e

https://maximebeauchemin.medium.com/the-downfall-of-the-data-engineer-5bfb701e5d6b

