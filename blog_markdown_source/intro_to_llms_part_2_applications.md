---
layout: post
published-on: March 27th 2023
author: Josh Patterson
title: Building Enterprise Applications with Large Language Models
subtitle: Part 2 - A Guide for Building Enterprise Application with LLMs
description: In this post we'll .....
keywords: snowflake, snowpark, automl, AutoGluon, pandas, dataframe, whl, pip, anaconda, dependency
meta_og_image: pct_autogluon_dep_og_card.jpg
---

# Introduction

Purpose of this series:

> To understand the role of large language models in enteprise applications and some of the components, tools, and technologies relevant to building these applications.

This article, part 2 of the series, is focused on design patterns for enterprise large language model applications. We build on ideas from part 1 around large language models' reasoning capabilities and how we can best use them in enterprise use cases.

The intended audience for this series is:

> Individual practitioners, enterprise data teams, and enterprise executives

Series:

* [An Introduction to Large Language Models (LLMs)](intro_to_llms_part_1_terminology.html)
* [A Guide for Building Enterprise Application with LLMs](intro_to_llms_part_2_applications.html)
* [Putting LLM Applications into Production](intro_to_llms_part_3_model_management.html)
* [Appendix A: What is Artificial Intelligence?](dl_book_appendix_a_ai.html)

The final post is where I give context on the arena of artificial intelligence based on the history of the field. This context and history gives the reader a better viewpoint on recent developments in large language models.

# Understanding Use Cases for LLMs

In part 1 of this series I talked about focusing on reasoning as the key ability of large language modeling and how to measure the reasoning capability of a model. For this series we are most focused on applications where we can leverage LLM-assisted reasoning to complete tasks. I call this style of application an "Augmented Reasoning" system.

We don't want to focus on use cases that involve specific knowledge retrieval is the core task --- because systems such as databases and search engines are already well-suited for those class of tasks. "Augmented Reasoning" should be where you spend your mental cycles with respect to enterprise use cases for near term large language model applications.

Let's get into a mental model on how to profile use cases appropriate for large language models in the enterprise.

## Profiling Use Cases

In any organization we want to identify use cases that:

* are labor-intensive tasks 
* require significant amounts of manual effort, analysis, and communication. 

These are attractive tasks candidates for large language model applications because we can operate more efficiently as a business unit if these tasks are done more quickly or with less resources. Improving these tasks doesn't mean we're trying to reduce headcount, it means we're trying to do more with the same amount of resources (e.g., "banks being open more days with computers").

The insurance industry is a great example of an industry that has many labor intensive tasks, with a few examples being:

* Claims processing
* Underwriting
* Customer service
* Compliance

If we use the mindset that natural language is the universal domain specific language, then we can expand and empower the group of potential employees who can efficiently perform these tasks. This is similar to how systems that use SQL as the base interface in enterprise software tend to have more adoption than platforms that require higher-level programming skills.

This allows us to frame large language model applications ***using natural language as the next generation scripting language***. 

From this perspective, most companies are full of labor-intensive, analysis-intensive, and heavy-communication tasks that are candidates for large language model applications.

### Mapping Types of Reasoning to Use Cases

Thinking about reasoning is not a common mental model for many of us, so check out Google's article on [Types of reasoning in LLMs](https://ai.googleblog.com/2022/05/language-models-perform-reasoning-via.html) to get a refresher on reasoning that large language models are good at.

Certain classes of LLM models are capable of Chain of Thought reasoning. Through chain of thought reasoning, models can break down intricate problems into separate intermediate steps that can be solved individually. Some of these problems that Chain of Thought enables include:

* Arithmetic reasoning
* Problem solving
* Commonsense reasoning

LLMs also demonstrate the ability to write code in languages such as SQL and Python (if they've been trained for that task).

However, breaking up a task into multiple smaller tasks is a key way to enable large langauge model applications to better accomplish a complex task. If we do some work on the front end to identify certain types of tasks, we can use a pre-pass on the task to break it down into sub-tasks and then let a large language model chain the output of one task as the input to a later task.

An example of this would be how we might convert natural language to SQL in the first task, and then execute the SQL, sending the results back to the LLM for interpretation and then explanation back in natural language, as described in this [article on task composability](https://huyenchip.com/2023/04/11/llm-engineering.html#part_2_task_composability):

* Task 1: convert natural language input from user to SQL query [LLM]
* Task 2: execute SQL query in the SQL database [SQL executor]
* Task 3: convert the SQL result into a natural language response to show user [LLM]

Now that we've mapped out some ideas in reasoning we can use in our use cases, let's look at a few emerging enterprise use cases.

## Examples of Use Cases

The major enterprise use cases being discussed at this point are:

- question-answering: query a corpus of text in natural language
- chat: same, but interactive
- extraction / summarization: what are the top N issues in these 10,000 reviews? 
- (semi-)structured natural language querying: answer from SQL query results

A great example of a question answer system is what Jeremy Lewi came up with for the Kubeflow project. Jeremy designed a large language model application called "Tribal Knowledge" that allowed any user to dynamically ask questions about what was discussed in a Kubeflow project call. While there are folks who take notes during open source project meetings, many times a lot of the discussion or context is lost. This system allows a user to go back and query the discussion nearly like they were on the call.

How he did it: Jeremy designed the system to transcribe the project management calls into text, and then fed those text transcriptions into a vector database. From there, he used a language model framework (LangChain) to take a natural language query, look in the vector database for contextual results, and then send the query text with the context text from the vector database to openAI's API to generate an answer to the natural langauge question.

Another great example is how Microsoft is taking large language models and integrating them through MS Office to allow for acceleration of document creation:

<iframe width="560" height="315" src="https://www.youtube.com/embed/S7xTBa93TX8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

### Generalized LLM Sub-Tasks

We can start to see some specific patterns, and outline some generalized use case types you can plug your industries use cases into:

* Task: “Understanding a Corpus”
   * Ask a Question of a corpus
   * Question / Answer
   * Needs - Low cost of false positives
* Task: “Query your tabular dataset”
   * SQL
   * Dataframes / CSVs
* Task: “Automate Knowledge Work”
   * create a spreadsheet
   * create a database
   * create a presentation
   * write an email
* Task: “Query the information in a phone conversation”
   * ask questions about what happened in a meeting

Additonally, we can perform tasks  with LLMs that have the following needs:

* mimicking a human through text
* basic reasoning
* breaking down a goal into specific steps or tasks
* text or code generation

### Examples of Poor Use Cases for LLMs

With any technology, without fail, folks take things too far and we see crazy requests. This is just part of the overall hype cycle naturally of any new technology in the orbit of artificial intelligence. Examples of these requests are things like:

* automate all financial advice (read: non-trivial legal issues here)
* migrate my whole legacy data warehouse
* automate all nurse practitioners 

Any time your use case runs into affecting the health or financial condition of people with little to no oversight, its probably a bad idea to try and use large language models for that use case at this point.




## A Design Process for Selecting LLM Use Cases

A quick and easy way to think about it is to evaluate each potential use case like this:

1. will it harm folks if it generates poor reasoning?
   * if yes, then not a good use case
2. Can I break the task down into a workflow of tasks?
   * if yes, do any of the sub-tasks work well as the generalized LLM sub-tasks above overlap?
3. Does this workflow accelerate a labor intensive workflow in your busienss unit?
   * if yes, then this is likely a relevant use case

Use the above 3 filter criteria as a "low pass filter" on new LLM use case ideas to help triage things quickly. 

Low-hanging fruit use case that pass the above filters are things such as:

* document generation with database integration
* significant data entry
* insurance policy Q/A in customer service
* email generation that requires knowledge integration and basic reasoning
* anything that requires a lot of data lookup with basic reasoning applied

Now that we have outlined some ways to triage use cases, let's look at some frameworks and components we can use to build large language model applications.

# Application Frameworks and Components

In this section I'm going to review some of the key frameworks and components you need to be aware of as basic building blocks for large language model applications.

A few we'll cover here:

* LangChain
* Embeddings
* Vector Databases
* Model Integration (Topic)



## LangChain

what is langchain?

LangChain is a comprehensive framework developed for building language model-powered applications. 

The github repo for Langchain began in October ‘22.

LangChain applications are built around 2 key characteristics:

1. Data Awareness: These applications establish connections between language models and other data sources, allowing for a broader understanding and utilization of diverse information.

2. Agentic Capability: Applications built on LangChain enable language models to actively interact with their environment, enhancing their ability to engage and respond in dynamic contexts.

Further, the LangChain framework offers two primary value propositions:

1. Components: LangChain provides modular abstractions for various components essential for working with language models. It includes a comprehensive collection of implementations for these abstractions. These components are designed to be easily utilized, whether you opt to utilize the entire LangChain framework or not.

2. Use-Case Specific Chains: Chains can be seen as arrangements of these components tailored to address specific use cases effectively. They serve as a higher-level interface that simplifies the process of getting started with a particular use case. These chains are also designed to be customizable, allowing users to adapt and tailor them to their specific requirements.

By offering both flexible components and purpose-built chains, LangChain empowers developers to create sophisticated language model applications that leverage data awareness and agentic capabilities, fostering innovation and customization.

...

The utilization of natural language for interacting with Python function return values presents an intriguing prospect. The advantage lies in avoiding the need for tightly coupled APIs. However, it is important to acknowledge that this approach also comes with certain drawbacks. One such drawback is that the language model (LLM) may initially rely on a trial-and-error process when engaging with the associated tools.

```
The hierarchy of LangChain Modules are loosely:
1. Agents utilize components of LLMs and Tools and
2. Chains utilize PromptTemplates and LLMs where
3. LLMs provide the text generations given an input
```

### What is LangChain?

Use Cases
Personal Assistants (Agents)
Autonomous Agents
Agent Simulations
Question Answering over Docs
Chatbots
Querying Tabular Data
Code Understanding
Interacting with APIs
Summarization
Extraction
Evaluation

Models supported:

AI21
Aleph Alpha
Azure OpenAI
Banana
CerebriumAI
Cohere
DeepInfra
ForefrontAI
GooseAI
GPT4All
Hugging Face Hub
Hugging Face Local Pipelines
Llama-cpp
Manifest
Modal
NLP Cloud
OpenAI
Petals
PredictionGuard
PromptLayer OpenAI
Replicate
Runhouse
SageMakerEndpoint
StochasticAI
Writer


LangChain Modules: 

### Prompts and Prompt Templates

By utilizing the Prompt Template module, you have the ability to establish the structure and arrangement of your prompts. This module serves the purpose of defining input data, context, and output indicators. Incorporating Prompt Templates can significantly contribute to maintaining consistency and enhancing the efficiency of prompt generation.

### LLMs 

The Large Language Model (LLM) module provides a standard interface for state-of-the-art language models for generating high-quality output. LangChain supports a wide range of tasks, including text summarization, mathematical reasoning, and code generation. The module includes pre-trained LLMs that can be fine-tuned to match the needs of specific conversational agents.

### Document Loaders

With the assistance of document loaders, generating documents from diverse sources becomes a seamless process. These documents can subsequently be loaded onto vector stores for convenient sourcing. The document loaders module offers two methods: "load" and "loadAndSplit." The "load" method retrieves the documents from the specified source and returns them as an array of documents. On the other hand, the "loadAndSplit" method loads the documents from the source, utilizes the provided TextSplitter to split them, and then returns them as an array of documents. These methods provide flexibility and efficiency in managing and manipulating document data within the system.
[ summarize ]
The Document Loaders module enables the ingestion of documents, such as PDFs or PowerPoints, into the LLM for subsequent analysis. Integrating language models with your custom text data presents an effective means of distinguishing their capabilities. The initial stage involves loading the data into "documents," which essentially refers to individual segments of text. This process establishes a foundation for leveraging the power of language models to extract valuable insights and enhance text processing tasks.

### Chains

The Chain module offers the capability to connect multiple LLMs, enabling the creation of intricate and advanced prompts and applications. This module proves valuable for tasks that involve multiple steps or stages. For instance, a chain can be established to take user input, apply formatting using a PromptTemplate, and subsequently pass the formatted response to an LLM. By combining multiple chains or integrating chains with other components like Utils, more complex chains can be constructed. This empowers the development of sophisticated workflows that leverage the strengths of various components to accomplish diverse objectives.

### Agents 

An Agent module facilitates the expansion of output generation by deploying prompts, enabling scalable operations. It leverages an LLM to determine the appropriate actions to undertake, whether it involves utilizing a tool and observing its output or providing a response back to the user. Tools, on the other hand, are functions designed to fulfill specific responsibilities, such as conducting a Google Search or performing a Database lookup. The Agent module relies on LLMs, which serve as the language models driving its functionality. Together, these components contribute to the efficient operation of the agent, empowering it to deliver enhanced performance and functionality in various contexts.

### Memory

The Memory component empowers agents to retain information from previous interactions with users, as well as remember important entities. This capability enables agents to offer users more personalized and contextually relevant responses over time. By leveraging stored memories, agents can enhance their understanding of user preferences and past conversations, facilitating a more tailored and engaging user experience. The Memory component plays a crucial role in enabling agents to evolve and adapt their responses based on accumulated knowledge, leading to more effective and satisfying interactions.

### Tools


### Other Similar Frameworks

While there are other frameworks beside LangChain such as Llama Index (a "data framework"), for the purposes of focus I'm only going to cover LangChain here.


### Some Thoughts on LangChain's Rapid Growth


* adoption of langchain has been rapid
* list attributes of langchain
   * open source 
   * simple quick install via pip or anaconda
   * no server dependencies, docker images, or extra infra required
   * great documentation and easy to replicate examples
   * lots of out of the box plugins (sql, pandas, more)


https://github.com/kyrolabs/awesome-langchain

https://www.pinecone.io/learn/langchain-intro/

https://www.pinecone.io/learn/langchain-agents/


https://blog.langchain.dev/announcing-our-10m-seed-round-led-by-benchmark/




## Embeddings


Embeddings<sup>Emb1</sup> are a fundamental concept in machine learning models, including Large Language Models (LLMs). They are numerical representations of data, such as text, images, or audio, that capture the essence or semantic meaning of the data. The process of embedding involves converting the input data into vectors of numbers, allowing the machine learning model to understand and process the data effectively. 

For example, in the context of text data embeddings represent the semantic relationships between words, sentences, or documents. Each word or document is assigned a vector in a high-dimensional space, where the position of the vector records information about the meaning of the text based on various traits or criteria (as represented by the dimensions of the vector space). By mapping words or documents into a continuous vector space, embeddings allow for similarity comparisons (through the use of algorithms like nearest neighbors) and the clustering of textual data. For instance, in the video embedded below you cna see a detailed explanation about how text embeddings work.

<iframe width="560" height="315" src="https://www.youtube.com/embed/ISPId9Lhc1g" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>


There are different types of embeddings depending on the use case and training techniques used. A few popular examples of these include:

1. Text Embeddings: These are embeddings that numerically capture the meaning of data in the form of text. There are three common forms of text embedding: word, sentence/paragraph, and document embeddings. 
   * Word Embeddings: These embeddings record the semantic meaning of each individual word of a text. This allows for operations on the text using words, such as measuring the similarity of words, finding word analogies, and finding similar words. Some popular algorithms for word embedding include GloVe, fastText, and [Word2Vec](https://jalammar.github.io/illustrated-word2vec/).
   * Sentence/Paragraph Embeddings: These embeddings describe the meaning of entire sentences or paragraphs of a text. This is done by finding the context and relationships between words to capture the meaning of the sentence or paragraph in its entirety. Some examples of models that create sentence/paragraph embeddings include OpenAI embeddings, Cohere embeddings, and Sentence Transformers.
   * Document Embeddings: Document embeddings are functionally very similar to sentence/paragraph embeddings but capture the meaning of entire documents or texts. These embeddings are particularly useful for tasks that involve clustering, document classification, and information retrieval.
2. Audio Embeddings: These are embeddings that numerically capture the meaning of data in the form of audio. This allows for operations on audio files such as similarity comparisons and isolation(?). An example of an algorithm for audio embedding is OpenL3.
3. Image Embeddings: These are embeddings that numerically capture the meaning of data in the form of images. This allows for operations on images such as classification, similarity comparisons, clustering, and identification. Some popular models for image embedding include VGG-16, ResNet50, and Inceptionv3

Embeddings are used in many machine learning applications, and LangChain is no exception. LangChain has an embedding class built in that functions as an interface for text embedding models like Cohere, HuggingFace, and OpenAI. LangChain only supports text embedding. This basic embedding class has two methods, with one functioning within one document while the other functions across multiple documents. 

Once an embedding is done and the vector is created, where does this information go? This is where embedding databases, also known as vector databases, are utilized. Vector databases play a crucial role in leveraging embeddings for efficient retrieval. These databases store the embeddings generated for various data points, such as documents, images, or audio segments, in the form of vectors. Rather than traditional database searches based on substrings or exact matches, vector databases allow searching based on the nearest neighbors in the vector space. By calculating the similarity between the embeddings of the query and the stored embeddings, vector databases can retrieve the most relevant data points in a more significant way than a substring or exact match search can.

## Vector Databases

Repeatedly generating all embeddings for a corpus would not be efficient, and that's where vector databases come into play. Vector databases play a crucial role in machine learning (ML) and large language model (LLM) applications. They are designed to efficiently store, index, and retrieve high-dimensional vectors, which are numerical representations of data points. These vectors can represent various entities such as words, documents, images, or user preferences. Vector databases work hand in hand with the embedding models that create such high-dimensional vectors.

The importance of vector databases lies in the many utilities and operations it allows embeddings to perform once the semantic meaning of data is vectorized. Of these, there are three that are particularly significant:

1. Efficient Similarity Search: Vector databases excel at performing efficient similarity searches. ML algorithms often rely on measuring the similarity between vectors to make accurate predictions or recommendations. By using specialized indexing structures like KD-trees or Annoy, vector databases can quickly find the most similar vectors to a given query, enabling fast retrieval of relevant information.
2. Nearest Neighbor Search: Vector databases enable efficient nearest neighbor search operations. Given a query vector, ML algorithms often need to find the closest vectors in the dataset. This operation is essential in recommendation systems, clustering, anomaly detection, and other ML tasks. Vector databases can perform nearest-neighbor searches efficiently, allowing ML models to find relevant data points in multi-dimensional spaces.
3. Embedding Storage: LLMs often rely on pre-trained embeddings, where words or sentences are mapped to high-dimensional vectors. Vector databases provide a convenient and efficient way to store and retrieve these embeddings. By using vector databases, LLMs can quickly access pre-trained embeddings for various language-related tasks, such as text generation, language translation, or sentiment analysis instead of calling embedding models every time there is a query.

### Vector Databases vs Traditional Databases

Vector databases are undoubtedly important when used in conjunction with embedding models, but how exactly do they compare with traditional databases? While they are both databases, vector databases differ greatly from traditional databases when it comes to the format and structure of the database and how querying functions within the database:
   
Traditional databases are typically designed to store structured data in tabular formats, such as rows and columns. They are optimized for transactional operations and data consistency. In contrast, vector databases focus on storing and querying high-dimensional vectors, which are often unstructured or semi-structured data representations. They prioritize efficient similarity searches and nearest-neighbor operations rather than traditional relational operations.

Traditional databases use indexing techniques like B-trees or hash indexes to accelerate query performance based on certain attribute values. These indexing methods are not well-suited for high-dimensional vector searches. Instead, vector databases employ specialized indexing structures like KD trees, ball trees, or locality-sensitive hashing (LSH) to efficiently index and search high-dimensional vectors.

### Vector Databases vs Graph Databases

Vector databases contain data formatted as high-dimensional vectors within a larger, interconnected vector space. We can also compare vector databases and graph databases for a different take:

Graph databases are designed to represent and store relationships between entities in the form of nodes and edges. They focus on capturing complex relationships and querying graph-based patterns efficiently. On the other hand, vector databases primarily focus on storing and querying high-dimensional vectors, with a lower emphasis on explicitly modeling and querying relationships between entities.

Graph databases offer powerful graph query languages (e.g., Cypher for Neo4j) that allow expressive queries to traverse and explore relationships in the graph. These queries emphasize graph traversal and pattern matching. In contrast, vector databases prioritize similarity search and nearest neighbor operations, which involve measuring vector distances rather than explicitly traversing graphical structures.

Graph databases excel in use cases where the relationships between entities are critical, such as social networks, recommendation systems, fraud detection, or knowledge graphs. Vector databases, on the other hand, are particularly beneficial in ML/LLM applications where high-dimensional vector representations and similarity-based operations are essential, such as content-based recommendation systems, text search, or image retrieval.

### Open Source and Commercial Vector Databases

Open soure vector databases include:

* [ChromaDB](https://github.com/chroma-core/chroma)
* [Milvus](https://milvus.io/)
* [Vespa](https://github.com/vespa-engine/vespa)
* [Weaviate](https://weaviate.io/)
* [Vald](https://github.com/vdaas/vald)
* [Qdrant](https://github.com/qdrant/qdrant)

Most of the above open source vector databases have some sort of managed service that you can upgrade to in order to get support, enterprise features, etc.

Commercial vector database (services) include:

* [Pinecone](https://www.pinecone.io/)
* [Vectera](https://vectara.com/)

Although popular open-source vector search libraries such as NMSLIB or Faiss yield favorable outcomes in nearest neighbor benchmarks, they present challenges when it comes to implementing them in a production environment. These libraries solely provide the necessary functionality, but do not constitute complete vector similarity search systems. Consequently, users would need to construct a distributed system to scale and incorporate these libraries effectively. Additionally, it can be non-trivial to manage the indexes of these distributed systems.

## LLM Models and Model Integration

* [ todo: source ]

### Issues in Integrating LLMs into Applications
https://www.datacamp.com/tutorial/introduction-to-lanchain-for-data-engineering-and-data-applications


# Design Patterns for Building Large Language Model Applications


The key is to select a model that has "good enough reasoning ability for the intended task at hand" --- e.g., you wouldn't hire a phd meteorologist to get you coffee from starbucks. It would just be a waste of the cost of their education.

https://weightwatcher.ai/leaderboard.html


## General Architecture of LLM Applications

* diagram here


### Options for Building LLM Applications

LangChain
Open Source Python Library
Can Use multiple Models (OpenAI, or Local)
Google Generative AI Studio
closed source
Built into GCP
Prompt Engineering Workbench
Tons of emerging libraries, really…


### Model Variations in LLMs

Models

1. Use a Pre-Trained LLM
2. In-Context Learning with Pre-Trained LLM - Fine-Tune an Existing LLM
3. Use Ray/DGX to Finetune models

### Building a Question / Answer System with LangChain

* discuss, link notebook


Required Tooling
LangChain
VectorStore
Custom Corpus
Something to ask questions about
LLM
OpenAI
Other local model

https://colab.research.google.com/drive/1Rl3eh_rrN7sco4bkzApVqOzu1CtjoWPb




### Task Composability

Consider the “talk-to-your-data” use case where we want to connect to a database and query this database in natural language. Imagine a credit card transaction table. You want to ask things like: 
"How many unique merchants are there in Phoenix and what are their names?" 
and your database will return: 
"There are 9 unique merchants in Phoenix and they are …".

One way to do this is to write a program that performs the following sequence of tasks:
Task 1: convert natural language input from user to SQL query [LLM]
Task 2: execute SQL query in the SQL database [SQL executor]
Task 3: convert the SQL result into a natural language response to show user [LLM]

### Querying Pandas Dataframes with Natural Language Example: Sketch

Sketch is an AI code-writing assistant for pandas users that understands the context of your data, greatly improving the relevance of suggestions. Sketch is usable in seconds and doesn't require adding a plugin to your IDE.

Data Catalogging:
General tagging (eg. PII identification)
Metadata generation (names and descriptions)
Data Engineering:
Data cleaning and masking (compliance)
Derived feature creation and extraction
Data Analysis:
Data questions
Data visualization

## LLMs, Agents, and Tools

Re-write:
```
Why do LLMs need to use Tools?
One of the most common challenges with LLMs is overcoming the lack of recency and specificity in their training data - answers can be out of date, and they are prone to hallucinations given the huge variety in their knowledge base. Tools are a great method of allowing an LLM to answer within a controlled context that draws on your existing knowledge bases and internal APIs - instead of trying to prompt engineer the LLM all the way to your intended answer, you allow it access to tools that it calls on dynamically for info, parses, and serves to customer.
Providing LLMs access to tools can enable them to answer questions with context directly from search engines, APIs or your own databases. Instead of answering directly, an LLM with access to tools can perform intermediate steps to gather relevant information. 
```

GPT-Plugins ---- link page


## LLMs, Data Modeling, and the Rise of the Semantic Layer


***Play up Cube's semantic layer here --- key to giving LLMs the context they need to understand your data model***


Natural Language Dataset Query with LLMs

Querying Tabular Stores with NL:
https://python.langchain.com/en/latest/use_cases/tabular.html
Using Chains to Query APIs
https://python.langchain.com/en/latest/use_cases/apis.html
Using NL to Query SQL Databases
https://python.langchain.com/en/latest/modules/chains/examples/sqlite.html
https://github.com/hodgesmr/LangChain-Data-Demo


# Summary

https://cube.dev/blog/conversational-interface-for-semantic-layer

https://github.com/approximatelabs/sketch


diagram here

# Footnotes

[Emb1] For a deeper dive on embeddings, check out [Vicki Boykis' article](https://vickiboykis.com/what_are_embeddings/)

