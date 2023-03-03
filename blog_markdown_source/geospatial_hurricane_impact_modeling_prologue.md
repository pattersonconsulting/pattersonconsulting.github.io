---
layout: post
published-on: February 15th 2023
author: Josh Patterson
title: Prologue - Open Sourcing a Geospatial Analyical Tool
subtitle: Geospatial Hurricane Analytics
description: In this post we'll .....
keywords: snowflake, snowpark, automl, AutoGluon, pandas, dataframe, whl, pip, anaconda, dependency
meta_og_image: pct_autogluon_dep_og_card.jpg
---

# Prologue

> A prologue is an opening to a story that establishes the context and gives background details, often some earlier story that ties into the main one, and other miscellaneous information

Other entries in this series:



* Part 1: Building a Data Pipeline with DBT
* Part 2: Building a Geospatial Hurricane Analytics Tool with Streamlit
* Part 3: Data Engineering with the Snowpark Python API


>	Who is the intended audience for this article?
>
>	Does the Main title market to them?
>
>
>	Who is the secondary audience?





## Core thesis ("Why do I care?"):

* Easy-to-use Building blocks drive higher-level application development
* analytics are the foundation of building next-generation smart city applications
* building next-gen smart city applications is imperative in the race against the Red Queen



## What Tool Are We Releasing?

* An open source set of dbt templates to transform raw census and hurricane data
* A map-generation system based on streamlit and folium to do Geospatial EDA
* A set of jupyter notebooks to perform tabular EDA on the unified dataset


## How Are We Using The Tool?

* This tool has helped us analyze 20 years of Hurricane data
* The insights gleamed from the tool impacted our EDA methods in the Jupyter notebooks
* This has directly impacted our results in building models to predict hospital admissions post-hurricane


## What Else Might it Be Used for?

* Understanding geospatial relationships between weather events and other events in
   * Transit
   * Housing
   * Water
   * Power
   * Air Quality
   * Foot Traffic
* Spatially exploring complex dataset
* Informing the tabular EDA workflow

We include an example where we analyze hurricanes' impact on FEMA inspected damage across 20 years.

# Collaboration with University of Michigan

sue anne bell

AMS invited talk

Started out with a few counties of data
Couldnt find relationships
Then moved to a lot more counties worth of data
Found some of the spikes we were looking for
But realized there was a larger story
Then moved to looking at a 5-7 states worth of data
For admissions
Added per-county storm data in
Found compelling results in the analysis

Talked these results over with another data expert
They pointed out: Storm (N=1)
Difficult to draw any generalizations when N = 1
Now we know we needed to look at 20 years worth of storm data
And as much admission data as we could get our hands on
Our geospatial system needed to be more robust


[ Presented the storyline to AMS in 2022 ]

# Evolution of the Project

Evolution of project

“The Principal Investigator, the data scientist, and the data engineer”
Need to be able to share a hurricane dashboard with folks outside of data science
Non-computer scientists researchers (e.g., Sue Anne)
https://locallyoptimistic.com/post/building-more-effective-data-teams-using-the-jtbd-framework/?utm_source=substack&utm_medium=email
Need to provide the same same of analytical data to
Researchers
Data engineers
Data scientists
Emailing jupyter notebooks is brittle and prone to error
E.g., “not the latest spike calculation code”, etc

Researchers
Want to better understand geo-spatial data with a custom visual tool
Analyst
Want to be able to build out analytics in a fashion consistent with
> “In the spirit of bringing software engineering practices to the SQL-centric ELT data warehousing world, any modern approach would be incomplete without automating the testing and deployment process and integrating with a CI/CD process.”
Data Engineers
Want to provide features to the data scientist that are consistent with what is presented in the BI tool
Data Scientists
Want to build models and not fuss about where the data came from

Talk about the themes from the AMS talk — cross-discipline collaboration
Open sourcing research results — for others to collaborate with!

Maps @ UM Research
Not traditional EDA
But we still need some custom visualization
Possibly could have used ERSI for the geospatial or another traditional GIS tool
But those tend to be locked down
And we started from a data-centric perspective, operating with python, and then later on bringing in GIS components
The open source world has added a lot of functionality that was traditionally in tools such as ERSI

## We started with a need to do traditional EDA

But then realized we needed geospatial visualization combined with our python analysis
To leverage cross-discipline research
Disasters
Computer science
We also needed a way to let multiple people work on the system
Data Analysts – SQL
This started out as a jupyter notebook
And then became a series of notebooks
Soon the data processing pipeline was long and un-weldy
And calculated the metrics for admission data and storm data slightly differently over time
Making comparison of results more difficult too


> JD: JD says he experiments with concepts in a notebook, and then once it gets to a certain point, he hands it off to an analyst

## "Lab to Factory"-Pattern

Concepts do not start as large pipelines
Concepts start in the lab as a jupyter notebook
Not all analysts can do python
But most can do SQL
We want to expand the surface area
More analysts can become engaged
Take data pipeline out of notebook once it gets to a certain size/complexity

## Leverage Open Source As Building Blocks

https://github.com/geanders/hurricaneexposure

CSV Data extracted from GEAnders Hurricane Exposure


# Investment Thesis for the Smart City Space

> The world is facing countless decision problems that often require balancing competing criteria: How to respond to new pandemic diseases while reducing their economic impact? How to react to a changing climate while sustaining economic growth? How to reduce community violence while preserving liberties? How to plan for city growth while considering effects to the environment and social inequality?

The world is changing 
Nations need GDP to compete
How does manufacturing play a role in this?
How does the Red Queen drive productivity?
Climate change is here
How we use our resources is more important than ever
Foundationally, managing cities are key to mitigating climate change


https://twitter.com/Chattanooga_gov/status/1560021936549281794


## Key Challenges Faced by Cities Today


The core challenges faced by the managers and operators of urban centers today are:

* Population Growth
* Traffic
* Operational Costs
* Planning
* Building Codes, Infrastructure, and Compliance

All of these challenges can be measured through data yet many today are not managed effectively. Population growth in urban centers is a key driver towards more managed solutions for other aspects of city management such as traffic.

In the following sub-sections we take a look at published research on each of these challenges.

### Population Growth

Many research papers and studies show a strong trend of population movement into major cities as expressed in the passage below from the University of Michigan:

http://css.umich.edu/factsheets/us-cities-factsheet

> "Approximately 84% of the U.S. population lives in urban areas, up from 64% in 1950. By 2050, 89% of the U.S. population and 68% of the world population is projected to live in urban areas."

Another publication states the following:

https://graylinegroup.com/urbanization-catalyst-overview/

> The United Nations in 2009 and the International Organization for Migration in 2015 both estimated that around 3 million people are moving to cities every week. Approximately 54% of people worldwide now live in cities, up from 30% in 1950. Sources estimate this will grow to 2/3 of world population in the next 15-30 years. More than half of urban dwellers live in the 1,022 cities with greater than 500,000 inhabitants. There are currently 29 megacities with populations of over 10 million, up from 2 in 1950 and projected to grow to between 41 and 53 by 2030. Additionally, there are 468 cities with a population of over 1 million, up from 83 in 1950.

The UN website goes on to state:

> "Today, 55% of the world&rsquo;s population lives in urban areas, a proportion that is expected to increase to 68% by 2050. Projections show that urbanization, the gradual shift in residence of the human population from rural to urban areas, combined with the overall growth of the world&rsquo;s population could add another 2.5 billion people to urban areas by 2050, with close to 90% of this increase taking place in Asia and Africa, according to a new United Nations data set launched today.&ldquo;"


#### Growth Factors of cities

Some of the drivers of the growth of city population size include:
<a href="http://www.yourarticlelibrary.com/essay/factors-influencing-growth-of-cities-around-the-world/24287">http://www.yourarticlelibrary.com/essay/factors-influencing-growth-of-cities-around-the-world/24287</a>

* Surplus Resources
* Industrialization and Commercialization
* Development of Transport and Communication
* Economic Pull of the City
* Educational and Recreational Facilities.


https://twitter.com/DKThomp/status/1507006859818901506







### Traffic

Top listed challenges from the &ldquo;What Challenges Must We Address?&rdquo; report:
<a href="http://www.trca.on.ca/dotAsset/164995.pdf">http://www.trca.on.ca/dotAsset/164995.pdf</a>

>    Two million more people: Provincial plans anticipate that the population of the Greater Toronto Area (GTA) will grow by approximately two million people over the next 20 years.

>    New housing and infrastructure required: This will require the construction of new housing, institutional and commercial supports, transportation systems, and servicing infrastructure.

>    Pace of rapid urbanization: Rapid urbanization will present environmental, social and traffic congestion challenges, which can impose costs on residents and businesses alike.

Another report identifies:
<a href="https://d3n8a8pro7vhmx.cloudfront.net/socialplanningtoronto/pages/574/attachments/original/1487348389/Report-v4-web.pdf?1487348389">https://d3n8a8pro7vhmx.cloudfront.net/socialplanningtoronto/pages/574/attachments/original/1487348389/Report-v4-web.pdf?1487348389</a>

Major concerns around this growth are:&nbsp;

* Gentrification
* Lack of affordable housing
* Transit
* Lack of amenities and greenspace

### Operational Costs

Cities are progressively finding it harder to manage the higher operational burden with the same resources as before:
&ldquo;Recent <a href="https://www.strongtowns.org/journal/2017/1/9/the-real-reason-your-city-has-no-money">research</a> into the tax efficiency (property tax revenues vs. infrastructure maintenance costs) of a variety of American cities and found that walkable urban districts tended to be revenue-positive &ndash; in effect, subsidizing surrounding low-density areas&rdquo;
<a href="https://www.strongtowns.org/journal/2017/1/9/the-real-reason-your-city-has-no-money">https://www.strongtowns.org/journal/2017/1/9/the-real-reason-your-city-has-no-money</a>

#### Fiscal Issues Facing the Operations of Cities

As cities become more complex, costs are outpacing tax revenue:
&ldquo;One evident problem is&nbsp;fiscal: Cities typically have serious difficulties in paying for basic services such as policing, public education, trash removal, street maintenance, and snow removal (at least in cold climates), and in providing certain services for their residents who are poor or disabled or who have other conditions.&nbsp;&ldquo;

### Planning

Planning is compelling to look at from a historical perspective. Appendix A of this report shows a table with the largest cities in history over the past 9,000 years. We can see a trend of cities hitting a progressively larger size plateau over time. In this sub-section on planning we take a look at some of the historical aspects of city infrastructure, building codes, and failures of major cities.

#### Historical Sanitation and Issues with a Growing City

For a many hundreds of years core sanitation practices limited the size of cities as plagues and disease continually restricted the growth of urban centers through killing off large portions of the population, as discussed in the following quote:

<a href="https://blogs.scientificamerican.com/lab-rat/plague-and-the-city/">https://blogs.scientificamerican.com/lab-rat/plague-and-the-city/</a>

> &ldquo;When the Black Death, caused by the bacteria Yersinia pestis, swept across Europe it killed over 1/3 of the population. This level of destruction is almost impossible to imagine today (particularly given that one third of the population of Europe today would be around 250 million people). One of the things that helped the bacteria to thrive was the conditions that the cities encouraged. Yersinia infects fleas, which travel on rats and huge populations of rats could be found in every major city in Europe. Often I suspect, they outnumbered the people. It wasn&apos;t just rats either, cities were crammed with animals including sheep, goats and pigs. Animals and humans in close proximity creates a breeding ground for zoonotic diseases, which can be highly deadly when they switch species.&ldquo;

> &ldquo;Not only are cities a good way to put humans and animals in close contact, they are also notorious for ill-health and bad living conditions compared to nomadic lifestyles. Water has to be brought in and shared around between many people. Overcrowding is common, as are disease vectors such as fleas and bed-bugs that can carry bacteria between humans. With the bad conditions, the close cramped living conditions and the complete lack of understanding of germ theory it&apos;s no wonder the disease swept through Europe until pretty much everyone had either died or survived.&rdquo;

> &ldquo;Before the development of cities bacterial diseases would have been present (cystitis springs to mind...) but the virulent and decimating plague-bearing diseases were unlikely to have arisen, or if they did there was no way for them to spread so far. Hunter gatherer populations did face hardships but on general they ate better and more regularly, got more exercise, and drank water that they were pretty certain was not contaminated. Cities might provide protection, and a solid base for trade and economic infrastructure, but they are also a brilliant way to encourage bacteria to grow and spread disease.&rdquo;

While cities were attracting people with protection and economic infrastructure, but city planning had not yet caught up to operating a city of that size. We can also see a list of the worst pandemics in history:

<a href="https://www.mphonline.org/worst-pandemics-in-history/">https://www.mphonline.org/worst-pandemics-in-history/</a>

And then &ldquo;How The Black Death moved around the world&rdquo;:
<a href="https://www.nytimes.com/2010/11/01/health/01plague.html?_r=0">https://www.nytimes.com/2010/11/01/health/01plague.html?_r=0</a>

excerpt:

> &ldquo;The third great wave of plague began in China&rsquo;s Yunnan province in 1894, emerged in Hong Kong and then spread via shipping routes throughout the world. It reached the United States through a plague ship from Hong Kong that docked at Hawaii, where plague broke out in December 1899, and then San Francisco, whose plague epidemic began in March 1900.&rdquo;
Beyond sanitation issues, there we also issues packing that many buildings closely together without consistent building rules.


History Lesson

Largest Cities over Time -- and what became of the cities
Make reference to
https://twitter.com/culturaltutor/status/1544793776186589184




#### Fires that Changed How City Codes were Written

Many times in history natural urban sprawl set conditions such that entire cities burnt to the ground
<a href="https://en.wikipedia.org/wiki/List_of_town_and_city_fires">https://en.wikipedia.org/wiki/List_of_town_and_city_fires</a>

specifically in the united states in the past 100 years, specific fires have shaped how we write building codes:
<a href="https://www.nfpa.org/~/media/Files/forms%20and%20premiums/101%20handbook/NFP101HB09_CHS1.pdf">https://www.nfpa.org/~/media/Files/forms%20and%20premiums/101%20handbook/NFP101HB09_CHS1.pdf</a>

<a href="https://fireprevention.utexas.edu/firesafety/historic-fires">https://fireprevention.utexas.edu/firesafety/historic-fires</a>

To grow larger, cities had to change how they were built with better building codes and better operations.

#### The Evolution of Building Codes and Compliance to Allow Larger Cities

In response to such issues as:

* Plagues
* Fires
* Earthquakes

Cities began to change how they wrote their building codes and operated their cities. Development of basic potable water handling and sanitation codes helping clean up cities:

<a href="https://wwwnc.cdc.gov/eid/article/24/5/17-1609_article">https://wwwnc.cdc.gov/eid/article/24/5/17-1609_article</a>

A need for public health standards:

<a href="https://www.floridamemory.com/exhibits/medicine/disease/disease5.php">https://www.floridamemory.com/exhibits/medicine/disease/disease5.php</a>

> &ldquo;Within three decades of establishment of the Board of Health, better regulation to ensure sanitary drinking water had begun to reduce instances of diseases such as hookworm, and more effective quarantining and more extensive state-run stations had allowed the state to limit the spread of yellow fever epidemics.&ldquo;

In many cases, changing building codes proved to be a valuable endeavor:

<a href="https://www.eesi.org/papers/view/the-value-and-impact-of-building-codes">https://www.eesi.org/papers/view/the-value-and-impact-of-building-codes</a>

In some cases, &ldquo;some buildings are too expensive to change&rdquo;, but cities were still able to raise the ceiling of maximum operating size with better codes and design. Urban planning and sanitation became key to building the major urban centers we see today.

#### Technology as a Mechanism for Larger Cities: Aqueducts

Lastly, we&rsquo;ll note how infrastructure advancements (such as the Roman aqueducts) notably enabled certain cities to grow to previously unseen sizes:

<a href="https://www.pbs.org/wgbh/nova/article/roman-aqueducts/">https://www.pbs.org/wgbh/nova/article/roman-aqueducts/</a>

> &nbsp;&ldquo;The Romans could not have built cities as big as they did without aqueducts&mdash;and some of their cities wouldn&apos;t have existed at all. Romans sometimes built cities on dry plains. They&apos;d find a spring in the mountains and take that water into the city, which would not have been possible without the transported water. With the water, they could have their baths, their fountains, and their drinking water.

> It also would be impossible to imagine Rome, which had about 1,000,000 people at its peak, without its large aqueducts. The Romans could have obtained their water from the river, wells, and springs, but these sources would have become polluted in a large city.&rdquo;


## Impact of the Industrial Revolution


Impact of the Industrial Revolution

https://lukemuehlhauser.com/industrial-revolution/



### Catastrophes


Impact of Catastrophes



### World Populations


World Population


### Pandemics

Pandemic impacts
https://docs.google.com/spreadsheets/d/14I49e43PphzocDcZghYm6ekQZcJ3JeuicJ9ZafTa7GA/edit#gid=447443392

Covid, more recently



## The Smarter City Races the Red Queen

The Smart City
Cities need to better understand
Transit
Housing
Water
Power
Air Quality
Foot Traffic
Population

Why?
https://www.artemis.bm/news/cat-models-dont-properly-reflect-climate-change-renre-ceo-odonnell/



### How Does This Help Cities?

This empowers better
Codes and compliance
Municipal planning
Operations
To do this, we need to measure and analyze
Traffic
People
Air
Water
Buildings


### Creating New Types of Next-Gen Applications

This creates applications in:
Road tolling
Traffic management
Road safety
Security
Parking management
Freight management
Automotive telematics
Public transport
Environmental protection



### Municipal Use Cases and Models of Utility

The 3 models of utility to consider when framing municipal use cases:

User-Based Insurance
Example: “lowering a city’s insurance costs through monitoring / code compliance”
Applications that save a city money
Example: “Quantify and Prioritize Repairs”
Applications that mitigate a city’s operational risk
Example “Reviewing historical data to understand the cause of adverse events”



### The Municipal Operating System

For cities to meet the demands of growth, they will have to be consumed by software

The City Operating System
Nobody loves city codes
But they power cities of our current epoch
Without standards, we would have to abandon major cities
Continuing the framing, make the case for data and analytics as the operating system of next generation cities
Red queen demands it

Relate to how ML use cases make us “just efficient enough” to meet demand

https://www.artemis.bm/news/cat-models-dont-properly-reflect-climate-change-renre-ceo-odonnell/


Closing
As cities grow, they become more interconnected
Cite flight statistics
A trip across a city now becomes a trip across the country to another city
If we can look at cities as needing management / OS to meet demand
Then by extension we have to consider a network cities as a logical unit in the 21st century
Covid / Pandemics
Climate Change
Pandemics and global coordinated resource management will be the challenge of smart city 2.0



# Promoting Open Research and Applications with Building Blocks


[ relate to SciPy and Anaconda ]


[ what is the core challnege we address with this project? ]


[ Geospatial EDA Tooling as core building blocks --- just as we built on GEAnders work ]


[ tie into the world of analytical data products ]


[ foundational building block in building next-gen smart city applications ]

