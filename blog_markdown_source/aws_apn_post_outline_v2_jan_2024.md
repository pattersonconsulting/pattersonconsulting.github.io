
You are a smart business analyst and writer. The reader is a technical founder or VP of Engineering. You are writing an article for a technical Blog.

Use this voice: informative and objective, with a touch of personal perspective

Use this tone: generally positive and enthusiastic, particularly when discussing the potential applications of large language models. Include a mix of technical and more conversational language, making the content accessible.

Use this style: be efficient in how you use words, opting for less words when more words do not help. be balanced in how you present the material, engaging both technical and non-technical readers.

Use this structure: the writing should follows a logical flow

Below is the outline for the article.

# Section 1: Introduction

* At AWS Re:Invent 2023 there were many new announcements in the realm of Generative AI
* AWS SageMaker and AWS Bedrock are quickly emerging as go to platforms for deploying Generative AI applications
* Why invest in LLM for reasoning applications in 2024?
   * LLMs will have an impact for enterprise on productivity, marketshare, profitability
   * Enterprise risk and cost of inaction, Can late adopters catch up

# Section 2: Trends

* Examples/characteristics of LLM applications
   * generate human-like text, answer questions, assist with language translation, write code, summarize article, create conversational agents
   * Enterprise value of LLM application is often increased by incorporating knowledge of the enterprise data (database lookup, document review).
* One key requirement to operate private appliations will be the need to use private models (e.g., "not openAI") when using private data
* We use the RAG design pattern to connect our private knowledge with the reasoning power of LLMs to build next-gen AI apps on AWS


# Section 3: What to Look Out for When Building LLM Applications

* We want to think about LLM applications in the terms of "knowledge vs reasoning", where our enterprise data in AWS is the knowledge, and LLM models provide the reasoning
* with most enterprise applications we want to augment prompts with private data from our private "knowledge" repositories (data warehouse, s3, etc)
* this means we're taking private data and adding it as strings into a prompt (e.g., a "larger string") to be evaluated by the large language model
* if we're using someone else's model (e.g., "openAI"), then our private customer data is exposed to their models and logging system
* for many use cases, this is a non-starter in terms of data security
* therefore, we need to control our own models, and so we need to take on the tasks of choosing a private model and operating it on infrastructure we control and can secure
* different models are more effective at different types of sub-tasks
* Choosing the correct private model, however, can be tricky


## Section 3.1 : Challenes in Choosing a LLM Model

* openAI has powerful models such as GPT3 and GPT4, but these models are difficult to run as private LLM model isntances
* smaller private models typically are more efficient to operate, but they have less horsepower in certain types of reasoning
* To build efficient, cost-effective AI applications we need a way to compare different models for our specific tasks with our data


## Section 3.2: The Reasoning Workbench

* Patterson Consulting has led the development of the open source tool called the "Reasoning Workbench"
* the Reasoning Workbench is an easy and direct way to generate scores to compare different models 
* this tool can you quickly get a relative sense/measure for which model works best for your sepecific AI application


## Section 3.3: Benefits of Evaluating Models with the Reasoning Workbench

* being able to quickly pick the best model for your use case allows your team to act quickly and decisively deploy new AI apps with confidence
* better models are less costly to operate (less tokens)
* smaller models require less costly cloud resources to operate, therefore are cheaper to run (what is model size to performance tradeoff? how do you quickly evaluate this?)
* applications require less prompt engineering, which allows us to do fewer inferences to our private models
* all of the above gives the end user a faster and more efficient user experience



# Section 5: Using the Reasoning Workbench on AWS

* load the notebook into AWS SageMaker Studio Lab

* the notebook will automatically pull in the reasoning_workbench python module

## Section 5.1: Writing a Configuration File

* configure the models.json file and the prompts.json file
* each entry in the JSON file corresponds to a model hosted on HuggingFace


## Section 5.2: Generating the Model Report

* run the notebook, the output will be generated and saved locally:
   * a JSON file containing the collected performance of each model
   * a radar plot image for each model's general performance
   * a radar plot image for each model's performance on the use case specific prompts
* if you don't supply custom prompts, it won't generate a "use case score" in the radar plot
* if you have custom prompts, then you'll need a GPU instance to generate scores

# Section 6: Interpreting the Report

* The general performance radar plot gives a relative idea of how the different private models stack up when compared to one another across 4 general areas and 1 use case specific area. 
* The 4 general areas are:
   * Language Understanding
   * World Knowledge
   * Math
   * Correctness
* In this case we use a relative score because any specific rating or number may not hold up across your specific use case
* the benefit of using custom prompts to evaluate models is that we can better compare models on tasks specific to your organization, data, and domain
* The secondary radar plot breaks down the Use Case Specific rating into sub-areas so you can get a better understanding on how the models perform in different sub-tasks



## Section 6.1: Implications of Model Metrics

* Average Prompt Inference Time: gives a relative sense on how long a user or application will have to wait for a single prompt analysis
   * Impact: application design

* Model Parameter Size: this correlates to GPU memory, so any GPU we choose will have to have enough memory to fit the model into GPU-RAM
   * Impact: We use the above two metrics to help choose our GPU to operate the private LLM
* which GPU we choose impacts the cost to operate in the cloud
* the reasoning workbench report helps us understand potential GPU spend and overhead to operate a LLM-based application on AWS

Note: do we test across multiple GPUs?

# Section 7: Next Steps

* once you have a baseline comparison, this will arm you and your team with the information needed to take next-steps on your genAI journey


## Section 7.1: Deploy to AWS Sagemaker

* If you want to start experimenting with one of the specific models, Patterson Consutling can help deploy the model for further testing on AWS Bedrock

https://aws.amazon.com/blogs/opensource/deploy-large-language-models-easily-with-the-new-ezsmdeploy-python-sdk/

## Section 7.2: Help Designing Custom Prompts

* if you want to further explore custom model performance on your specific use case, Patterson Consutling can help with custom prompt development


## Section 7.3: Designing and Deploying Custom Agents on AWS

* if you are ready to start building out your LLM application on AWS, Patterson Consulting can help design and deploy new custom agents on AWS with your team


## Section 7.4: Fine-Tune a Model

* Patterson Consulting can help you further fine-tune a specific model for a use cases


Write 1 paragraphs for an article based on section 2 in the outline above 


