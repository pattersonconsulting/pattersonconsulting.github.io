---
layout: post
published-on: March 27th 2023
author: Josh Patterson
title: Building Next-Generation LLM Applications with Private Models
subtitle: Using the Reasoning Workbench to Better Select Private LLM Models
description: In this post we'll .....
keywords: aws, bedrock, llm, ai, reasoning workbench, private models
meta_og_image: pct_autogluon_dep_og_card.jpg
---


You are a smart business analyst and writer. You are writing an article for Amazon Web Services Partner Network Blog.

Below is the outline for the article.

# Section 1: Introduction

* At AWS Re:Invent 2023 there were many new announcements in the realm of Generative AI
* AWS Bedrock is quickly emerging as a go to platform for deploying Generative AI applications


* Why invest in LLM for reasoning applications in 2024
   * LLM impact for enterprise on productivity, marketshare, profitability
   * Enterprise risk and cost of inaction, Can late adopters catch up





# Section 2: Trends

* Examples/characteristics of LLM applications
   * generate human-like text, answer questions, assist with language translation, write code, summarize article, create conversational agents
   * Enterprise value of LLM application is often increased by incorporating knowledge of the enterprise data (database lookup, document review).

* One key requirement to operate private appliations will be the need to use private models (e.g., "not openAI") when using private data

https://www.wsj.com/tech/ai/openai-turmoil-pushes-customers-to-diversify-d888b253

* We use the RAG design pattern to connect our private knowledge with the reasoning power of LLMs to build next-gen AI apps on AWS




# Section 3: Building LLM Applications

* We want to think about LLM applications in the terms of "knowledge vs reasoning", where our enterprise data in AWS is the knowledge, and LLM models provide the reasoning

* different models are more effective at different types of sub-tasks

* Choosing the correct private model, however, can be tricky


# Section 3.1 : Choosing a LLM Model

* openAI has powerful models such as GPT3 and GPT4, but these models are difficult to run as private LLM model isntances
* smaller private models typically are more efficient to operate, but they have less horsepower in certain types of reasoning
* To build efficient, cost-effective AI applications we need a way to compare different models for our specific tasks with our data


# Section 3.2: The Reasoning Workbench

* Patterson Consulting has led the development of the open source tool called the "Reasoning Workbench"
* the Reasoning Workbench is an easy and direct way to generate scores to compare different models 
* this tool can you quickly get a relative sense/measure for which model works best for your sepecific AI application


# Section 3.3: Benefits of Evaluating Models with the Reasoning Workbench

* being able to quickly pick the best model for your use case allows your team to act quickly and decisively deploy new AI apps with confidence
* better models are less costly to operate (less tokens)
* smaller models require less costly cloud resources to operate, therefore are cheaper to run (what is model size to performance tradeoff? how do you quickly evaluate this?)
* applications require less prompt engineering, which allows us to do fewer inferences to our private models
* all of the above gives the end user a faster and more efficient user experience



# Section 5: Using the Reasoning Workbench on AWS

* load the notebook into AWS Sagemaker Studio Lab
* configure the models.json file and the prompts.json file
* the notebook will automatically pull in the reasoning_workbench python module


# Section 5.1: Generating the JSON Scorecard

* if you don't supply custom prompts, it won't generate a "use case score" in the radar plot
   * NOTE: in this case, we should gather perf metrics with a set of stock prompts

* if you have custom prompts, then we'll need a GPU instance to generate scores
   * NOTE: we should also gather inference performance metrics while evaluating the prompts

* run the notebook, the json output will be generated and saved locally ------ note: may want to omit this detail for now

# Section 5.2: Generating the PDF Report

* run the last cell, and a pdf report scorecard will be generated from the json file


# Section 6: Interpreting the Report

* what are we looking at?
* how to read the radar plot
* the benefit of using custom prompts to evaluate models

# Section 7: Next Steps


* what can we do now?


# Section 7.1: Deploy to AWS Bedrock

* deploy the model for further testing



Write 1-2 paragraphs for section 1 of the article based on the outline above. Your audience in the CXO-level in Fortune 500 companies.


# Prompts and Instructions

You are a smart business analyst and writer. You are writing an article for Amazon Web Services Partner Network Blog.

Below is the outline for the article.


