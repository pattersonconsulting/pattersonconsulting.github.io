---
layout: post
published-on: February 15th 2023
author: Josh Patterson
title: Open Sourcing the geoEDA Toolkit
subtitle: Geospatial Hurricane Analytics
description: In this post we'll .....
keywords: snowflake, snowpark, automl, AutoGluon, pandas, dataframe, whl, pip, anaconda, dependency
meta_og_image: pct_autogluon_dep_og_card.jpg
---

# Open Sourcing the geoEDA Toolkit

yadda


sue anne bell

AMS invited talk

Started out with a few counties of data
Couldnt find relationships
Then moved to a lot more counties worth of data
Found some of the spikes we were looking for
But realized there was a larger story
Then moved to looking at a 5-7 states worth of data
For admissions
Added per-county storm data in
Found compelling results in the analysis

Talked these results over with another data expert
They pointed out: Storm (N=1)
Difficult to draw any generalizations when N = 1
Now we know we needed to look at 20 years worth of storm data
And as much admission data as we could get our hands on
Our geospatial system needed to be more robust


[ Presented the storyline to AMS in 2022 ]

## What Tool Are We Releasing?

* An open source set of dbt templates to transform raw census and hurricane data
* A map-generation system based on streamlit and folium to do Geospatial EDA
* A set of jupyter notebooks to perform tabular EDA on the unified dataset


## How Are We Using The Tool?

* This tool has helped us analyze 20 years of Hurricane data
* The insights gleamed from the tool impacted our EDA methods in the Jupyter notebooks
* This has directly impacted our results in building models to predict hospital admissions post-hurricane


## What Else Might it Be Used for?

* Understanding geospatial relationships between weather events and other events in
   * Transit
   * Housing
   * Water
   * Power
   * Air Quality
   * Foot Traffic
* Spatially exploring complex dataset
* Informing the tabular EDA workflow

We include an example where we analyze hurricanes' impact on FEMA inspected damage across 20 years.


## Evolution of the Project

Evolution of project

“The Principal Investigator, the data scientist, and the data engineer”
Need to be able to share a hurricane dashboard with folks outside of data science
Non-computer scientists researchers (e.g., Sue Anne)
https://locallyoptimistic.com/post/building-more-effective-data-teams-using-the-jtbd-framework/?utm_source=substack&utm_medium=email
Need to provide the same same of analytical data to
Researchers
Data engineers
Data scientists
Emailing jupyter notebooks is brittle and prone to error
E.g., “not the latest spike calculation code”, etc

Researchers
Want to better understand geo-spatial data with a custom visual tool
Analyst
Want to be able to build out analytics in a fashion consistent with
> “In the spirit of bringing software engineering practices to the SQL-centric ELT data warehousing world, any modern approach would be incomplete without automating the testing and deployment process and integrating with a CI/CD process.”
Data Engineers
Want to provide features to the data scientist that are consistent with what is presented in the BI tool
Data Scientists
Want to build models and not fuss about where the data came from

Talk about the themes from the AMS talk — cross-discipline collaboration
Open sourcing research results — for others to collaborate with!

Maps @ UM Research
Not traditional EDA
But we still need some custom visualization
Possibly could have used ERSI for the geospatial or another traditional GIS tool
But those tend to be locked down
And we started from a data-centric perspective, operating with python, and then later on bringing in GIS components
The open source world has added a lot of functionality that was traditionally in tools such as ERSI

## We started with a need to do traditional EDA

But then realized we needed geospatial visualization combined with our python analysis
To leverage cross-discipline research
Disasters
Computer science
We also needed a way to let multiple people work on the system
Data Analysts – SQL
This started out as a jupyter notebook
And then became a series of notebooks
Soon the data processing pipeline was long and un-weldy
And calculated the metrics for admission data and storm data slightly differently over time
Making comparison of results more difficult too


> JD: JD says he experiments with concepts in a notebook, and then once it gets to a certain point, he hands it off to an analyst


## Leverage Open Source As Building Blocks

https://github.com/geanders/hurricaneexposure

CSV Data extracted from GEAnders Hurricane Exposure



## What is the geoEDA Toolkit?

yadda 

## What does the geoEDA Toolkit do?

yadda 

## Ongoing Research and Invited Talks

yadda 

## Overview of the geoEDA Toolkit Github Repository

yadda 

### Building an Interactive Custom geoEDA Map

yadda 

### Adding Custom Layers

yadda 

## Summary

yadda 
