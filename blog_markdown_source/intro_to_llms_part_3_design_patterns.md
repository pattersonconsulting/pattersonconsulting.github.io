---
layout: post
published-on: March 27th 2023
author: Josh Patterson
title: Building Enterprise Applications with Large Language Models
subtitle: Part 3 - Design Patterns for Building Large Language Model Applications
description: In this post we'll .....
keywords: snowflake, snowpark, automl, AutoGluon, pandas, dataframe, whl, pip, anaconda, dependency
meta_og_image: pct_autogluon_dep_og_card.jpg
---

# Introduction

Purpose of this series:

> To understand the role of large language models in enteprise applications and some of the components, tools, and technologies relevant to building these applications.

This article, part 2 of the series, is focused on design patterns for enterprise large language model applications. We build on ideas from part 1 around large language models' reasoning capabilities and how we can best use them in enterprise use cases.

The intended audience for this series is:

> Individual practitioners, enterprise data teams, and enterprise executives

Series:

* [An Introduction to Large Language Models (LLMs)](intro_to_llms_part_1_terminology.html)
* [Understanding Use Cases for Large Language Models](intro_to_llms_part_2_use_cases.html)
* [Design Patterns for Large Language Model Applications](intro_to_llms_part_3_design_patterns.html)
* [Putting LLM Applications into Production](intro_to_llms_part_4_model_management.html)
* [Appendix A: What is Artificial Intelligence?](dl_book_appendix_a_ai.html)

The final post is where I give context on the arena of artificial intelligence based on the history of the field. This context and history gives the reader a better viewpoint on recent developments in large language models.


# Design Patterns for Building Large Language Model Applications

This section is based on early prototyping notes our team has collected designing LLM application prototypes for customers and partners.

To design a new LLM application, we follow the design steps listed below:

1. set a measurable goal for the system
   * example: "display a hurricane on a map based on a text command"
   * example: "answer a question about a type of insurance policy"
2. Choose a model to prototype around
   * most of the time you should use an existing model to prototype with
   * if you are exploring ideas, just use OpenAI
   * only in rare cases will you need to train a custom model
3. Take goal and break it into sub-tasks
   * the sub-tasks should be tasks that can be answered by a small program
   * not all sub-tasks will need to query a LLM model
4. Blocks of sub-tasks create logical workflows
   * some workflows are building blocks in your application (e.g., the LangChain SQL Agent)
5. Wire into prototype system for testing
   * sometimes command-line interfaces are ok
   * other times, a quick UI in a framework such as Streamlit is helpful

Let's take some of these ideas and visualize how they work in practice.

## Building Logical Sub-Tasks from Goals

Most goals are more complex than a single task so we need to break the goal down into a few sub-tasks that are "bite-sized" enough for a large language model to process in a single call. Sometimes there are pre-processing steps to do on the original prompt so that down-stream tasks are more directed.

An example of of this is anytime you are speaking in terms of a date or time, there can be some ambiguitiy in how time is expressed, so a pre-processing step might be something like "confirm the specific date in a MM/DD/YYYY format". This is especially helpful in cases where the user implies a date such as "today", etc.

Visually, if we take our goal and break it into a sub-task workflow, it looks like:

<img style="float: right; width: 750px;" src="./images/pct_llm_app_goal_to_sub_tasks.png">

Once we have a logical flow of sub-tasks, we can begin to fit these tasks into a logical architecture that can be implemented by a LLM framework.

## Convert Sub-Task List into Application Architecture

Once we've selected a goal and have broken it into sub-tasks, we can convert this workflow into a logical LLM Application architecture.

We can see the above diagrams generalized into an application workflow below:

<img style="float: right; width: 750px;" src="./images/pct_llm_app_arch_workflow.png">

In the diagram above we can see an agent pre-processing the prompt (e.g., add a template, add context) and then routing to different goal-specific agent. This is helpful when we have a system that has multiple potential goals that can be done depending on the text input.

 If there are multiple major tasks in the application then the system routes the task to an agent that can do specific processing towards the goal. Using a specific agent for a specific goal is helpful as it keeps the sub-task workflow

---

Many times I see engineers talking about "training a new LLM" as soon as they have an idea for a new application, but I believe that to be the wrong place to start. As I wrote in part 1 of this series, you should be focused on the reasoning performance of the LLM you are using. Create some test sub-task LLM model inputs and see how well your chosen pre-trained LLM model performs. Through experimentation you'll find a model that works well for your sub-task sets. A leaderboard of good models:

https://weightwatcher.ai/leaderboard.html

The key is to select a model that has "good enough reasoning ability for the intended task at hand" --- e.g., you wouldn't hire a phd meteorologist to get you coffee from starbucks. It would just be "a waste of the cost of their education".

---



```
The hierarchy of LangChain Modules are loosely:
1. Agents utilize components of LLMs and Tools and
2. Chains utilize PromptTemplates and LLMs where
3. LLMs provide the text generations given an input
```

### Task Composability

Consider the “talk-to-your-data” use case where we want to connect to a database and query this database in natural language. Imagine a credit card transaction table. You want to ask things like: 
"How many unique merchants are there in Phoenix and what are their names?" 
and your database will return: 
"There are 9 unique merchants in Phoenix and they are …".

One way to do this is to write a program that performs the following sequence of tasks:
Task 1: convert natural language input from user to SQL query [LLM]
Task 2: execute SQL query in the SQL database [SQL executor]
Task 3: convert the SQL result into a natural language response to show user [LLM]


# General Architecture of LLM Applications

* diagram here


## LLM Application Workflow




### Prompt Analysis

<img style="float: right; width: 750px;" src="./images/pct_llm_app_arch_prompt_pipeline.png">


### Task Cycle 1

<img style="float: right; width: 750px;" src="./images/pct_llm_app_arch_task_cycle_0.png">

### Task Cycle 2

<img style="float: right; width: 750px;" src="./images/pct_llm_app_arch_task_cycle_1.png">





### Model Variations in LLMs

Models

1. Use a Pre-Trained LLM
2. In-Context Learning with Pre-Trained LLM - Fine-Tune an Existing LLM
3. Use Ray/DGX to Finetune models

### Building a Question / Answer System with LangChain

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

# LLMs, Agents, and Tools

Re-write:
```
Why do LLMs need to use Tools?
One of the most common challenges with LLMs is overcoming the lack of recency and specificity in their training data - answers can be out of date, and they are prone to hallucinations given the huge variety in their knowledge base. Tools are a great method of allowing an LLM to answer within a controlled context that draws on your existing knowledge bases and internal APIs - instead of trying to prompt engineer the LLM all the way to your intended answer, you allow it access to tools that it calls on dynamically for info, parses, and serves to customer.
Providing LLMs access to tools can enable them to answer questions with context directly from search engines, APIs or your own databases. Instead of answering directly, an LLM with access to tools can perform intermediate steps to gather relevant information. 
```

GPT-Plugins ---- link page

### Issues in Integrating LLMs into Applications
https://www.datacamp.com/tutorial/introduction-to-lanchain-for-data-engineering-and-data-applications

### limitations of LLMs

1. Ambiguous inputs + outputs
2. Hallucination vs. factuality
3. Privacy: how to ensure LLMs don’t reveal your user PII info?
4. Unstable infra: performance + latency
5. Inference cost
6. Forward & backward compatibility


## LLMs, Data Modeling, and the Rise of the Semantic Layer


***Play up Cube's semantic layer here --- key to giving LLMs the context they need to understand your data model***


Natural Language Dataset Query with LLMs

Querying Tabular Stores with NL:
https://python.langchain.com/en/latest/use_cases/tabular.html
Using Chains to Query APIs
https://python.langchain.com/en/latest/use_cases/apis.html
Using NL to Query SQL Databases
https://python.langchain.com/en/latest/modules/chains/examples/sqlite.html
https://github.com/hodgesmr/LangChain-Data-Demo



# Summary

something something something