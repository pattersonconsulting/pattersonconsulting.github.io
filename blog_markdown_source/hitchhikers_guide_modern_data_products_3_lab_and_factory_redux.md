---
layout: post
published-on: March 27th 2023
author: Josh Patterson
title: Revisting The Lab and the Factory
subtitle: The Hitchhiker's Guide To Building Modern Data Products
description: In this post we'll .....
keywords: snowflake, snowpark, automl, AutoGluon, pandas, dataframe, whl, pip, anaconda, dependency
meta_og_image: pct_autogluon_dep_og_card.jpg
---

# Introduction

Purpose of this article:

* set up evolution of data pipelines article
* communicate what tools belong in the individual exploration 
* use metaphor of "searching parameter space" for a good solution --- "explore vs exploit" 

Series:

* [Prologue (Don't Panic)](hitchhikers_guide_modern_data_products_1_prologue.html)
* [The Evolution of Modern Data Platforms](hitchhikers_guide_modern_data_products_2_evolution_data_platforms.html)
* [Revisting The Lab and the Factory](hitchhikers_guide_modern_data_products_3_lab_and_factory_redux.html)
* [A Methodology for Building Data Products](hitchhikers_guide_modern_data_products_4_methodology_for_data_products.html)
* [Appendix A: Definitions](hitchhikers_guide_modern_data_products_5_appendix_A_definitions.html)
* [Appendix B: Roles](hitchhikers_guide_modern_data_products_6_appendix_B_roles.html)

the term "lab and factory" has caught on as an idea, but like many terms in the data space, its overused and its semantics have drifted over time. (see also: "data science" and "data engineering")

![Lab and the Factory vs Analytics and ML](./images/lab_factory_analytics_ml.png "Lab and the Factory vs Analytics and ML")

Original Article:

https://hbr.org/2013/04/two-departments-for-data-succe

Other people, like JWills, picked it up later:

https://qconsf.com/sf2013/presentation/lab-factory-building-production-machine-learning-infrastructure.html

Reference DBT's work in putting definitions on roles in data transformation

## Outline / 3 key ideas

1. Revisit original idea/source of the "Lab and the Factory" / Put framing around lab and factory, respectively
2. Definitions: Data Engineering, Analytics, Roles, Data Modeling, Feature Engineering --- this is key
3. Games of view materializations
4. Establish key principles of both lab and factory, setting up the next "evolution" article


### Problem Areas to Highlight

* JD Long: "Big IT tends to say 'we only do factories'" ---- "factory by default"
* call out Kubeflow's issue with early users --- hinders adoption
   * heavy need for MLOps -- because its a MLOps heavy system for the factory
   * https://becominghuman.ai/no-you-dont-need-mlops-5e1ce9fdaa4b
   * https://mlops.community/mlops-is-mostly-data-engineering/


* Benn making argument to just use dbt over duckdb (s3)
   * https://benn.substack.com/p/what-happened-to-the-data-warehouse#footnote-1-106233151
   * explain why this becomes problematic in this article

"Just"

https://cutlefish.substack.com/p/tbm-210-just?r=o29ix&utm_medium=ios&utm_campaign=post

### Quotes from HHGTTG

> It reminds Bundell of how world leaders handle major issues, such as climate change, where they gather and say "we should definitely do something about climate change. But in practice, the years go by ... and we don't."

> "The fact that life is just an adventure and the goal is to have fun. You're there to make the most of what's around you and be a good person while you do it," Oz says. "And I think that's grounding when your world is becoming an adventure."


### More JD thoughts

* JD
   * small firms are sorta "everything is a lab" so they struggle building the factory stuff
   * large firms say "we only do factories" --- hilarity ensues
   * "factory by default" / "lab by default" / "factory bias"
 
### JD on Analytics vs Lab and Factory

much analytical work can be build with simply a PowerBI or Tableau instance loaded with production data. Analysts can dig around and slice the data a number of ways and experiment with different ways of aggregating or looking at trends. So for those use cases a "lab" isn't really needed. Just a production environment accessible to analysts. 

when a lab becomes necessary is when analysts want to start building, testing or exploring ideas that either don't fit on typical production analytics platforms because of size, volume, or demands on the system. One example would be quant analysts in a financial services firm wanting to build large Monte Carlo simulations that produce voluminous output. A normal production environment might not have the compute nor the storage to handle large simulations. And if those analysts want to engage in optimizations of large portfolios, they may need resources that far exceed a typical analytical workbench. These analytical loads are far beyond typical BI workloads that are focused on filter, slice, and pivot operations.

### ChatGPT Thoughts

> *In the context of data pipelines, the terms "lab" and "factory" can refer to different stages or environments in the process of developing, testing, and deploying data pipelines.*

> *A lab is typically a testing environment where data scientists and engineers experiment with different data processing techniques, algorithms, and models. In a lab, they might use small-scale datasets to test their ideas and refine their code. Labs are typically more flexible and allow for rapid iteration, as data scientists can quickly experiment with new ideas without worrying about the constraints of the production environment.*

> *On the other hand, a factory refers to the production environment where data pipelines are executed at scale to process large volumes of data in a reliable and efficient manner. Factories are typically more rigid and require more careful planning and optimization, as the stakes are higher and errors can have significant consequences. In a factory, data pipelines must be carefully tested and validated before being deployed to ensure that they can handle large volumes of data, run reliably and efficiently, and produce accurate results.*

> *Overall, the main difference between a lab and a factory in data pipelines is that a lab is a more experimental and flexible environment for developing and testing new ideas, while a factory is a more rigorous and production-ready environment for executing data pipelines at scale.*

### JD Long thoughts

Thoughts on individual vs enterprise:

> *Individual workflow needs to be very very low friction for easy and fast exploration. There will be lots of dead ends so every step should be trivially easy to iterate. But.. when done with the individual EDA, there may be things that are useful for daily metrics or whatever. So those may be lifted and landed into a scheduled robust pipeline.*

> *So there should be low friction between exploratory & prod… strong argument for same language, common environments etc*

> *Stupid shit adds huge friction. Stuff like credentials and environments being different between. Exploration & prod. I’ve spent soooo many calories getting that friction out of our systems.*

> *IT devs will look at “exploratory” workflows and say “oh, that’s dev” and try to set up data scientists to work in dev with incomplete and stale data. Wrong. The explore environment must have production data.*

> *That’s an example of friction we’ve had to remove.*

> *Prod flows also have more logging and error checking, naturally*


and

> *I feel like the "modern data pipeline" sort of assumes the builder of the pipeline knows exactly what they want to create and report. that sort of assumes that EDA and design and all that has already happened*

> *so the modern data pipeline either needs to prepare data to be explored prior to EDA/ metric POC or the pipeline is informed by the work done in EDA to create metrics that the business knows they want*

> *a common failure mode, in my experience, is to have pipelines that do a bunch of shit that's not really the right thing, or not informed by what's really useful downstream*

> *usually because an engineer hasn't spend enough time with the end consumer to really understand what's useful*

# Revisting the Lab and the Factory

Original Artcile:

https://hbr.org/2013/04/two-departments-for-data-succe

# The 3 Key Roles to Consider

link the DBT article for the roles

## Data Engineer

ML

## Analytics Engineer

analytics

## Data Analyst

SQL bro

# Criteria for When to Use a Lab Environment When Build Data Products

"Good data engineers are lazy"

https://stkbailey.substack.com/p/good-data-engineers-are-lazy?utm_source=substack&utm_medium=email

* need to be quick and nimble
* want to be able to try out new ideas and new tools quickly without a lot of effort --- thoughts are fleeting, sometimes

Mention: some systems, such as Kubeflow, are execptional for Enterprise operations, but have a steep learning curve

* explain why this is bad, and why product makers should allow for early users to experiment quickly

ChatGPT says:

*Kubeflow is a powerful open-source platform for deploying and managing machine learning workflows on Kubernetes. While Kubeflow has many benefits for ML practitioners, it also has a steep learning curve due to several reasons:*

*Complexity of Kubernetes: Kubeflow is built on top of Kubernetes, which is a complex container orchestration platform. This means that users need to have a solid understanding of Kubernetes before they can start using Kubeflow.*

*Multitude of components: Kubeflow is composed of several components such as JupyterHub, Tensorflow, and Istio. Understanding how each component works and how to use them effectively can take time.*

*Command line interface: Kubeflow relies heavily on the command-line interface (CLI) for managing workflows and deployments. This can be intimidating for users who are not comfortable with the CLI.*

*DevOps skills: Kubeflow requires users to have some DevOps skills such as Docker and Kubernetes knowledge, Git for version control, and Python for scripting.*

*Steep learning curve for machine learning: Finally, machine learning itself has a steep learning curve, and Kubeflow adds an additional layer of complexity to this.*

*Overall, while Kubeflow has many benefits, it can be challenging for new users to get started due to its reliance on Kubernetes and its multitude of components. However, with the right resources and support, it is possible to overcome these challenges and leverage the power of Kubeflow for ML workflows.*

## Typcial Lab Scenario

relate eexperience of developing medical models with the University of Michigan and running lots of small tests on raw data files

* I have some files locally
* single user of dataset
* I want to do basic analysis
* dont want to install much / anything
* quick local python env
   * python3
   * Numpy
   * Pandas
   * Sci-Kit Learn

likely managed by anaconda

Examples of tools

* jupyter notebooks (local or on GCP / AWS / cloud)


## Challenges Over Time with Lab Pipelines

* having that notebook (version 15?) that has a ton of cells in it running a series of transform steps eventually becomes unweildy
* once our data product goes beyond experiment and towards "business production value IP" we want to protect IP
   * consistency
   * git tracked
* we'll also want to let more people work on the pipeline, whihc is harder to do w a single notebook
* this is the point where we want to move to a CI/CD-based system
   * DBT
   * Airflow
   * Fivetran
* some tools are DAG-based, some tools are notebook-based --- but they all tend to be github / CI/CD-style systems

ChatGPT Says:
*CI/CD stands for Continuous Integration and Continuous Deployment/Delivery, and it is a set of practices used in software development to ensure that code changes are tested, validated, and deployed frequently and reliably. In the context of data pipelines, CI/CD can be used to ensure that changes to data processing code and data models are tested and deployed automatically and seamlessly.
Continuous Integration refers to the practice of integrating code changes into a shared repository and testing them automatically, preferably in a repeatable and automated way. This helps to identify integration issues and conflicts early, which reduces the risk of introducing bugs into the codebase.
Continuous Deployment/Delivery refers to the practice of deploying validated code changes into production environments frequently and automatically. In the context of data pipelines, this means that changes to data processing code and data models can be deployed quickly and reliably, ensuring that data is processed and analyzed as soon as possible.
To implement CI/CD for data pipelines, organizations can use tools such as Git for version control, Jenkins or CircleCI for automated testing, and Kubernetes or Docker for containerization and deployment. Additionally, data pipeline frameworks such as Apache Airflow or Apache Beam can be used to create data pipelines that are easy to test and deploy.
Overall, CI/CD for data pipelines helps organizations to ensure that data processing code and models are tested, validated, and deployed quickly and reliably, reducing the time to insights and enabling faster decision-making.*

# The Data Lakehouse Architecture

* what they got right wrt bridging the gap between ML and analytics
* the overhead for standing up infrastructure is more in the "factory" camp
* early lab work doesnt always port well (starts w simple python)

# Criteria for When to Use a Factory Environment When Build Data Products

## An Overview of Data Infrastructure in the Factory

* illustrating the connective area between the data warehouse and machine learning pipelines
   * DBT vs Kubeflow Pipelines


## Goals of the Factory

* routinely produced processed data from many sources for downstream daily systems

## Constraints

* security -- can't just touch any data however we want
* orchestration -- dont want this running on Larry's laptop
* multiple users of the data

## The Typical Factory Scenario

* may have some files in s3 / cloud storage
* my team all actively share this data (multi-tenancy)
* system needs to run despite any single user being active / online
* data needs to continuously run / pump through pipeline of transforms






## Relationship with the "Modern Data Stack"

* the concept of the "Lab" shouldn't involve standing up all that stuff --- this should only be a "factory" situation

