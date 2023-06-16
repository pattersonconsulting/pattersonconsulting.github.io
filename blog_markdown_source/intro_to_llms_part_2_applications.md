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

> To understand what LLMs are

The intended audience for this series is:

> Individual researchers, data scientists, and then also enterprise data teams as well

Series:

* [Background and Core Concepts in LLMs](intro_to_llms_part_1_terminology.html)
* [A Guide for Building Enterprise Application with LLMs](intro_to_llms_part_2_applications.html)
* [Putting LLM Applications into Production](intro_to_llms_part_3_model_management.html)
* [Appendix A: What is Artificial Intelligence?](dl_book_appendix_a_ai.html)

# Profiling Use Cases for LLMs

We are most focused on applications where we can leverage LLM-assisted reasoning to complete tasks

For different industries, these tasks will be different.

We dont want to focus on use cases that involve specific knowledge retrieval is the core task --- because systems such as databases and search engines are already well-suited for those class of tasks.

"Assisted Reasoning" should be where you spend your mental cycles with respect to enterprose use cases.




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

Abilities of a LLM that can be leveraged in an application

* mimicking a human through text
* basic reasoning
* breaking down a goal into specific steps or tasks
* text or code generation


## Natural Language as a DSL for Anything with an API

* So basically I think it can automate the creation of workflows that need humans in the middle
* Ala “write me some code to do” but for anything — as long as you write a plug-in/bindings for the task
* And you can use basically any llm to power the question analysis
* Doesn’t replace people
* But just like that office 365 video — a person does a shit load more stuff, faster
* It’s a next generation scripting language, but in the case you don’t have to learn some domain specific language, you just use “your own natural language “ 

## Examples of Use Cases

Kubeflow / Tribal Knowledge
* Benefit: allows us to query what happened in the audio meeting

Office 365 CoPilot

* https://www.youtube.com/watch?v=S7xTBa93TX8&t=2s
* Office work / Knowledge work


## Task Composability

https://huyenchip.com/2023/04/11/llm-engineering.html

One way to do this is to write a program that performs the following sequence of tasks:
* Task 1: convert natural language input from user to SQL query [LLM]
* Task 2: execute SQL query in the SQL database [SQL executor]
* Task 3: convert the SQL result into a natural language response to show user [LLM]


## Raw Source Notes

`
What are common LLM use cases? If I had to roughly categorize the use cases I'm hearing people ask about in the enterprise, in 2023, after the rise of ChatGPT, it's something like:

- 40% question-answering: query a corpus of text in natural language
- 10% chat: same, but interactive
- 20% extraction / summarization: what are the top N issues in these 10,000 reviews? 
- 20% (semi-)structured natural language querying: answer from SQL query results
- 10% other sci-fi use cases: write my business strategy

Of course, there are a number of use cases too that I'd describe as simply not LLM problems. I've heard forecasting a few times. Even regression! Why?

Some are too sci-fi, like, migrate my whole legacy data warehouse. I think that's interesting. You show people a bit of magic, and it's not at all clear how deep the magic goes. LLMs are a little magic, not the Starship Enterprise. Language models, not actually sentient. But you'd be forgiven for assuming otherwise.

Conspicuously missing from the conversations I've seen are:

- Translation, classification: these are real use cases, just, those that want to do this have already been doing this
- Content generation: write a response to this customer. I suppose individuals are doing this with ChatGPT?
- Code generation: already well in hand with Copilot et al

It's not surprising that natural-language querying over, well, natural language is a leading use case. It's a natural fit for LLMs, and is quite easy already. I think these will rapidly get implemented and productized. More targeted extractive queries are a little harder at the margins but seem well within the capability of LLMs.

The interesting frontier for the rest of the year is IMHO SQL generation. Everybody has a database, it's an obvious use case, and it's at least not-infeasible now. It's just hard to do well enough, reliably enough to consider turning loose at scale, I think. It works OK now if you assume this is fundamentally a code assistant for SQL analysts, something to create a first draft that they'll correct. It does not work if you assume the audience are users who would not know the correct answer, let alone SQL, when they saw it.

This is a problem that will probably get solved well enough in the next year, such that there are services and OSS models that are close enough, to make this a next big focus.

That's an interesting topic for another day!
`

## Issues in Integrating LLMs into Applications
https://www.datacamp.com/tutorial/introduction-to-lanchain-for-data-engineering-and-data-applications



Overall, labor-intensive tasks in an insurance company tend to be those that 

require significant amounts of manual effort, analysis, and communication. 

As such, many companies are investing in automation and other technologies to streamline these processes and reduce the workload on human staff.

The insurance industry is a great example of an industry that has many labor intensive tasks.

Here are a few examples:

* Claims processing
* Underwriting
* Customer service
* Compliance


## Example: Claims Processing

* todo: link QA demo notebook

This involves 
verifying the accuracy of submitted claims, 
reviewing policy coverage and terms, (QA)
and determining the appropriate payout amount.  (QA)
Claims processing often requires 
a significant amount of manual data entry, (Data Entry)
analysis, 
and communication with (Document Generation)
policyholders, 
medical professionals, 
and other stakeholders.


QA
Question answer
Data Entry
“enter the data from this person’s file into this template”
Document Generation
Similar to office 365 demo video
examples
“write a letter to the policyholder about their claim that approves/denies the claim”
“create a CSV file with the medical history of the patient to send to the medical professional”



# Application Frameworks and Components

asdasd

## LangChain

https://blog.langchain.dev/structured-tools/

https://github.com/kyrolabs/awesome-langchain

https://www.pinecone.io/learn/langchain-intro/

https://www.pinecone.io/learn/langchain-agents/


https://blog.langchain.dev/announcing-our-10m-seed-round-led-by-benchmark/


https://medium.com/@gk_/chatgpt-and-langchain-an-attempt-at-scheduling-automation-part-3-of-3-db65906ab581
```
Langchain is on a productive and crucially important path, but things are still quite raw. This is to be expected. The github repo for Langchain began in October ‘22.

New models will inevitably interact with these chains and their ‘agents’ in new ways such that the chain infrastructure will need to evolve with the models over time.

The use of natural language to interact with Python function return values is intriguing. The benefit of this is not having to tightly couple APIs, the downside is the llm is in a trial-and-error mode with the tools.

It seems clear that agent instructions (the prompts) need to be specialized to the type of automation needed. This is natural, if we hired a human to perform the task of scheduling they would need instructions.
Overall…
A fusion of functional code and LLMs is inevitable. Both must work together to create automation pathways.

The use of natural language in managing programmatic functions (‘tools’) seems promising however once the llm has found the correct calling format it should remember it rather than repeating the trial&error each time.

A chat model is fine so long as it considers at least 3-parties in the conversation: a) the customer/user, b) the chatbot, and c) the business representative
```

* adoption of langchain has been rapid
* list attributes of langchain
   * open source 
   * simple quick install via pip or anaconda
   * no server dependencies, docker images, or extra infra required
   * great documentation and easy to replicate examples
   * lots of out of the box plugins (sql, pandas, more)

## Embeddings

https://vickiboykis.com/what_are_embeddings/

https://jalammar.github.io/illustrated-word2vec/


Embeddings are a fundamental concept in machine learning models, including Large Language Models (LLMs). They are numerical representations of data, such as text, images, or audio, that capture the essence or semantic meaning of the data. The process of embedding involves converting the input data into vectors of numbers, allowing the machine learning model to understand and process the data effectively.

<iframe width="560" height="315" src="https://www.youtube.com/embed/ISPId9Lhc1g" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For example, in the context of text data embeddings represent the semantic relationships between words, sentences, or documents. Each word or document is assigned a vector in a high-dimensional space, where the position of the vector records information about the meaning of the text based on various traits or criteria (as represented by the dimensions of the vector space). By mapping words or documents into a continuous vector space, embeddings allow for similarity comparisons (through the use of algorithms like nearest neighbors) and the clustering of textual data.

There are different types of embeddings depending on the use case and training techniques used. A few popular examples of these include:

1. Text Embeddings: These are embeddings that numerically capture the meaning of data in the form of text. There are three common forms of text embedding: word, sentence/paragraph, and document embeddings. 
   * Word Embeddings: These embeddings record the semantic meaning of each individual word of a text. This allows for operations on the text using words, such as measuring the similarity of words, finding word analogies, and finding similar words. Some popular algorithms for word embedding include GloVe, fastText, and Word2Vec.
   * Sentence/Paragraph Embeddings: These embeddings describe the meaning of entire sentences or paragraphs of a text. This is done by finding the context and relationships between words to capture the meaning of the sentence or paragraph in its entirety. Some examples of models that create sentence/paragraph embeddings include OpenAI embeddings, Cohere embeddings, and Sentence Transformers.
   * Document Embeddings: Document embeddings are functionally very similar to sentence/paragraph embeddings but capture the meaning of entire documents or texts. These embeddings are particularly useful for tasks that involve clustering, document classification, and information retrieval.
2. Audio Embeddings: These are embeddings that numerically capture the meaning of data in the form of audio. This allows for operations on audio files such as similarity comparisons and isolation(?). An example of an algorithm for audio embedding is OpenL3.
3. Image Embeddings: These are embeddings that numerically capture the meaning of data in the form of images. This allows for operations on images such as classification, similarity comparisons, clustering, and identification. Some popular models for image embedding include VGG-16, ResNet50, and Inceptionv3

Embeddings are used in many ML applications, and LangChain is no exception. LangChain has an embedding class built in that functions as an interface for text embedding models like Cohere, HuggingFace, and OpenAI. LangChain only supports text embedding. This basic embedding class has two methods, with one functioning within one document while the other functions across multiple documents. 

Once an embedding is done and the vector is created, where does this information go? This is where embedding databases, also known as vector databases, are utilized. Vector databases play a crucial role in leveraging embeddings for efficient retrieval. These databases store the embeddings generated for various data points, such as documents, images, or audio segments, in the form of vectors. Rather than traditional database searches based on substrings or exact matches, vector databases allow searching based on the nearest neighbors in the vector space. By calculating the similarity between the embeddings of the query and the stored embeddings, vector databases can retrieve the most relevant data points in a more significant way than a substring or exact match search can.

> It is important to note that repeatedly calling embedding models with LangChain to search over a large number of vectors quickly isn’t very efficient or cost-effective. In such a situation, using a vector database is a much more suitable option. (Unsure if necessary)

## Vector Databases

### Vihaal Writing on Vector Databases

Vector databases play a crucial role in machine learning (ML) and large language model (LLM) applications. They are designed to efficiently store, index, and retrieve high-dimensional vectors, which are numerical representations of data points. These vectors can represent various entities such as words, documents, images, or user preferences. Vector databases work hand in hand with the embedding models that create such high-dimensional vectors.

The importance of vector databases lies in the many utilities and operations it allows embeddings to perform once the semantic meaning of data is vectorized. Of these, there are three that are particularly significant:

1. Efficient Similarity Search: Vector databases excel at performing efficient similarity searches. ML algorithms often rely on measuring the similarity between vectors to make accurate predictions or recommendations. By using specialized indexing structures like KD-trees or Annoy, vector databases can quickly find the most similar vectors to a given query, enabling fast retrieval of relevant information.
2. Nearest Neighbor Search: Vector databases enable efficient nearest neighbor search operations. Given a query vector, ML algorithms often need to find the closest vectors in the dataset. This operation is essential in recommendation systems, clustering, anomaly detection, and other ML tasks. Vector databases can perform nearest-neighbor searches efficiently, allowing ML models to find relevant data points in multi-dimensional spaces.
3. Embedding Storage: LLMs often rely on pre-trained embeddings, where words or sentences are mapped to high-dimensional vectors. Vector databases provide a convenient and efficient way to store and retrieve these embeddings. By using vector databases, LLMs can quickly access pre-trained embeddings for various language-related tasks, such as text generation, language translation, or sentiment analysis instead of calling embedding models every time there is a query.

Vector databases are undoubtedly important when used in conjunction with embedding models, but how exactly do they compare with traditional databases? While they are both databases, vector databases differ greatly from traditional databases when it comes to the format and structure of the database and how querying functions within the database:
   
1. Data Representation: Traditional databases are typically designed to store structured data in tabular formats, such as rows and columns. They are optimized for transactional operations and data consistency. In contrast, vector databases focus on storing and querying high-dimensional vectors, which are often unstructured or semi-structured data representations. They prioritize efficient similarity searches and nearest-neighbor operations rather than traditional relational operations.
2. Indexing Techniques: Traditional databases use indexing techniques like B-trees or hash indexes to accelerate query performance based on certain attribute values. These indexing methods are not well-suited for high-dimensional vector searches. Instead, vector databases employ specialized indexing structures like KD trees, ball trees, or locality-sensitive hashing (LSH) to efficiently index and search high-dimensional vectors.

Perhaps comparing vector databases with traditional databases wasn’t appropriate, after all, vector databases contain data formatted as high-dimensional vectors within a larger, interconnected vector space. Instead, a comparison between vector databases and graph databases seems more appropriate:

1. Data Model: Graph databases are designed to represent and store relationships between entities in the form of nodes and edges. They focus on capturing complex relationships and querying graph-based patterns efficiently. On the other hand, vector databases primarily focus on storing and querying high-dimensional vectors, with a lower emphasis on explicitly modeling and querying relationships between entities.
2. Query Paradigm: Graph databases offer powerful graph query languages (e.g., Cypher for Neo4j) that allow expressive queries to traverse and explore relationships in the graph. These queries emphasize graph traversal and pattern matching. In contrast, vector databases prioritize similarity search and nearest neighbor operations, which involve measuring vector distances rather than explicitly traversing graphical structures.
3. Use Cases: Graph databases excel in use cases where the relationships between entities are critical, such as social networks, recommendation systems, fraud detection, or knowledge graphs. Vector databases, on the other hand, are particularly beneficial in ML/LLM applications where high-dimensional vector representations and similarity-based operations are essential, such as content-based recommendation systems, text search, or image retrieval.

todo: summarize + segue

### ChatGPT on Vector Databases

Vector databases play a crucial role in large language model applications by enabling efficient and scalable retrieval of relevant information or embeddings for various tasks. Here's an explanation of their role in the context of large language models:

* Efficient Similarity Search: Large language models often operate in high-dimensional vector spaces, where each word, sentence, or document is represented as a numerical vector. Vector databases provide efficient indexing and search capabilities, allowing for similarity-based retrieval of vectors. This is essential for tasks like semantic search, where the goal is to find similar or related content based on vector representations.

* Document and Text Retrieval: Large language models can be utilized for document or text retrieval tasks, where given a query, the goal is to retrieve the most relevant documents or passages. Vector databases help accelerate this process by efficiently indexing and querying large collections of text embeddings, allowing for fast retrieval of relevant documents or text snippets.

* Nearest Neighbor Search: Vector databases enable nearest neighbor search, which is fundamental in various applications. For example, in text completion or language generation tasks, a large language model may need to find the most semantically similar or contextually appropriate words or phrases to complete a given prompt. Vector databases enable efficient search for nearest neighbors in the embedding space, aiding in generating relevant and coherent responses.

* Clustering and Categorization: Vector databases facilitate clustering and categorization tasks by grouping similar vectors together. These clusters can help in organizing and structuring large amounts of text data, supporting tasks such as topic modeling, content recommendation, or information retrieval.

* Contextual Embedding Storage: Large language models like GPT-3.5 generate contextual embeddings that capture the meaning and context of words, sentences, or documents. Vector databases allow for the storage and retrieval of these embeddings, enabling efficient access to contextual information for downstream tasks such as question answering, sentiment analysis, or text summarization.

* Scalability and Indexing: Vector databases provide efficient indexing and storage mechanisms that can handle large-scale language models and extensive text collections. They optimize memory usage, enable parallel processing, and support distributed computing to handle the high-dimensional vector representations generated by large language models.

In summary, vector databases play a vital role in large language model applications by facilitating efficient search, retrieval, clustering, and categorization of vector representations. They enable scalability and accelerate various tasks that rely on vector-based operations, enhancing the overall performance and usability of large language models.

* ChromaDB
* Pinecone
* Vectera
* [ todo: more ]

> Pinecone is an external database where developers can store relevant contextual data for LLM apps. Rather than sending large document collections back and forth with every API call, developers can store them in a Pinecone database, then pick only the few most relevant to any given query — an approach called in-context learning. It’s a must-have for enterprise use cases to truly bloom.
> In particular, Pinecone is a vector database, which means data is stored in the form of semantically meaningful embeddings. While a technical explanation of embeddings is beyond the scope of this post, the important part to understand is that LLMs also operate on vector embeddings — so by storing data in Pinecone in this format, part of the AI work has effectively been pre-processed and offloaded to the database.

## Model Servers

* [ todo: source ]



# Implementing LLMs in Applications



## General Architecture of LLM Applications


diagram here


## Options for Building LLM Applications

LangChain
Open Source Python Library
Can Use multiple Models (OpenAI, or Local)
Google Generative AI Studio
closed source
Built into GCP
Prompt Engineering Workbench
Tons of emerging libraries, really…


## Model Variations in LLMs

Models

1. Use a Pre-Trained LLM
2. In-Context Learning with Pre-Trained LLM - Fine-Tune an Existing LLM
3. Use Ray/DGX to Finetune models

## Building a Question / Answer System with LangChain

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


### What is LangChain?

what what?

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



## Natural Language Dataset Query with LLMs


Natural Language Dataset Query with LLMs

Querying Tabular Stores with NL:
https://python.langchain.com/en/latest/use_cases/tabular.html
Using Chains to Query APIs
https://python.langchain.com/en/latest/use_cases/apis.html
Using NL to Query SQL Databases
https://python.langchain.com/en/latest/modules/chains/examples/sqlite.html
https://github.com/hodgesmr/LangChain-Data-Demo

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
