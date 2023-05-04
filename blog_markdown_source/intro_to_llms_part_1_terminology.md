---
layout: post
published-on: March 27th 2023
author: Josh Patterson
title: An Introduction to Large Language Models (LLMs)
subtitle: Part 1 - Core Concepts and Terminology in LLMs
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

# What are Large Language Models (LLMs)?

todo

https://www.theatlantic.com/technology/archive/2023/01/artificial-intelligence-ai-chatgpt-dall-e-2-learning/672754/

## Terminology in LLMs



## Deep Learning, Transformers, and Deep Learning

todo

https://amatriain.net/blog/transformer-models-an-introduction-and-catalog-2d1e9039f376/

* DL is about automated feature learning

todo

* dont need to create features
* can use tons of data
* can use tons of parameters

## You Don't Have to Re-Train the Foundation Models to Do Things

It's amazing

# Generative Language Models

todo

* refernece our strata talk in 2016

## GPT Architecture

* based on transformers
* doesnt need feature engineering
* just give it structured set of natural language

## Trends in Model Parameter Sizes

* todo

## Specializing Smaller Models for Specific Performance

[ICML 2023] Specializing Smaller Language Models towards Multi-Step Reasoning.

https://arxiv.org/abs/2301.12726

```
We show that such abilities can, in fact, be distilled down from GPT3.5 (≥ 175B) to T5 variants (≤ 11B)

. We propose
model specialization, to specialize the model’s
ability towards a target task. The hypothesis is
that large models (commonly viewed as larger
than 100B) have strong modeling power, but are
spread on a large spectrum of tasks. Small models (commonly viewed as smaller than 10B) have
limited model capacity, but if we concentrate their
capacity on a specific target task, the model can
achieve a decent improved performance
```

https://github.com/FranxYao/FlanT5-CoT-Specialization


# LLM Abilities


## Prompts and Prompt Engineering

todo

https://exchange.scale.com/public/events/llm-prompt-engineering-and-rlhf-history-and-techniques-2023-03-09

https://lilianweng.github.io/posts/2023-03-15-prompt-engineering/

https://github.com/dair-ai/Prompt-Engineering-Guide

https://www.pinecone.io/learn/langchain-prompt-templates/

## In-Context Learning

todo

https://datascience.stackexchange.com/questions/115554/how-exactly-does-in-context-few-shot-learning-actually-work-in-theory-under-the

https://arxiv.org/pdf/2005.14165.pdf

https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00485/111728/True-Few-Shot-Learning-with-Prompts-A-Real-World

http://ai.stanford.edu/blog/understanding-incontext/

### In-Context Learning and Indexing

todoo

## Emergent Abilities of Language Models

https://yaofu.notion.site/How-does-GPT-Obtain-its-Ability-Tracing-Emergent-Abilities-of-Language-Models-to-their-Sources-b9a57ac0fcf74f30a1ab9e3e36fa1dc1



## Reasoning vs Knowledge

## Chain of Thought


## Decomposed Prompting

[ICLR 2023] Decomposed Prompting: A Modular Approach for Solving Complex Tasks. [paper][code]


# LangChain

https://blog.langchain.dev/structured-tools/

https://github.com/kyrolabs/awesome-langchain

https://www.pinecone.io/learn/langchain-intro/

https://www.pinecone.io/learn/langchain-agents/


https://blog.langchain.dev/announcing-our-10m-seed-round-led-by-benchmark/

## LangChain Thoughts

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


# Other

https://cube.dev/blog/conversational-interface-for-semantic-layer

https://github.com/approximatelabs/sketch
