---
layout: post
published-on: February 15th 2023
author: Josh Patterson
title: Exploratory Data Pipelines vs Enterprise Data Pipelines
subtitle: The Lab and the Factory in 2023
description: In this post we'll .....
keywords: snowflake, snowpark, automl, AutoGluon, pandas, dataframe, whl, pip, anaconda, dependency
meta_og_image: pct_autogluon_dep_og_card.jpg
---

# Exploratory (Lab) Data Pipelines vs Enterprise (Factory) Data Pipelines

## ChatGPT Thoughts

> *In the context of data pipelines, the terms "lab" and "factory" can refer to different stages or environments in the process of developing, testing, and deploying data pipelines.*

> *A lab is typically a testing environment where data scientists and engineers experiment with different data processing techniques, algorithms, and models. In a lab, they might use small-scale datasets to test their ideas and refine their code. Labs are typically more flexible and allow for rapid iteration, as data scientists can quickly experiment with new ideas without worrying about the constraints of the production environment.*

> *On the other hand, a factory refers to the production environment where data pipelines are executed at scale to process large volumes of data in a reliable and efficient manner. Factories are typically more rigid and require more careful planning and optimization, as the stakes are higher and errors can have significant consequences. In a factory, data pipelines must be carefully tested and validated before being deployed to ensure that they can handle large volumes of data, run reliably and efficiently, and produce accurate results.*

> *Overall, the main difference between a lab and a factory in data pipelines is that a lab is a more experimental and flexible environment for developing and testing new ideas, while a factory is a more rigorous and production-ready environment for executing data pipelines at scale.*

## JD Long thoughts

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


## Lab and the Factory

intro...

### Data Pipelines in the Lab

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

Scenario

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


Challenges Over Time with Lab Pipelines

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

### Data Pipelines in the Factory

Goals

* routinely produced processed data from many sources for downstream daily systems

Constraints

* security -- can't just touch any data however we want
* orchestration -- dont want this running on Larry's laptop
* multiple users of the data

Scenario

* may have some files in s3 / cloud storage
* my team all actively share this data (multi-tenancy)
* system needs to run despite any single user being active / online
* data needs to continuously run / pump through pipeline of transforms


