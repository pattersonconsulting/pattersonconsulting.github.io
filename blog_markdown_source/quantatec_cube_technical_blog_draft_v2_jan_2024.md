<!--
---
layout: post
published-on: January 10th 2024
author: Josh Patterson
title: Building Natural Language User Interfaces over Analytics Platforms
subtitle: Using LLMs and the Semantic Layer to Extend Analytics Platforms
description: In this post we'll .....
keywords: aws, bedrock, llm, ai, reasoning workbench, private models
meta_og_image: pct_autogluon_dep_og_card.jpg
---

-->

# Introduction

In the rapidly evolving landscape of knowledge work platforms, the surge in end-user numbers presents both opportunities and challenges for organizations. Training new users on intricate analytics tools is not only a resource-intensive process but also time-consuming. Recognizing this, the integration of a natural language interface into analytics products emerges as a transformative solution, promising a significant reduction in training time and a simultaneous boost in productivity. As technical leaders in Fortune 500 companies navigate the complexities of managing expanding user bases, leveraging advancements in Large Language Models (LLMs) becomes pivotal for staying ahead of the curve. This article delves into the strategic adoption of LLMs, exploring how they serve as a linchpin for next-generation applications, enhancing enterprise value by seamlessly blending human-like text generation with domain-specific knowledge, ultimately redefining the landscape of reasoning applications in 2024.

# Market Trends

notes:
* talk about "a NL interface for anything"

As technical leaders in Fortune 500 companies seek innovative solutions to harness the burgeoning potential of knowledge work platforms, Large Language Models (LLMs) emerge as a transformative force in shaping the next generation of applications. These advanced models showcase remarkable capabilities, ranging from generating human-like text and answering complex questions to assisting with language translation, code writing, summarizing articles, and even creating conversational agents. The intrinsic value of LLM applications for enterprises is further amplified by their ability to seamlessly integrate with and leverage knowledge from enterprise data, including database lookups and document reviews.

In 2024, investing in LLMs for reasoning applications has become a strategic imperative for forward-thinking organizations. The impact of LLMs on enterprise productivity, market share, and profitability is profound, making it a key driver for competitive advantage. This section explores the tangible benefits of incorporating LLMs into the technological fabric of Fortune 500 companies, emphasizing the strategic advantage they confer. Additionally, it delves into the potential risks and costs of inaction, addressing the concerns of late adopters striving to catch up in the fast-paced technological landscape. To effectively bridge the gap between private knowledge and the reasoning power of LLMs, this article introduces the RAG design pattern, providing technical leaders with a roadmap for building next-gen AI applications that leverage the full potential of these language models.

# Challenges

notes: 
* mention the evolution of RAG from last article

In the pursuit of seamlessly integrating Large Language Models (LLMs) into the fabric of analytics products, technical leaders face a myriad of challenges. Among these challenges, the design and implementation of user interfaces for applications stand out as a significant hurdle. This process is not only inherently expensive but also demands end-users to undergo specialized training for each application, contributing to prolonged onboarding times and increased costs. Compounding this issue is the expectation in some cases that analysts should possess knowledge of a programming language, introducing an additional layer of complexity to the usability of analytics tools.

While SQL boasts the broadest adoption within the analyst community due to its user-friendly nature, training large numbers of new users on SQL remains a time-consuming and expensive endeavor. Recognizing these challenges is pivotal for technical leaders navigating the landscape of knowledge work platforms. This section aims to shed light on the obstacles associated with user interface design and skill requirements, paving the way for a strategic exploration of how LLMs can offer a solution to streamline user interactions through Natural Language User Interfaces (NLUIs). By overcoming these challenges, organizations can not only reduce training overhead but also enhance the accessibility of analytics tools, ultimately driving productivity gains within their teams.

# Using LLMs to build Natural Language User Interfaces

note: edit this down some

Addressing the challenges outlined in Section 3, the integration of Large Language Models (LLMs) into analytics products introduces a paradigm shift towards Natural Language User Interfaces (NLUIs). By leveraging LLMs, organizations can transcend the barriers associated with traditional user interfaces, offering end-users the ability to interact with analytics tools in plain English. This transformative approach allows for providing clear and concise answers to questions posed by end-users without the need for specialized training in a particular application or programming language.

The integration process involves harnessing the analytical prowess of LLMs, seamlessly intertwining them with private datasets. These LLMs are not only adept at analyzing and reasoning through plain English questions but also possess the capability to determine the type of information required for each query. Subsequently, they generate comprehensive plain English answers based on the insights extracted from the organization's private data. This approach not only reduces the training time for end-users but also significantly enhances productivity by democratizing access to analytical tools. By adopting NLUIs powered by LLMs, technical leaders can usher in a new era of user-friendly and efficient analytics experiences, ultimately paving the way for the development of next-gen AI applications.

## Using Prompt Routing to Generate Analytical Answers

section outline:

* in an analytics system, we know the N types of questions (Generally) that will be asked
* we can use a prompt router to send the request to different workflows or agents
* this allows us to pre-write certain SQL queries
* once we have the SQL, we can also extract filter criteria such as user, date, etc
* we then run the SQL query manually (retrieval), we serialize the results into a string and insert them into our prompt (augmentation) to generate natural language results

diagrams
1. prompt analysis
2. prompt routing table
3. multi-agent system
4. augmented prompt
5. answer

### Prompt Routing to Multiple Agents

The first stage of the workflow is to use a "prompt router" (e.g., a type of prompt classifier) to classify the prompt into 1 of N "buckets" or types. A typical prompt router looks like:

> code here

LangChain also now offers **code branching** concept (look up)

Once we know what kind of analytical question we're dealing with, we can send the prompt over to an agent or group of agents for further focused processing.

### Prompt Augmentation with SQL Results

Now that we know what kind of query we're dealing with, we need to **retrieve** the relevant information from a knowledge repository to augment our prompt (in a retrieval augmented generation architecture).

In some cases we may not know the database schema and will need to use a tool such as LangChain's SQLChain.

In other cases, however, we can leverage our knowledge of the schema ahead of time and manually write the SQL for our agent. In this case, we can use further focused prompt analysis to determine variables for our SQL such as filter criteria or date ranges. We'll also want to segment out the data that only the current user should be able to see. 

* diagram: SQL Statement

Once we have our SQL data results back, we need to serialize the rows into our prompt to **augment** the existing prompt.

* diagram: prompt with table results embedded

Now we're ready for our agent to pass this augmented prompt on to our LLM for **generation**.

### Generating Natural Language Analytical Results

Now that we have a newly **augmented** prompt, we can pass it over to our LLM to generate a natural language response that is readable by a technical or non-technical user.

# Summary and Webinar

If you enjoyed this article, sign up to watch our webinar with Cube and Quantatec on January 24th where we'll talk about how we put these ideas into practice for Quantatec's new analytics system.

