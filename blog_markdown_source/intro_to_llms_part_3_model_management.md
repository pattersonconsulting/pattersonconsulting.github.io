---
layout: post
published-on: March 27th 2023
author: Josh Patterson
title: An Introduction to Large Language Models (LLMs)
subtitle: Part 3 - Model Training and Management in LLMs
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

# Which Model Should I Use for My LLM Application?

todo

## API vs In-House Models

asdasd


## The Cost of Cloud APIs at Scale

link work here

https://huyenchip.com/2023/04/11/llm-engineering.html


```
The more explicit detail and examples you put into the prompt, the better the model performance (hopefully), and the more expensive your inference will cost.
OpenAI API charges for both the input and output tokens. Depending on the task, a simple prompt might be anything between 300 - 1000 tokens. If you want to include more context, e.g. adding your own documents or info retrieved from the Internet to the prompt, it can easily go up to 10k tokens for the prompt alone.
The cost with long prompts isn’t in experimentation but in inference.

Experimentation-wise, prompt engineering is a cheap and fast way get something up and running. For example, even if you use GPT-4 with the following setting, your experimentation cost will still be just over $300. The traditional ML cost of collecting data and training models is usually much higher and takes much longer.
* Prompt: 10k tokens ($0.06/1k tokens)
* Output: 200 tokens ($0.12/1k tokens)
* Evaluate on 20 examples
* Experiment with 25 different versions of prompts

```

```
The cost of LLMOps is in inference.
* If you use GPT-4 with 10k tokens in input and 200 tokens in output, it’ll be $0.624 / prediction.
* If you use GPT-3.5-turbo with 4k tokens for both input and output, it’ll be $0.004 / prediction or $4 / 1k predictions.
* As a thought exercise, in 2021, DoorDash ML models made 10 billion predictions a day. 
   * If each prediction costs $0.004, that’d be $40 million a day!
* By comparison, AWS personalization costs about $0.0417 / 1k predictions and AWS fraud detection costs about $7.5 / 1k predictions [for over 100,000 predictions a month]. AWS services are usually considered prohibitively expensive (and less flexible) for any company of a moderate scale.


```

# How are LLM Models Customized or Trained?

now this is an interesting topic!

## In-Context Learning



## Fine-Tuninng

### When Should I Fine-Tune a Model?

Currently there is no great heuristic here for the threshold to fine-tune over using advanced context mechanics
Does using Context Mechanics give you a “good enough” result for the current problem?
if no, then it may be worth experimenting with fine-tuning

Context
Some papers suggest you need around 50K examples in order to improve alignment. 
So if you have that many examples maybe it's worth it.
Fine-tuning needs to improve “alignment” ultimately for any use case
I think in the context of LLMs the purpose of "fine tuning" is really "alignment"; 
that is to better align model outputs with the intended task. 



## RHLF --- other stuff


## LLM Training Data

Training Data for Stanford Alpaca

https://raw.githubusercontent.com/tatsu-lab/stanford_alpaca/main/alpaca_data.json


## The Impact of Parameter Sizes in LLMs

there are light weight models that are approaching the quality of chat GPT.  
It's a space to watch.  
There is reason to believe this will all be very accessible on consumer grade hardware soon


### GPU Memory as Upper Ceiling

1GB == 1B paramters


# General Architecture of LLM Applications


diagram here


