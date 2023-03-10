---
layout: post
published-on: February 15th 2023
author: Josh Patterson
title: Designing Modern Enterprise Data Pipelines
subtitle: The Do's and Don'ts in Data Pipeline Design in 2023
description: In this post we'll .....
keywords: snowflake, snowpark, automl, AutoGluon, pandas, dataframe, whl, pip, anaconda, dependency
meta_og_image: pct_autogluon_dep_og_card.jpg
---

# Designing Modern Enterprise Data Pipelines

## Questions to Ask

todo

1. Who is the Primary User?
   * Individual
   * Team
2. What is the goal?
   * Analytics
   * Data Engineering pipeline
   * Exploratory Data Analysis



## Key aspects:

1. Information Architecture
   * avoid having to manually design this with file-system level semantics
   * you want ingest / merge / de-dupe "baked in"
   * you want to avoid manually managing concurrency issues
   * Moving Data is Bad, typically
2. Computations Patterns
   * SQL-first for analysts
   * Python first for data engineers and data scientists
   * you want to process data where it lives (in the cloud) typically in blob storage
3. Security
   * Active Directory ? Kerberos ?
4. Orchestration
   * [ todo ]
   * Is the pipeline a part of a larger system?