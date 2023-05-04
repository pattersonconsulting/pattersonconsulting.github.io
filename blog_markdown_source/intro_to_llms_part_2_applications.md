---
layout: post
published-on: March 27th 2023
author: Josh Patterson
title: An Introduction to Large Language Models (LLMs)
subtitle: Core Concepts and Terminology
description: In this post we'll .....
keywords: snowflake, snowpark, automl, AutoGluon, pandas, dataframe, whl, pip, anaconda, dependency
meta_og_image: pct_autogluon_dep_og_card.jpg
---

# Introduction

Purpose of this series:

> To understand what LLMs are

The intended audience for this series is:

> Individual researchers, data scientists, and then also enterprise data teams as well

Series:

* [Core Concepts and Terminology in LLMs](intro_to_llms_part_1_terminology.html)
* [LLMs and Enterprise Applications](intro_to_llms_part_2_applications.html)
* [Model Training and Management in LLMs](intro_to_llms_part_3_model_management.html)

# Early Target Use Cases for LLMs

Overall, labor-intensive tasks in an insurance company tend to be those that 

require significant amounts of manual effort, analysis, and communication. 

As such, many companies are investing in automation and other technologies to streamline these processes and reduce the workload on human staff.

The insurance industry is a great example of an industry that has many labor intensive tasks.

Here are a few examples:

* Claims processing
* Underwriting
* Customer service
* Compliance


## Example: Claims Processing

* todo: link QA demo notebook

This involves 
verifying the accuracy of submitted claims, 
reviewing policy coverage and terms, (QA)
and determining the appropriate payout amount.  (QA)
Claims processing often requires 
a significant amount of manual data entry, (Data Entry)
analysis, 
and communication with (Document Generation)
policyholders, 
medical professionals, 
and other stakeholders.


QA
Question answer
Data Entry
“enter the data from this person’s file into this template”
Document Generation
Similar to office 365 demo video
examples
“write a letter to the policyholder about their claim that approves/denies the claim”
“create a CSV file with the medical history of the patient to send to the medical professional”


# Implementing LLMs in Applications


## Options for Building LLM Applications

LangChain
Open Source Python Library
Can Use multiple Models (OpenAI, or Local)
Google Generative AI Studio
closed source
Built into GCP
Prompt Engineering Workbench
Tons of emerging libraries, really…


## Model Variations in LLMs

Models

1. Use a Pre-Trained LLM
2. In-Context Learning with Pre-Trained LLM - Fine-Tune an Existing LLM
3. Use Ray/DGX to Finetune models

## Building a Question / Answer System with LangChain

* discuss, link notebook


Required Tooling
LangChain
VectorStore
Custom Corpus
Something to ask questions about
LLM
OpenAI
Other local model

https://colab.research.google.com/drive/1Rl3eh_rrN7sco4bkzApVqOzu1CtjoWPb


### What is LangChain?

what what?

Use Cases
Personal Assistants (Agents)
Autonomous Agents
Agent Simulations
Question Answering over Docs
Chatbots
Querying Tabular Data
Code Understanding
Interacting with APIs
Summarization
Extraction
Evaluation

Models supported:

AI21
Aleph Alpha
Azure OpenAI
Banana
CerebriumAI
Cohere
DeepInfra
ForefrontAI
GooseAI
GPT4All
Hugging Face Hub
Hugging Face Local Pipelines
Llama-cpp
Manifest
Modal
NLP Cloud
OpenAI
Petals
PredictionGuard
PromptLayer OpenAI
Replicate
Runhouse
SageMakerEndpoint
StochasticAI
Writer



## Natural Language Dataset Query with LLMs


Natural Language Dataset Query with LLMs

Querying Tabular Stores with NL:
https://python.langchain.com/en/latest/use_cases/tabular.html
Using Chains to Query APIs
https://python.langchain.com/en/latest/use_cases/apis.html
Using NL to Query SQL Databases
https://python.langchain.com/en/latest/modules/chains/examples/sqlite.html
https://github.com/hodgesmr/LangChain-Data-Demo

### Task Composability

Consider the “talk-to-your-data” use case where we want to connect to a database and query this database in natural language. Imagine a credit card transaction table. You want to ask things like: 
"How many unique merchants are there in Phoenix and what are their names?" 
and your database will return: 
"There are 9 unique merchants in Phoenix and they are …".

One way to do this is to write a program that performs the following sequence of tasks:
Task 1: convert natural language input from user to SQL query [LLM]
Task 2: execute SQL query in the SQL database [SQL executor]
Task 3: convert the SQL result into a natural language response to show user [LLM]

### Querying Pandas Dataframes with Natural Language Example: Sketch

Sketch is an AI code-writing assistant for pandas users that understands the context of your data, greatly improving the relevance of suggestions. Sketch is usable in seconds and doesn't require adding a plugin to your IDE.

Data Catalogging:
General tagging (eg. PII identification)
Metadata generation (names and descriptions)
Data Engineering:
Data cleaning and masking (compliance)
Derived feature creation and extraction
Data Analysis:
Data questions
Data visualization

## LLMs, Agents, and Tools

Re-write:
```
Why do LLMs need to use Tools?
One of the most common challenges with LLMs is overcoming the lack of recency and specificity in their training data - answers can be out of date, and they are prone to hallucinations given the huge variety in their knowledge base. Tools are a great method of allowing an LLM to answer within a controlled context that draws on your existing knowledge bases and internal APIs - instead of trying to prompt engineer the LLM all the way to your intended answer, you allow it access to tools that it calls on dynamically for info, parses, and serves to customer.
Providing LLMs access to tools can enable them to answer questions with context directly from search engines, APIs or your own databases. Instead of answering directly, an LLM with access to tools can perform intermediate steps to gather relevant information. 
```

GPT-Plugins ---- link page
