---
layout: post
published-on: January 10th 2024
author: Josh Patterson
title: How Quantatec Built a Natural Langauge UX for their Embedded Analytics Platform
subtitle: A Case Study of How Patterson Consulting Helped Quantatec Build a Next-Generation Fleet Management Platform
description: In this post we'll .....
keywords: case-study, quantatec, cube, movias, fleet-management, embedded-analytics
meta_og_image: pct_autogluon_dep_og_card.jpg
test_var: "holla holla holla"
---

Editing Notes:
* add a riff on "data engineering for genAI"



# Quantatec Profile

* Industry: SaaS
* Stack: Postgres, Angular, Azure Kubernetes Service, Azure OpenAI, Langchain
* Employees: 15
* Use Case: Natural Language UX for Embedded Analytics
* Headquarters: Sã0 Paulo, Brazil

# Overview

## Quantatec's Challenge

Customers were asking for complex custom reports that required a sophisticated user interface to configure for each report. This interface was cumbersome to build and also not easy for new users to quickly learn.

## Patterson Consulting's Solution

The Patterson Consulting team brought three critical peices to the engagement:

* Data engineering expertise in setting up both cloud data platforms and data pipelines 
* In-house custom methods for getting consistent answers with private enterprise data and large language models
* A professional engineering process that kept Quantatec's end goals in mind setting them up for future success

# Making Fleet Management Data-Driven

With more than 32 years of experience in automotive electronics and more than 23 years of leadership and innovation in the automotive tracking segment, Brazilian company Quantatec specializes in tracking, logistics control, fleet management, accident, and cost reduction for fleets of vehicles of any type and size.

Quantatec provides fleet managers access to their tracking device data in Movias, their exclusive fleet management platform. Mauricio Cirelli manages the Movias platform. The embedded analytics solution, available on the web and mobile, presents account-specific data to hundreds of customers in South America. Six million tracker messages are received and processed daily, amounting to about 1TB of data annually.

# Quantatec's Challenge

Before Cube, Quantatec’s multi-tenant embedded analytics solution delivered static, hard-coded reports with basic filtering. Fleet managers soon wanted customizations, such as adding a column for the driver’s name or the fleet name to the report. Each request was slightly different. The team would either create a new report or modify an existing one in a way that would not impact others.

Demand was high. A growing number of unique SQL queries for the current user were sent to the database to return account-specific data. The increased volume of direct database queries combined with real-time data processing from over 10,000 devices resulted in unpredictable database performance and degraded customer experience.

* diagram

When customers began asking for their own interactive dashboards and the ability to customize them, Mauricio knew that more custom queries would only add to the existing performance issues. He began searching for a solution. It turned out to be just the beginning of a series of major innovations for Quantatec’s customers.

# Results

 Inspired by Patterson Consulting’s demo to showcase an LLM chatbot's potential, Mauricio imagined a user-friendly, chat interface over Quantatec’s fleet data. Mauricio partnered with Patterson Consulting to realize his vision.

## Improving the User Experience with Natural Language

Using the Cube’s universal semantic layer, OpenAI API, and LangChain framework, Mauricio and Josh introduced Movias AI, a chatbot interface, capable of interpreting natural language queries and fetching relevant data from Cube's cache or database as needed. Development took only about six weeks from POC to production. With chatbot integration, Quantatec provided a truly unique experience to deliver data to fleet managers. Questions can be written in any language supported by the LLM. In particular, English, Spanish and Brazilian Portuguese were evaluated.

Connecting the next-generationa with large language models also required a non-trivial amount of data engineering work to get the integration correct. The Patterson Consulting team leverage their experience working on data pipelines and in data modeling to create the right integration for LangChain and the Generative AI engine.

## Making Self Service Easier by Making Data Conversational

Mauricio shared, “Ultimately, fleet managers have questions and want them to be answered. We can do that by providing them a report or a dashboard, but it is much more efficient for them to just ask the system and get a clean response to their questions.

Combining the power of the universal semantic layer’s with Patterson Consulting's Generative AI expertise, Quantatec revolutionized fleet management operations, empowering fleet managers to extract actionable insights with ease.

# Why Patterson Consulting?

Patterson Consulting has consistently demonstrated the forward-looking expertise in data engineering, Azure, and large language models to build Generative AI applications. Our project scoping process was detailed and clearly communicated expectations to Quantatec on how the project would be run and what they could expect for delivered functionality.

Mauricio Cirelli of Quantatec states:

> “We worked with Patterson Consulting on this Generative AI project. We wanted a large language model (LLM) to answer customer’s questions about their own fleet data and Patterson Consulting helped us to integrate the LLM properly and provide consistent quality answers to the user. They delivered the project on schedule, well documented and according to all specs we had defined in the SoW. It was a pleasure and a profit to work with them.”


# Call To Action

* Take the next step with Patterson Consulting








