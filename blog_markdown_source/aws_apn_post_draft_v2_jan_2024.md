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



# Section 1: Introduction

At AWS Re:Invent 2023, the landscape of Generative AI witnessed a wave of innovations, and among the emerging platforms, AWS SageMaker and AWS Bedrock stand out as the go-to choices for deploying Generative AI applications. In the realm of Large Language Models (LLMs), the year 2024 holds significant promise for businesses, where the adoption of LLMs can substantially impact productivity, market share, and profitability. However, as we delve into the potential benefits, we must also navigate the landscape of enterprise risk and the cost of inaction for late adopters. In this article, we'll explore why investing in LLMs for reasoning applications is a strategic move and how enterprises can harness their power for a competitive edge. The aim is to provide both technical founders and VP of Engineering a comprehensive understanding of the trends, challenges, and practical considerations in incorporating LLMs into their AI strategies.

# Section 2: Trends

<!--
The capabilities of LLM applications are broad and encompass generating human-like text, answering questions, language translation, code writing, article summarization, and creating conversational agents. Notably, the enterprise value of LLM applications is augmented by incorporating knowledge from proprietary data repositories such as databases and documents. However, the challenge lies in balancing the power of reasoning provided by LLMs with the need to secure private data. This dichotomy leads to a fundamental consideration: the use of private models is essential when dealing with sensitive data to avoid exposing it to external models and logging systems. This article delves into the trends shaping the deployment of LLMs, shedding light on the strategic considerations for technical leaders navigating this transformative landscape.
-->

The allure of Large Language Models (LLMs) takes center stage in 2024, offering enterprises a transformative edge in enhancing productivity, expanding market share, and boosting profitability. 

What sets these models apart is their ability to generate human-like text, answer queries, assist in language translation, code writing, summarizing articles, and even creating conversational agents. The true power of LLM applications, especially in an enterprise context, lies in their synergy with private data repositories, leveraging knowledge from databases and documents. However, a key consideration arises – the need for private models, ensuring data security and mitigating risks associated with exposing sensitive customer information to external models and logging systems. This article navigates the evolving trends and strategic considerations in harnessing the potential of LLMs for reasoning applications, emphasizing the pivotal role of private models in this transformative journey.

# Section 3: What to Look Out for When Building LLM Applications

Navigating the integration of Large Language Models (LLMs) into enterprise applications requires a nuanced understanding of the interplay between knowledge and reasoning. In the realm of LLM applications, the distinction between enterprise data as "knowledge" and the LLM models providing the "reasoning" becomes paramount. For Fortune 500 companies, the challenge lies in effectively augmenting prompts with proprietary data from internal repositories, such as data warehouses and S3, while maintaining robust data security protocols. An essential consideration is the potential exposure of private customer data when utilizing external models like those from openAI, making it imperative for technical leaders to assert control over their models. Differentiating between LLM models, such as the powerful yet challenging-to-operate GPT-3 and GPT-4 from openAI, and smaller, more efficient private models becomes a key task in building efficient, cost-effective AI applications.

The selection of an appropriate private model introduces complexities, considering that smaller models may be more operationally efficient but might lack the horsepower required for certain reasoning tasks. Addressing these challenges, the article explores the "Reasoning Workbench," an open-source tool developed by Patterson Consulting. This tool provides a systematic approach to evaluating and comparing different LLM models, offering technical leaders a means to generate scores and make informed decisions based on their specific use cases. 

By delving into the intricacies of model selection and operational efficiency, this section aims to equip technical VPs of Engineering with the insights needed to navigate the labyrinth of LLM applications successfully.

## Section 3.1 : Challenes in Choosing a LLM Model

Choosing the right Large Language Model (LLM) for enterprise applications poses a distinct set of challenges, especially when considering the balance between power and operational feasibility. While openAI's models like GPT-3 and GPT-4 are undeniably powerful, their integration as private LLM instances can be intricate and resource-intensive. This complexity can be a hindrance for Fortune 500 companies aiming for streamlined and secure operations. On the other end of the spectrum, smaller private models offer efficiency but may lack the computational prowess required for certain reasoning tasks. Striking the right balance is crucial, and technical VPs of Engineering must grapple with the intricacies of evaluating different models for specific tasks with their unique datasets.


## Section 3.2: The Reasoning Workbench

To address these challenges, the article introduces the concept of the "Reasoning Workbench," an open-source tool crafted by Patterson Consulting. This tool provides a practical and direct method for generating scores that allow technical leaders to compare different LLM models effectively. By leveraging the Reasoning Workbench, technical VPs can gain a relative understanding of how various models perform in the context of their enterprise applications. This section dives into the nuances of model selection, shedding light on the importance of efficiency, computational horsepower, and the overall operational considerations when navigating the landscape of private LLMs for Fortune 500 companies.



## Section 3.3: Benefits of Evaluating Models with the Reasoning Workbench

The adoption of the "Reasoning Workbench" introduces a strategic advantage for technical VPs of Engineering in Fortune 500 companies by streamlining the process of evaluating Large Language Models (LLMs). This open-source tool, spearheaded by Patterson Consulting, facilitates the quick and efficient comparison of different LLMs, providing a relative measure for selecting the most suitable model for specific AI applications. The benefits of employing the Reasoning Workbench extend beyond mere model selection; it empowers technical leaders to act decisively, confidently deploying new AI applications with an acute understanding of each model's performance nuances. Moreover, the tool aids in optimizing operational costs by identifying models that are not only more effective in terms of performance but also less token-intensive, translating to a more economical use of cloud resources. This section serves as a practical guide for technical VPs, emphasizing the pivotal role of the Reasoning Workbench in expediting decision-making processes, reducing costs, and ultimately enhancing the end-user experience in the deployment of private LLMs on AWS.



# Section 4: Using the Reasoning Workbench on AWS

* todo --

## Section 4.1: Writing a Configuration File

Deploying the "Reasoning Workbench" on AWS SageMaker Studio Lab is easy. The process begins by loading the notebook into AWS SageMaker Studio Lab, seamlessly integrating the Reasoning Workbench Python module. Section 5.1 guides technical leaders through the configuration of essential files, namely the models.json and prompts.json files, which play a crucial role in tailoring the Reasoning Workbench to the specific needs of the enterprise. Each entry in these JSON files corresponds to a model hosted on HuggingFace, affording a structured approach to organizing and comparing various LLMs. This section demystifies the initial steps of deploying the Reasoning Workbench on AWS, setting the stage for the subsequent exploration of generating comprehensive model reports and empowering technical VPs with actionable insights for optimal LLM selection and deployment.

## Section 4.2: Generating the Model Report

Section 5.2 of this technical article delves into the pivotal process of generating a comprehensive model report using the deployed "Reasoning Workbench" within AWS SageMaker Studio Lab. 

As technical VPs navigate this critical step, the article outlines the tangible outputs that result from running the notebook. 

The generated JSON file encapsulates a wealth of data, providing a detailed performance analysis for each model. Additionally, the inclusion of radar plot images sheds light on both the general and use-case-specific performance of each LLM, offering a visual representation that aids in quick and effective model comparison. By elucidating the intricacies of these outputs, the article equips technical leaders with actionable insights, enabling them to make informed decisions regarding the selection and deployment of LLMs tailored to the specific needs of their Fortune 500 enterprises. Furthermore, the section underscores the significance of custom prompts, acknowledging their potential to refine the evaluation process and generate nuanced use-case scores, thereby enhancing the precision of model assessments in the AWS environment.




