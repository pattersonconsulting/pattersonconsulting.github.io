---
layout: post
published-on: March 27th 2023
author: Josh Patterson
title: Building Enterprise Applications with Large Language Models
subtitle: Part 3 - Putting LLM Applications into Production
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

* [An Introduction to Large Language Models (LLMs)](intro_to_llms_part_1_terminology.html)
* [Understanding Use Cases for Large Language Models](intro_to_llms_part_2_use_cases.html)
* [Design Patterns for Large Language Model Applications](intro_to_llms_part_3_design_patterns.html)
* [Putting LLM Applications into Production](intro_to_llms_part_4_model_management.html)
* [Appendix A: What is Artificial Intelligence?](dl_book_appendix_a_ai.html)

# Which Model Should I Use for My LLM Application?

todo

Numbers every LLM developer should know:

https://github.com/ray-project/llm-numbers


Ray used to train gpt-3

https://www.anyscale.com/blog/ray-common-production-challenges-for-generative-ai-infrastructure

https://thenewstack.io/how-ray-a-distributed-ai-framework-helps-power-chatgpt/

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

High computational requirements: Training and deploying large language models require significant computational resources, making them inaccessible to many researchers and organizations. This can hinder widespread adoption and contribute to the concentration of AI capabilities in a few entities.

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


https://huyenchip.com/2023/06/07/generative-ai-strategy.html

7B param model can run on a Macbook

### GPU Memory as Upper Ceiling

1GB == 1B paramters






# Other Considerations for Deploying Large Language Model Applications

todo

## Closed Source vs Open Source Models

* todo

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


Smaller models performing

https://albertoromgar.medium.com/the-era-of-large-ai-models-is-over-a5c9d7d804d4

```
Don’t conflate the reduced size of these models with them being inferior performance-wise: LLaMA 13B benchmark results are comparable to GPT-3 175B despite the latter being 13x larger. Three years have sufficed to improve the state-of-the-art on variables other than size (e.g., finetuning techniques, data quality, or hardware-software optimizations) so that the largest models of 2020 will be eventually dwarfed by the efficiency of much smaller new ones.

https://twitter.com/GuillaumeLample/status/1629151231800115202
```


# Summary

