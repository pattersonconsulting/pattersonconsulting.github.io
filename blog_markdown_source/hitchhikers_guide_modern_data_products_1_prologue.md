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
* [Revisting The Lab and the Factory](hitchhikers_guide_modern_data_products_2_lab_and_factory_redux.html)
* [The Evolution of Modern Data Pipelines](hitchhikers_guide_modern_data_products_3_evolution_data_pipelines.html)
* [A Methodology for Building Data Products](hitchhikers_guide_modern_data_products_4_methodology_for_data_products.html)

We spend the first 3 posts of this series providing background and definitions to set the stage for our methodology and in part 4 we lay out our step by step process.

The main thing to remember is, as always: Don't Panic.


References

* AI Hierarchy of Needs
   * https://hackernoon.com/the-ai-hierarchy-of-needs-18f111fcc007
* The Rise of the Data Engineer
   * https://www.freecodecamp.org/news/the-rise-of-the-data-engineer-91be18f1e603
* The Lab and the Factory
* Towel as the most important item to carry
   * https://hitchhikers.fandom.com/wiki/Towel

Themes
* Walking around Snowflake conference (Strata Deja Vu)
* Discussions with customers, instituional investors
* twitter/blog discussions about the "modern data stack" / what is in there
   * not gonna tell you "what" to put in there, but put some framing around the "why" and "how" to choose the "what"


Outline / 3 key ideas

1. Key trends of past decade
2. colliding worlds (DW and Data Engineering)
3. Rise of Cloud (Because IT is a pain)

# Fuzzy Definitions, Marketing Teams, and the Need to Be Specific

Reference my interview on AI -- blog post

* make fun of our Kubeflow book using the term "lab and factory" in chapter 1, but never defining it further in the book
* nail down the definition of some terms --- instead of their "breezy twitter usage"
   * the idea of the "lab and the factory caught on" --- but there were few specifics to it (also: "data science")


# Definitions Revisted

Some good definitions on reddit blog:

https://dataengineering.wiki/FAQ/What+is+the+difference+between+a+Data+Engineer+and+X

## A Data Product

## Analytics


## Data Modeling

## Metrics

## The Kimball Data Warehouse Architecture

## Vectors, Features, and Tensors -- Oh, My

https://stats.stackexchange.com/questions/192873/difference-between-feature-feature-set-and-feature-vector

https://stats.stackexchange.com/questions/351514/usage-of-the-term-feature-vector-in-lindsay-i-smiths-pca-tutorial?rq=1

Attributes?

## Feature Engineering

## Machine Learning Modeling

## Machine Learning Model Inference

## Artificial Intelligence

* marketing

# The Disconnect Between Analytics and Data Engineering

* as defined above, both use different terms to mean the same thing
* look at the DBT notes here on the differences / differences in roles

## Games of View Materialization

--- let's see if we can bridge the ideas of analytics and data engineering with the commonality of "view materialization"

## Looking More Critically at Data Engineering


* WTF is "Data Engineering"?
   * the term has shifted over time
   * how we viewed it in the DL Book




# Reference to the Original Hitchhiker's Guide to the Galaxy

Use ChatGPT here to genereate references to data content concepts

> The story is a satire on what happens around the world and what we're doing to our planet and is still relevant today. In the story, Vogons are an alien race destroying planets to make way for construction of a new hyperspace bypass.

JD Long:

> "Data Products: Mostly Harmless"

* this is great because many times data products are harmless. until they aren't.


Towels:

> A towel is just about the most massively useful thing an interstellar hitchhiker can carry. Partly because it has great practical value. You can wrap it around you for warmth as you bound across the cold moons of Jaglan Beta; you can lie on it on the brilliant marble-sanded beaches of Santraginus V, inhaling the heady sea vapours; you can sleep under it beneath the stars which shine so redly on the desert world of Kakrafoon; use it to sail a miniraft down the slow heavy River Moth; wet it for use in hand-to-hand combat; wrap it around your head to ward off noxious fumes or avoid the gaze of the Ravenous Bugblatter Beast of Traal (a mind-bogglingly stupid animal, it assumes that if you can't see it, it can't see you — daft as a brush, but very very ravenous); you can wave your towel in emergencies as a distress signal, and of course you can dry yourself off with it if it still seems to be clean enough.
> More importantly, a towel has immense psychological value. For some reason, if a strag discovers that a hitchhiker has his towel with him, he will automatically assume that he is also in possession of a toothbrush, washcloth, soap, tin of biscuits, flask, compass, map, ball of string, gnat spray, wet-weather gear, space suit etc., etc. Furthermore, the strag will then happily lend the hitchhiker any of these or a dozen other items that the hitchhiker might accidentally have "lost." What the strag will think is that any man who can hitch the length and breadth of the Galaxy, rough it, slum it, struggle against terrible odds, win through and still knows where his towel is, is clearly a man to be reckoned with.

Restaurant at the End of the Universe



## Themes to Discuss
