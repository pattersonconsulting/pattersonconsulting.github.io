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
* [Revisting The Lab and the Factory](hitchhikers_guide_modern_data_products_2_lab_and_factory_redux.html)
* [The Evolution of Modern Data Pipelines](hitchhikers_guide_modern_data_products_3_evolution_data_pipelines.html)
* [A Methodology for Building Data Products](hitchhikers_guide_modern_data_products_4_methodology_for_data_products.html)

Story: Snowflake summit --- all the logos are the same, just replace Cloudera with Snowflake

Topics to reference

* unbundling of Airflow
   * rise of airflow, what it replaced, compared to Hadoop-infra
* rise of DBT
   * its hard to describe, a developer tool, and middleware --- but its super hot. and its hard to understand why.

# The Evolution of Data Infrastructure

Narrative and Ideas

* Refer to the trend starting around 2008 to have "everything scale" -- hadoop, big data
* in terms of graphs/charts --- need to talk about late 2000's where "big data" started to emerge with data growth
* this data growth drives more BI tools, such as Tableau
* setting the stage for a tool such as DBT to emerge, 7-8 years later (2016)

## Early OLAP Databases

* Postgres, Oracle, MySQL, etc

## The Big Data Era, Hadoop, and Cloudera

* On-Prem and the JVM
* Parallel Databases (Vertica, Greenplum)
* Spark and Databricks

Story: Watching Matei demo Spark as a Hadoop execution engine at a Hadoop User Group in 2010/2011

## The Cloud Came Along, Slowly, and Then All at Once

The irony of Cloudera's name...

* Cloud Rise: IT blocking "the lab", 
   * so they just run to the cloud with a credit card
   * Story: when my hadoop hardware sat on the loading dock for weeks cause folks wouldnt unload it


# Key Trends of the Past 15 Years


## Python and It's Ecosystem

* growth, chart

## Deep Learning and GPUs

* growth, chart
* co-evolution with Python ecosystem
* charts of models' jump in performance
   * vision models
   * voice reconition
   * large language models (jump in late 2021) --- and mention Watson having a similar moment a decade earlier

## Emergence of the Cloud

* growth, chart



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

https://www.freecodecamp.org/news/the-rise-of-the-data-engineer-91be18f1e603

https://medium.com/validio/the-rise-and-future-of-data-engineering-whats-it-all-about-a235dbb4412e

https://maximebeauchemin.medium.com/the-downfall-of-the-data-engineer-5bfb701e5d6b

