---
layout: post
published-on: March 27th 2023
author: Josh Patterson
title: Prologue (Don't Panic)
subtitle: The Hitchhiker's Guide To Building Modern Data Products
description: In this post we'll .....
keywords: snowflake, snowpark, automl, AutoGluon, pandas, dataframe, whl, pip, anaconda, dependency
meta_og_image: pct_autogluon_dep_og_card.jpg
---

# Introduction

Purpose of this series:

> To develop a clear step-by-step process to design and operate data infrastructure for your data product.

The intended audience for this series is:

> Individual researchers, data scientists, and then also enterprise data teams as well

Series:

* [Prologue (Don't Panic)](hitchhikers_guide_modern_data_products_1_prologue.html)
* [The Evolution of Modern Data Platforms](hitchhikers_guide_modern_data_products_2_evolution_data_platforms.html)
* [Revisting The Lab and the Factory](hitchhikers_guide_modern_data_products_3_lab_and_factory_redux.html)
* [A Methodology for Building Data Products](hitchhikers_guide_modern_data_products_4_methodology_for_data_products.html)
* [Appendix A: Definitions](hitchhikers_guide_modern_data_products_5_appendix_A_definitions.html)

## How to Read The Series

If you don't care about the history and evolution stuff, maybe just skip to part 3 [Revisting The Lab and the Factory](hitchhikers_guide_modern_data_products_3_lab_and_factory_redux.html) -- otherwise, this Prologue and then the Evolution of Data Platforms should be fun background reading.

We spend the first 3 posts of this series providing background and definitions to set the stage for our methodology and in part 4 we lay out our step by step process.

## Purpose of This Series

I wrote this series for 3 reasons:

1. To better lay out my own thesis for building data products through long-form writing
2. To give our customers a more complete guide on building data products that can be shown in a 20-minute slide deck
3. To create a set of architectural guidelines for our team to use when working through customer design decisions

The notes in this series comes from working with customers over the past 20 years in the data space, from working with Fortune 500 customers while at Cloudera, to helping build the Deeplearning4j open source library, to writing the Kubeflow Operations Guide, to working with our Fortune 500 customers today at Patterson Consulting. 

A key challenge for platform architects in the data industry is understanding which tools to use and what the tradeoffs are if those tools are used. There are so many vendors pushing their own "all-in-one" platform magic solution that it can be dizzying to cut through the noise.

An advantage that I have in writing a series such as this is that I do not represent a software vendor and so I can play the (mostly) neutral analyst.

Some of the content in this series is based on some of the presentations we've given on the topic over the past 3 years (We also offer consulting to venture capital groups and institutional investor groups).

The most interesting underlying trends I highlight in this series occur not on the quarterly scale, but "tectonic plate" movements across the past decade.

My goal is to condense the vapor of nuance across the past decade of data infrastructure into more solid concepts for building modern data products. Given that most of us are just wandering along the vast data super highways, I felt that the "Hitchhiker's Guide to the Galaxy" was a good analogue for this series.

While there is a lot to consider and ruminate on in trying to understand the data product/infrastructure space, the main thing to remember is, as always: 

Don't Panic.

## The Tectonic Plates of the Data Industry

In 2022 Covid had blown over enough that the conference circuit started up again, and we headed out to a major cloud vendor conference.

One thing that immediately struck me was how similar the conference floor looked to that of O'Reilly Strata back in 2012. If you replaced the cloud platform with Cloudera, the conference would look nearly identical. Even some of the same ETL vendors still existed a decade later (data ETL vendors? check. data load vendors? check. BI vendors trying to disrupt Tableau? check.).

My immediate thought was that "nothing has changed". 

My next thought was "wait a minute, how can that possibly be?"

Some of the folks I saw there had the same reaction that I did. That feeling of "Strata Deja Vu" stuck to me, and on the plane ride home I started writing out notes on the market (which eventually became core themes in this series) to better understand the evolutionary trajectory from 2008 until 2022. 

What bothered me was that "tectonic plates" (e.g., "fundamental things") in the industry had shifted, refactoring the data infratructure space, but I was struggling to put my finger on exactly "what those things were".

In this series I'll take a look at key ideas in the data space:
 
1. The original ideas around the "Lab and the Factory"
2. Key "tectonic plate" shifts of the past decade
3. The evolution of modern data pipelines

Looking back at these ideas directly informs how I craft out guidelines in part 4 of this series for building new data products. The background and context of these topics directly inform the what and why of making the design decisions needed to create new data products. To get there, however, we need to be intentional about the terminology we use and explicit in how these terms are defined.

# Fuzzy Definitions, Marketing Teams, and the Need to Be Specific

In this prologue, though, I want to establish some ground-truth context around terminology --- because in many conversations I've had on this topic (accomplished, educated, experienced) folks make comments such as

* "I'm not really sure what data engineering is" (said by someone 'known' in the ML space)
* "I couldn't tell you where analytics starts and machine learning begins"
* "I'm not sure how long the term 'feature engineering' has been around"

When working on our internal notes on this topic for customers and investors, I wasn't entirely sure a series like this was needed. However, based on the above comments I could tell this topic was worth the writing effort. 

I'll spend some time baselining the discussion with term definitions ("Feature", "Data Modeling", etc) as some folks in both the analytics world and the machine learning world have different definitions for the same concept, and it's worth (attempting to build?) building a common vernacular.

The challenge with this common vernacular is that it seems the combination of "marketing teams jumping on the latest hot term" and "twitter chatter" is a recipe for fuzzy definitions. Definitions and the framing of concepts are where we need to start.

## Revisting the Framing of The Lab and the Factory

Another theme I touch on in this series is revisting the idea of the "Lab and the Factory". I do active research with the University of Michigan on modeling disaster data and its impact on healthcare. I help researchers build out different exploratory data pipelines, and it always was interesting in how, while we were still exploring data product ideas, the tools that best fit the situation were quite different than the tools that fit enterprise data analytics and machine learning projects. Projects such as working with Universtiy researchers is one of the core places that new ideas are born, implicitly embodying the idea of the "lab".

Many ideas, such as "The Lab and the Factory", are used in talks and discussion in a breezy manner, but many times lack specifics. (An example of this is how I use the term "lab and the factory" in our Kubeflow Operations Guide book in chapter 1, but never defining it further in the book. I'm as guity as anyone here.)

Another framing of the data industry was "Data is the new oil". This framing didn't work as well, as not all data was as useful to companies (or they were unable to make use of it).

It's worth grounding any data product analysis in the right framing, to understand what worked --- and what did not work.

# Bridging The Disconnect Between Analytics and Data Engineering

* as defined above, both use different terms to mean the same thing
* look at the DBT notes here on the differences / differences in roles

## Not Everyone Sees It From the Same Viewpoint

* statistics vs machine learning
* analytics vs data engineering

layers are abstracted away over time; in 2010 we thought a lot about distributed parallel processing, network speeds, and disk speeds in context of how we might write a complex data transformation job in MapReduce.

Storage has been progressively abstracted away (snowflake, etc)

some concepts have different labels in different domains

## Where Does ETL End and Analytics Begin?

https://multithreaded.stitchfix.com/blog/2016/03/16/engineers-shouldnt-write-etl/?utm_source=substack&utm_medium=email

https://stkbailey.substack.com/p/nobody-should-write-etl?utm_source=substack&utm_medium=email

## Focus on Value-Creating Tasks

a general idea --- does this work as an evolutionary theme?

## Building Data Products

* many systems have the same data flow, but different consumers at the end of the pipe
* the data processing pipeline tees off different data products for different purposes
   * analytics for BI tools
   * operational data
   * data for machine learning
   * etc

## Modern Data Stack

Notes here:

https://mode.com/collection-build-a-modern-data-stack/

## Games of View Materialization

--- let's see if we can bridge the ideas of analytics and data engineering with the commonality of "view materialization"

In terms of computer science design decisions, it boils down to “Games of Materialized Views” (ref: https://mitpress.mit.edu/books/materialized-views ). 

## Data Engineer (Role)

https://www.freecodecamp.org/news/the-rise-of-the-data-engineer-91be18f1e603

> "I joined Facebook in 2011 as a business intelligence engineer. By the time I left in 2013, I was a data engineer."

> "I wasn’t promoted or assigned to this new role. Instead, Facebook came to realize that the work we were doing transcended classic business intelligence. The role we’d created for ourselves was a new discipline entirely."

## Data Engineering

> "Data engineering refers to the building of systems to enable the collection and usage of data. This data is usually used to enable subsequent analysis and data science; which often involves machine learning.[1][2] Making the data usable usually involves substantial compute and storage, as well as data processing and cleaning."

https://en.wikipedia.org/wiki/Data_engineering

https://www.amazon.com/Fundamentals-Data-Engineering-Robust-Systems/dp/1098108302/ref=pd_bxgy_img_sccl_2/143-2847560-0944436?pd_rd_w=BXhTE&content-id=amzn1.sym.6ab4eb52-6252-4ca2-a1b9-ad120350253c&pf_rd_p=6ab4eb52-6252-4ca2-a1b9-ad120350253c&pf_rd_r=V2C07V6S9W4WZ52VK07T&pd_rd_wg=36QXW&pd_rd_r=b1b67f23-fc07-46ff-ba58-f30f071cd2e6&pd_rd_i=1098108302&psc=1&asin=1098108302&revisionId=&format=4&depth=1

* WTF is "Data Engineering"?
   * the term has shifted over time
   * how we viewed it in the DL Book


# Reference to the Original Hitchhiker's Guide to the Galaxy

Use ChatGPT here to genereate references to data content concepts

> The story is a satire on what happens around the world and what we're doing to our planet and is still relevant today. In the story, Vogons are an alien race destroying planets to make way for construction of a new hyperspace bypass.


* this is great because many times data products are harmless. until they aren't.


Towels:

> A towel is just about the most massively useful thing an interstellar hitchhiker can carry. Partly because it has great practical value. You can wrap it around you for warmth as you bound across the cold moons of Jaglan Beta; you can lie on it on the brilliant marble-sanded beaches of Santraginus V, inhaling the heady sea vapours; you can sleep under it beneath the stars which shine so redly on the desert world of Kakrafoon; use it to sail a miniraft down the slow heavy River Moth; wet it for use in hand-to-hand combat; wrap it around your head to ward off noxious fumes or avoid the gaze of the Ravenous Bugblatter Beast of Traal (a mind-bogglingly stupid animal, it assumes that if you can't see it, it can't see you — daft as a brush, but very very ravenous); you can wave your towel in emergencies as a distress signal, and of course you can dry yourself off with it if it still seems to be clean enough.
> More importantly, a towel has immense psychological value. For some reason, if a strag discovers that a hitchhiker has his towel with him, he will automatically assume that he is also in possession of a toothbrush, washcloth, soap, tin of biscuits, flask, compass, map, ball of string, gnat spray, wet-weather gear, space suit etc., etc. Furthermore, the strag will then happily lend the hitchhiker any of these or a dozen other items that the hitchhiker might accidentally have "lost." What the strag will think is that any man who can hitch the length and breadth of the Galaxy, rough it, slum it, struggle against terrible odds, win through and still knows where his towel is, is clearly a man to be reckoned with.

Restaurant at the End of the Universe

# In Closing


( todo: bring together the purpose of this series )

* lab and the factory: based on who I am, and what my goal is -- what do the tools look like that best suit my needs?
* evolution of data pipelines / tectonic plates: what trends are driving the design of "modern data stacks"?

If we know those two things, then we can entertain ideas around designing new data projects


No matter what you think about the data pipeline/infratructure/product space, my friend JD Long summed it up best when he said:

> "Data Products? Mostly Harmless (Until they Aren't)"



# References

* AI Hierarchy of Needs
   * https://hackernoon.com/the-ai-hierarchy-of-needs-18f111fcc007
* The Rise of the Data Engineer
   * https://www.freecodecamp.org/news/the-rise-of-the-data-engineer-91be18f1e603
* The Lab and the Factory
* Towel as the most important item to carry
   * https://hitchhikers.fandom.com/wiki/Towel

