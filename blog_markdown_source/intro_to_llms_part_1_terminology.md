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

This space is moving fast and its valuable to get a mental framing on how to think about LLMs to better understand how to apply them in your projects and organization

It also sets context for a better understanding of new developments in LLMs

Our technical series are based on private reports we produce for our enterprise customers.

The intended audience for this series is:

> Individual researchers, data scientists, and then also enterprise data teams as well

Series:

* [Core Concepts and Terminology in LLMs](intro_to_llms_part_1_terminology.html)
* [LLMs and Enterprise Applications](intro_to_llms_part_2_applications.html)
* [Model Training and Management in LLMs](intro_to_llms_part_3_model_management.html)

# What are Large Language Models (LLMs)?

todo

https://www.theatlantic.com/technology/archive/2023/01/artificial-intelligence-ai-chatgpt-dall-e-2-learning/672754/

emergent abilities

https://www.quantamagazine.org/the-unpredictable-abilities-emerging-from-large-ai-models-20230316/

LLMs having their "stable diffusion"-moment

https://simonwillison.net/2023/Mar/11/llama/

## Terminology in Large Language Models (LLMs)

todo

### Prompts and Prompt Engineering

todo

https://exchange.scale.com/public/events/llm-prompt-engineering-and-rlhf-history-and-techniques-2023-03-09

https://lilianweng.github.io/posts/2023-03-15-prompt-engineering/

https://github.com/dair-ai/Prompt-Engineering-Guide

https://www.pinecone.io/learn/langchain-prompt-templates/

todo

### In-Context Learning



### Indexing



### Embeddings



## Deep Learning, Transformers, and Generative Language Models

todo

https://amatriain.net/blog/transformer-models-an-introduction-and-catalog-2d1e9039f376/

### Defining Deep Learning

* DL is about automated feature learning


### Introduction of Transformers in 2017

todo

* dont need to create features
* can use tons of data
* can use tons of parameters

LLMs are implemented with Neural Networks 
using the Transformer architecture
Transformers were introduced in 2017
they are an architecture of deep learning neural networks that worked well in natural language applications

Transformers can process long sequences of text and generate high-quality outputs for various language tasks, such as 
* text generation
* question answering
* translation

Noteworthy because:

Deep Learning is about using the correct architecture for a data type such that the architecture can perform automated feature engineering
Transformers are a Deep Learning architecture for natural language
Therefore, Transformer-based systems require no manual feature engineering

Transformers and LLMs rely directly on raw natural language text as the input


### Generative Language Models

todo

* refernece our strata talk in 2016

## The GPT Architecture

* based on transformers
* doesnt need feature engineering
* just give it structured set of natural language


### GPT Series of Models

https://platform.openai.com/docs/models


### ChatGPT

https://help.openai.com/en/articles/6783457-what-is-chatgpt
```
ChatGPT is fine-tuned from GPT-3.5, a language model trained to produce text. ChatGPT was optimized for dialogue by using Reinforcement Learning with Human Feedback (RLHF) – a method that uses human demonstrations and preference comparisons to guide the model toward desired behavior.
```

### Training Data for GPT

https://arxiv.org/abs/2005.14165


# LLM Abilities



## GPT-3 Abilities and Evolution

https://yaofu.notion.site/How-does-GPT-Obtain-its-Ability-Tracing-Emergent-Abilities-of-Language-Models-to-their-Sources-b9a57ac0fcf74f30a1ab9e3e36fa1dc1

Yao Fu writes about the 3 important abilities that the initial GPT-3 exhibit:
 
- **Language generation**: to follow a prompt and then generate a completion of the given prompt. Today, this might be the most ubiquitous way of human-LM interaction.
- **In-context learning**: to follow a few examples of a given task and then generate the solution for a new test case. It is interesting to note that, although being a language model, the original GPT-3 paper barely talks about “language modeling” — the authors devoted their writing efforts to their visions of in-context learning, which is the real focus of GPT-3.
- **World knowledge**: including factual knowledge and commonsense.

Fu goes on to describe the origin of the abilites of GPT-3:

> Generally, the above three abilities should come from large-scale pretraining — to pretrain the 175B parameters model on 300B tokens 

* 60% 2016 - 2019 Common Crawl
* 22% WebText2
* 16% Books
* 3% Wikipedia). 

Where:

- The **language generation** ability comes from the language modeling **training objective**.
- The **world knowledge** comes from the 300B token **training corpora** (or where else it could be).
- The **175B model size** is for **storing knowledge**, which is further evidenced by Liang et al. (2022), who conclude that the performance on tasks requiring knowledge correlates with model size.
- The source of the **in-context learning** ability, as well as its generalization behavior, **is still elusive**. Intuitively, this ability may come from the fact that data points of the same task are ordered sequentially in the same batch during pretraining. Yet there is little study on why language model pretraining induces in-context learning, and why in-context learning behaves so differently than fine-tuning.

<!--
Yao Fu then goes on to offer a diagram (embedded below) showing the evolution tree of GPT-3

![GPT Abilities](https://yaofu.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F2ea67e8e-18e1-42d0-9bd9-dbb1f47e22f0%2FUntitled.png?id=a039705a-5a32-41ef-bfb7-1c2793e90e74&table=block&spaceId=281b3c78-d734-43fb-aa33-707babff9463&width=1150&userId=&cache=v2)

Some abilities of note in the above diagram:
-->

For reference, if we say the average book has 80,000 words in it, and ~2 million tokens is roughly the equivalent to 1.5 million words, we can calculate the total books GPT-3 was trained on to be **around 2.8 million books** based on a 300 billion token training corpora.

For comparison, the average person might read around 700 books in their lifetime.

The entire series is wonderful for insight into how large language models such as GPT-3 get certain types of "abilities" such as "code generation" and "in-context learning".

## LLMs and Knowledge Lookup

* define knowledge
* explain use in people and in LLMs
* discuss specific abilities of GPT-3

## LLMs and Reasoning Abilities

* define reasoning
* explain and contrast reasoning vs knowledge
* discuss specific abilities of GPT-3

More Yao Fu:

> Now let’s look at code-davinci-002 and text-davinci-002, the two first GPT3.5 models, one for code and the other for text. There are four important abilities they exhibit that differentiate them from the initial GPT-3

- **Responding to human instruction**: previously, the outputs of GPT-3 were mostly high-frequency prompt-completion patterns within the training set. Now the model generates reasonable answers to the prompt, rather than related but useless sentences.
- **Generalization to unseen tasks**: when the number of instructions used for tuning the model is beyond a certain scale, the model can automatically generate completions for new instructions that are not in the training set. **This ability is crucial for deployment**, as users with always come up with new prompts.
- **Code generation and code understanding**: obviously, because the model is trained on code.
- **Complex reasoning** **with chain-of-thought**

## In-Context Learning

todo

https://datascience.stackexchange.com/questions/115554/how-exactly-does-in-context-few-shot-learning-actually-work-in-theory-under-the

https://arxiv.org/pdf/2005.14165.pdf

https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00485/111728/True-Few-Shot-Learning-with-Prompts-A-Real-World

http://ai.stanford.edu/blog/understanding-incontext/

## Emergent Abilities of Language Models

https://yaofu.notion.site/How-does-GPT-Obtain-its-Ability-Tracing-Emergent-Abilities-of-Language-Models-to-their-Sources-b9a57ac0fcf74f30a1ab9e3e36fa1dc1


## Chain of Thought


## Decomposed Prompting

[ICLR 2023] Decomposed Prompting: A Modular Approach for Solving Complex Tasks. [paper][code]


# Why Are Large Language Models Compelling?

todo

## Tectonic Plate Shifts in Technology

todo

## Natural Language as a Driver for Any Application

toodo

ChatGPT was a nice demo, but there is a lot more here


## You Don't Have to Re-Train the Foundation Models to Do Things

It's amazing


# Summary

https://cube.dev/blog/conversational-interface-for-semantic-layer

https://github.com/approximatelabs/sketch
