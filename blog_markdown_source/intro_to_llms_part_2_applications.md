---
layout: post
published-on: March 27th 2023
author: Josh Patterson
title: An Introduction to Large Language Models (LLMs)
subtitle: Part 2 - LLMs and Enterprise Applications
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
* [Appendix A: What is Artificial Intelligence?](dl_book_appendix_a_ai.html)

# Profiling Use Cases for LLMs


## Raw Source Notes

`
What are common LLM use cases? If I had to roughly categorize the use cases I'm hearing people ask about in the enterprise, in 2023, after the rise of ChatGPT, it's something like:

- 40% question-answering: query a corpus of text in natural language
- 10% chat: same, but interactive
- 20% extraction / summarization: what are the top N issues in these 10,000 reviews? 
- 20% (semi-)structured natural language querying: answer from SQL query results
- 10% other sci-fi use cases: write my business strategy

Of course, there are a number of use cases too that I'd describe as simply not LLM problems. I've heard forecasting a few times. Even regression! Why?

Some are too sci-fi, like, migrate my whole legacy data warehouse. I think that's interesting. You show people a bit of magic, and it's not at all clear how deep the magic goes. LLMs are a little magic, not the Starship Enterprise. Language models, not actually sentient. But you'd be forgiven for assuming otherwise.

Conspicuously missing from the conversations I've seen are:

- Translation, classification: these are real use cases, just, those that want to do this have already been doing this
- Content generation: write a response to this customer. I suppose individuals are doing this with ChatGPT?
- Code generation: already well in hand with Copilot et al

It's not surprising that natural-language querying over, well, natural language is a leading use case. It's a natural fit for LLMs, and is quite easy already. I think these will rapidly get implemented and productized. More targeted extractive queries are a little harder at the margins but seem well within the capability of LLMs.

The interesting frontier for the rest of the year is IMHO SQL generation. Everybody has a database, it's an obvious use case, and it's at least not-infeasible now. It's just hard to do well enough, reliably enough to consider turning loose at scale, I think. It works OK now if you assume this is fundamentally a code assistant for SQL analysts, something to create a first draft that they'll correct. It does not work if you assume the audience are users who would not know the correct answer, let alone SQL, when they saw it.

This is a problem that will probably get solved well enough in the next year, such that there are services and OSS models that are close enough, to make this a next big focus.

That's an interesting topic for another day!
`

## Issues in Integrating LLMs into Applications
https://www.datacamp.com/tutorial/introduction-to-lanchain-for-data-engineering-and-data-applications



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



# Application Frameworks and Components

asdasd

## LangChain

https://blog.langchain.dev/structured-tools/

https://github.com/kyrolabs/awesome-langchain

https://www.pinecone.io/learn/langchain-intro/

https://www.pinecone.io/learn/langchain-agents/


https://blog.langchain.dev/announcing-our-10m-seed-round-led-by-benchmark/


https://medium.com/@gk_/chatgpt-and-langchain-an-attempt-at-scheduling-automation-part-3-of-3-db65906ab581
```
Langchain is on a productive and crucially important path, but things are still quite raw. This is to be expected. The github repo for Langchain began in October ‘22.

New models will inevitably interact with these chains and their ‘agents’ in new ways such that the chain infrastructure will need to evolve with the models over time.

The use of natural language to interact with Python function return values is intriguing. The benefit of this is not having to tightly couple APIs, the downside is the llm is in a trial-and-error mode with the tools.

It seems clear that agent instructions (the prompts) need to be specialized to the type of automation needed. This is natural, if we hired a human to perform the task of scheduling they would need instructions.
Overall…
A fusion of functional code and LLMs is inevitable. Both must work together to create automation pathways.

The use of natural language in managing programmatic functions (‘tools’) seems promising however once the llm has found the correct calling format it should remember it rather than repeating the trial&error each time.

A chat model is fine so long as it considers at least 3-parties in the conversation: a) the customer/user, b) the chatbot, and c) the business representative
```

## Vector Databases

* ChromaDB
* Pinecone
* Vectera
* [ todo: more ]

## Model Servers

* [ todo: source ]



# Implementing LLMs in Applications



## General Architecture of LLM Applications


diagram here


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
