---
layout: post
published-on: March 27th 2023
author: Josh Patterson
title: An Introduction to Large Language Models (LLMs)
subtitle: Part 1 - Background and Core Concepts in LLMs
description: In this post we'll .....
keywords: snowflake, snowpark, automl, AutoGluon, pandas, dataframe, whl, pip, anaconda, dependency
meta_og_image: pct_autogluon_dep_og_card.jpg
---

# Introduction

Purpose of this series:

> To understand what LLMs are

This space is moving fast and its valuable to get a mental framing on how to think about LLMs to better understand how to apply them in your projects and organization

It also sets context for a better understanding of new developments in LLMs

Our technical series are based on private reports we produce for our enterprise customers.

The intended audience for this series is:

> Individual researchers, data scientists, and then also enterprise data teams as well

Series:

* [Background and Core Concepts in LLMs](intro_to_llms_part_1_terminology.html)
* [A Guide for Building Enterprise Application with LLMs](intro_to_llms_part_2_applications.html)
* [Putting LLM Applications into Production](intro_to_llms_part_3_model_management.html)
* [Appendix A: What is Artificial Intelligence?](dl_book_appendix_a_ai.html)

# What are Large Language Models (LLMs)?

Large language models, such as GPT-3.5, are advanced artificial intelligence systems designed to understand and generate human-like text. These models are trained on vast amounts of data to learn the patterns, structures, and semantics of language. They can then generate coherent and contextually relevant responses to various prompts.

Training a large language model involves utilizing a massive dataset, which often includes a wide range of texts from books, articles, websites, and other written sources. This diverse corpus helps the model learn the nuances of human language and develop a broad understanding of various topics.

Once trained, large language models can be used for a wide range of applications. They can generate human-like text, answer questions, assist with language translation, write code, summarize articles, create conversational agents, and much more. They achieve this by leveraging the knowledge and patterns they have learned during training.

It's important to note that while large language models like GPT-3.5 can generate impressive and coherent text, they don't possess true understanding or consciousness. They are statistical models that rely on patterns and associations in the training data rather than true comprehension.
LLMs are good at understanding written language in the form of plain text input. LLMs output plain text based on the plain text input.

Foundation models

https://arxiv.org/abs/2205.09911

> Foundation Models (FMs) are models trained on large corpora of data that, at very large scale, can generalize to new tasks without any task-specific finetuning. As these models continue to grow in size, innovations continue to push the boundaries of what these models can do on language and image tasks.

GPT-3 and GPT-4 are examples of large language models.

ChatGPT is an example of an application built around a large language model (here: GPT-3.5, etc)

LLMs themselves DO:

* reason about instructions and context in the input (the "prompt")
* create plans of actions, and then execute each step of the plan with further calls back to the LLM model
* integrate with external tools (search engines, wikipedia, python interpreters, etc) to try out commands and examine the input in a later LLM chained call

LLMs do not:

* execute code inside the neural network itself

Later on in this series we'll introduce a generalized application architecture for LLM-based applications.

todo

https://www.theatlantic.com/technology/archive/2023/01/artificial-intelligence-ai-chatgpt-dall-e-2-learning/672754/

emergent abilities

https://arxiv.org/abs/2205.09911

> Emergent Behaviors Interestingly, the biggest GPT-3 variant (175B parameters) has the capacity to solve natural language tasks with only a few examples (called few-shot prompting), and in some cases, just a task description (e.g. “Translate French to English”). Unlike traditional finetuning, no model parameters are updated to fit the task. Few-shot prompting has proven to be effective on tasks widely different from the FMs pretraining objective. Some examples include code generation [84], Trivia QA [18, 48] and common sense reasoning tasks [18]. Smaller models (less than 10B parameters) typically require some form of task-specific finetuning to perform well. 

https://www.quantamagazine.org/the-unpredictable-abilities-emerging-from-large-ai-models-20230316/

LLMs having their "stable diffusion"-moment

https://simonwillison.net/2023/Mar/11/llama/


## Will LLMs Start Replacing Jobs?

<img style="float: right;" src="./images/19th_century_textile_loom.jpg">

> "Rapid and pivotal advances in technology have a way of unsettling people, because they can reverberate mercilessly, sometimes, through business, employment, and cultural spheres. And so it is with the current shock and awe over large language models, such as GPT-4 from OpenAI."

> "It’s a textbook example of the mixture of amazement and, especially, anxiety that often accompanies a tech triumph."

> “It gives an answer with complete confidence, and I sort of believe it. And half the time, it’s completely wrong.”

> “A very famous senior person said, ‘Radiologists will be out of business before long.’ And people stopped enrolling in radiology specialties, and now there’s a shortage of them.”

> So what about these predictions that entire classes of employment will go away, paralegals, and so on? Is that a legitimate concern?

> Brooks: You certainly hear these things. I was reviewing a government report a few weeks ago, and it said, “Lawyers are going to disappear in 10 years.” So I tracked it down and it was one barrister in England, who knew nothing about AI. He said, “Surely, if it’s this good, it’s going to get so much better that we’ll be out of jobs in 10 years.” There’s a lot of disaster hype. Someone suggests something and it gets amplified.

> We saw that with radiologists. A very famous senior person said, “Radiologists will be out of business before long.” And people stopped enrolling in radiology specialties and now there’s a shortage of them. Same with truck driving…. There are so many ads from all these companies recruiting truck drivers because there’s not enough truck drivers, because three or four years ago, people were saying, “Truck driving is going to go away.”

https://spectrum.ieee.org/amp/gpt-4-calm-down-2660261157


LLMs and Artificial Intelligence --- [What is Artificial Intelligence?](dl_book_appendix_a_ai.html)


Reference the luddites

https://en.wikipedia.org/wiki/Luddite

> The Luddites were members of a 19th-century movement of English textile workers which opposed the use of certain types of cost-saving machinery, often by destroying the machines in clandestine raids. They protested against manufacturers who used machines in "a fraudulent and deceitful manner" to replace the skilled labour of workers and drive down wages by producing inferior goods.[1][2] Members of the group referred to themselves as Luddites, self-described followers of "Ned Ludd", a legendary weaver whose name was used as a pseudonym in threatening letters to mill owners and government officials.[3]



LLMs aren't taking jobs, they are accelerating workforce, a natural evolution of tooling

soon, they will be table stakes in many / most industries

## Terminology in Large Language Models (LLMs)

todo

* Prompt 
* Prompt Engineering
* In-Context Learning
* Indexing: (in realm of LLMs) can be considered a 
* Chain of Thought
* Embeddings
* vector databases
* fine-tuning: the model is trained via repeated gradient updates using a large corpus of example tasks
* Instruction tuning
* Reinforcement Learning from Human Feedback (RLHF)


todo

https://exchange.scale.com/public/events/llm-prompt-engineering-and-rlhf-history-and-techniques-2023-03-09

https://lilianweng.github.io/posts/2023-03-15-prompt-engineering/

https://github.com/dair-ai/Prompt-Engineering-Guide



todo

### Prompts and Prompt Engineering

In the context of large language models, prompts are the input text or instructions given to the model to generate a desired response. A prompt can be a question, a statement, or an incomplete sentence that sets the context for the model to generate a coherent and relevant output.

When providing a prompt, users specify their desired outcome or request, and the model generates a response based on the patterns and information it has learned during training. The prompt serves as a guide for the model to understand the user's intent and generate a suitable response accordingly.

The effectiveness of a prompt depends on its clarity, specificity, and relevance to the desired task. Well-crafted prompts help elicit accurate and meaningful responses from the model, while ambiguous or poorly phrased prompts may yield inaccurate or undesired outputs.

Prompt engineering, which involves optimizing the wording and structure of prompts, has become an important practice to improve the quality and reliability of model-generated responses. Researchers and developers often experiment with different prompt formulations to achieve the desired outcomes and mitigate potential biases or limitations of the language model.

sub-topics:

* instructions
* external information
* user input
* output indicator

https://www.pinecone.io/learn/langchain-prompt-templates/

### In-Context Learning

In-context learning refers to a technique used with large language models to fine-tune or adapt them to specific tasks or domains by providing additional training on task-specific examples or data. This process allows the model to specialize and improve its performance on specific tasks or to better align with the requirements of a particular application.

In large language models like GPT-3.5, the initial training involves exposing the model to a diverse range of text from various sources. However, this general training may not be sufficient for certain specific tasks or domains. In-context learning addresses this limitation by fine-tuning the model with additional examples or data that are relevant to the target task.

To perform in-context learning, the model is provided with specific prompt-response pairs or labeled examples related to the desired task. These pairs serve as additional training data, and the model is retrained using this task-specific information. By exposing the model to task-specific examples, it can learn to generate more accurate and contextually appropriate responses for that particular task.

In-context learning helps to enhance the model's performance, adaptability, and task-specific understanding. It allows large language models to be more versatile and capable of addressing a wide range of tasks and applications by leveraging the benefits of both general pre-training and task-specific fine-tuning.

* zero-shot
* one-shot
* few-shot

> Since GPT-2 (Radford et al.) and GPT-3 (Brown et al.), we have seen that generative large language models (LLMs) pretrained on a general text corpus are capable of in-context learning, which doesn’t require us to further train or finetune pretrained LLMs if we want to perform specific or new tasks that the LLM wasn’t explicitly trained on. Instead, we can directly provide a few examples of a target task via the input prompt, as illustrated in the example below.

> In-context learning is very useful if we don’t have direct access to the model, for instance, if we are using the model through an API.



## Deep Learning, Transformers, and Generative Language Models

The architecture of large language models typically consists of multiple layers of artificial neural networks. These networks contain millions or even billions of parameters that enable the model to capture and represent the complex relationships between words and concepts.

----

Deep learning, transformers, and large language models are interconnected concepts that play crucial roles in the development and success of advanced natural language processing (NLP) systems. Here's an overview of their relationship:

Deep Learning: Deep learning is a subfield of machine learning that focuses on training artificial neural networks with multiple layers to learn and extract complex patterns and representations from data. Deep learning algorithms, such as convolutional neural networks (CNNs) and recurrent neural networks (RNNs), have revolutionized various fields, including computer vision, speech recognition, and natural language processing.

Transformers: Transformers are a specific type of deep learning architecture that has significantly advanced NLP tasks. They were introduced in the seminal paper "Attention is All You Need" by Vaswani et al. in 2017. Transformers employ a self-attention mechanism to capture contextual dependencies between words in a sequence, allowing the model to weigh the importance of different words when generating responses. This attention mechanism helps transformers effectively model long-range dependencies and improves their ability to understand and generate coherent text.

Large Language Models: Large language models, such as GPT-3.5, are deep learning models built using transformer architectures specifically designed for language understanding and generation tasks. These models have been trained on massive amounts of text data, learning to predict the next word or sequence of words given a context. By leveraging the power of transformers and deep learning techniques, large language models can generate human-like text, answer questions, perform language translation, and assist with a wide range of natural language processing tasks.

The success of large language models is largely attributed to the transformer architecture's ability to capture long-range dependencies and learn contextual representations effectively. The deep learning techniques used in training these models allow them to understand complex patterns and relationships in language data, making them capable of generating coherent and contextually relevant text.

In summary, deep learning forms the foundation of large language models, and transformers provide the architecture that empowers these models with the ability to understand and generate natural language text. Together, they have revolutionized the field of NLP and enabled the development of sophisticated language understanding and generation systems.


* refernece our strata talk in 2016


### Defining Deep Learning

* DL is about automated feature learning


### Introduction of Transformers in 2017


<img style="float: right;" src="./images/transformers_architecture_2017.png">

* dont need to create features
* can use tons of data
* can use tons of parameters

https://amatriain.net/blog/transformer-models-an-introduction-and-catalog-2d1e9039f376/

LLMs are implemented with Neural Networks 
using the Transformer architecture
Transformers were introduced in 2017
they are an architecture of deep learning neural networks that worked well in natural language applications

great visual explanation of transformers: http://jalammar.github.io/illustrated-transformer/

Transformers can process long sequences of text and generate high-quality outputs for various language tasks, such as 
* text generation
* question answering
* translation

Noteworthy because:

Deep Learning is about using the correct architecture for a data type such that the architecture can perform automated feature engineering
Transformers are a Deep Learning architecture for natural language
Therefore, Transformer-based systems require no manual feature engineering

Transformers and LLMs rely directly on raw natural language text as the input



## The GPT Architecture

* based on transformers
* doesnt need feature engineering
* just give it structured set of natural language

> This is GPT's rockstar application -- a conditional generative model that creates near-human level quality text content.

### GPT Series of Models

https://platform.openai.com/docs/models

https://arxiv.org/abs/2005.14165

> GPT-3 comes in eight sizes, ranging from 125M to 175B parameters. The largest GPT-3 model is an order of magnitude larger than the previous record holder, T5-11B. The smallest GPT-3 model is roughly the size of BERT-Base and RoBERTa-Base.

> All GPT-3 models use the same attention-based architecture as their GPT-2 predecessor. The smallest GPT-3 model (125M) has 12 attention layers, each with 12x 64-dimension heads. The largest GPT-3 model (175B) uses 96 attention layers, each with 96x 128-dimension heads.

> GPT-3 expanded the capacity of its GPT-2 by three orders of magnitudes without significant modification of the model architecture — just more layers, wider layers, and more data to train it on

> But to put things into perspective, GPT-3 175B model required 3.14E23 FLOPS of computing for training. Even at theoretical 28 TFLOPS for V100 and lowest 3 year reserved cloud pricing we could find, this will take 355 GPU-years and cost $4.6M for a single training run. Similarly, a single RTX 8000, assuming 15 TFLOPS, would take 665 years to run.

Ray used to train gpt-3

https://www.anyscale.com/blog/ray-common-production-challenges-for-generative-ai-infrastructure

https://thenewstack.io/how-ray-a-distributed-ai-framework-helps-power-chatgpt/

### ChatGPT

https://help.openai.com/en/articles/6783457-what-is-chatgpt
```
ChatGPT is fine-tuned from GPT-3.5, a language model trained to produce text. ChatGPT was optimized for dialogue by using Reinforcement Learning with Human Feedback (RLHF) – a method that uses human demonstrations and preference comparisons to guide the model toward desired behavior.
```




* key summary
   * text in, text out 
   * no feature engineering



# LLM Abilities and Limitations

* the goal of this section is to communicate what you can expect out of LLMs

* this is analagous to understanding what to expect out of machine learning (classification, regression) and deep learning (image object detection, generative models, etc)

* its fun to talk about conscious robots and the like, but in the enterprise world of problem solving, we need to focus on what can be expected from our tools (here: llms)




## Initial GPT-3 Abilities and Evolution



Yao Fu [writes about the 3 important abilities that the initial GPT-3 exhibit](https://yaofu.notion.site/How-does-GPT-Obtain-its-Ability-Tracing-Emergent-Abilities-of-Language-Models-to-their-Sources-b9a57ac0fcf74f30a1ab9e3e36fa1dc1):
 
- **Language generation**: to follow a prompt and then generate a completion of the given prompt. Today, this might be the most ubiquitous way of human-LM interaction.
- **In-context learning**: to follow a few examples of a given task and then generate the solution for a new test case. It is interesting to note that, although being a language model, the original GPT-3 paper barely talks about “language modeling” — the authors devoted their writing efforts to their visions of in-context learning, which is the real focus of GPT-3.
- **World knowledge**: including factual knowledge and commonsense.

For those inclined in the details, Fu's article is wonderfully detailed and contains considerable insight into the evolution of the GPT-series of LLMs.

Fu goes on to describe the origin of the abilites of GPT-3:

> Generally, the above three abilities should come from large-scale pretraining — to pretrain the 175B parameters model on 300B tokens 

* 60% 2016 - 2019 Common Crawl
* 22% WebText2
* 16% Books
* 3% Wikipedia). 

Where:

- The **language generation** ability comes from the language modeling **training objective**.
- The **world knowledge** comes from the 300B token **training corpora** (or where else it could be).
- The **175B model size** is for **storing knowledge**, which is further evidenced by Liang et al. (2022), who conclude that the performance on tasks requiring knowledge correlates with model size.
- The source of the **in-context learning** ability, as well as its generalization behavior, **is still elusive**. Intuitively, this ability may come from the fact that data points of the same task are ordered sequentially in the same batch during pretraining. Yet there is little study on why language model pretraining induces in-context learning, and why in-context learning behaves so differently than fine-tuning.

<!--
Yao Fu then goes on to offer a diagram (embedded below) showing the evolution tree of GPT-3

![GPT Abilities](https://yaofu.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F2ea67e8e-18e1-42d0-9bd9-dbb1f47e22f0%2FUntitled.png?id=a039705a-5a32-41ef-bfb7-1c2793e90e74&table=block&spaceId=281b3c78-d734-43fb-aa33-707babff9463&width=1150&userId=&cache=v2)

Some abilities of note in the above diagram:
-->

For reference, if we say the average book has 80,000 words in it, and ~2 million tokens is roughly the equivalent to 1.5 million words, we can calculate the total books GPT-3 was trained on to be **around 2.8 million books** based on a 300 billion token training corpora.

For comparison, the average person might read around 700 books in their lifetime.

The entire series is wonderful for insight into how large language models such as GPT-3 get certain types of "abilities" such as "code generation" and "in-context learning".


## More Abilities and the Evolution of GPT-3.5


More Yao Fu:

> Now let’s look at code-davinci-002 and text-davinci-002, the two first GPT3.5 models, one for code and the other for text. There are four important abilities they exhibit that differentiate them from the initial GPT-3

- **Responding to human instruction**: previously, the outputs of GPT-3 were mostly high-frequency prompt-completion patterns within the training set. Now the model generates reasonable answers to the prompt, rather than related but useless sentences.
- **Generalization to unseen tasks**: when the number of instructions used for tuning the model is beyond a certain scale, the model can automatically generate completions for new instructions that are not in the training set. **This ability is crucial for deployment**, as users with always come up with new prompts.
- **Code generation and code understanding**: obviously, because the model is trained on code.
- **Complex reasoning** **with chain-of-thought**

### Conclusions on GPT-3.5 Abilities

* todo

`The initial GPT-3 model gains its generation ability, world knowledge, and in-context learning from pretraining.`

`Then the instruction tuning branch gains the ability to follow instructions and generalization to unseen tasks. The training on code branch gains the ability of code understanding, and potentially the side product of complex reasoning. Combining the two branches, code-davinci-002 seems to be the most capable GPT-3.5 model with all the powerful abilities.`



### Knowledge vs Reasoning

* define knowledge
* explain use in people and in LLMs
* discuss specific abilities of GPT-3

Knowledge: Knowledge refers to the information, facts, and understanding that an individual possesses about the world. It represents accumulated information and expertise gained through learning and experience.

Reasoning: Reasoning is the mental process of drawing conclusions or making inferences based on available information, logic, and rules. It involves using logical and cognitive abilities to analyze, evaluate, and synthesize information.

Nature:

Knowledge: Knowledge is a repository of information and understanding. It encompasses facts, concepts, rules, relationships, and models about various domains. It is generally static and acquired through learning and observation.

Reasoning: Reasoning is a dynamic cognitive process that involves actively manipulating and processing information to arrive at logical conclusions or make decisions. It involves using cognitive abilities such as deduction, induction, and abductive reasoning.

Role:

Knowledge: Knowledge provides the foundation and raw material for reasoning. It serves as a basis for making informed decisions, solving problems, and understanding the world. Knowledge provides context and background information that can be used in the reasoning process.
Reasoning: Reasoning employs logical and cognitive processes to analyze and manipulate knowledge. It helps in organizing, connecting, and utilizing knowledge to derive new insights, solve problems, make judgments, and make predictions.
Dependency:

Knowledge: Knowledge is a prerequisite for effective reasoning. Reasoning heavily relies on the availability and accuracy of relevant knowledge. Lack of knowledge can limit the quality and accuracy of reasoning.
Reasoning: Reasoning can operate even in the absence of complete knowledge. It can make use of partial or incomplete information to draw conclusions or make decisions. Reasoning can also be employed to fill gaps in knowledge and acquire new knowledge.

Knowledge defined:
> "facts, information, and skills acquired by a person through experience or education; the theoretical or practical understanding of a subject."

Reasoning defined:
> "the action of thinking about something in a logical, sensible way."

In summary, knowledge and reasoning are interrelated cognitive processes. Knowledge provides the information and foundation for reasoning, while reasoning employs logical and cognitive processes to manipulate knowledge and arrive at conclusions. Knowledge represents accumulated information, while reasoning is a dynamic process of drawing inferences and making decisions based on available information.






https://arxiv.org/abs/2212.10403

* explain and contrast reasoning vs knowledge
* discuss specific abilities of GPT-3

Types of reasoning in LLMs:
https://ai.googleblog.com/2022/05/language-models-perform-reasoning-via.html


World knowledge: including factual knowledge and commonsense.

Yao Fu:
`- The two important but different abilities of GPT-3.5 are **knowledge** and **reasoning**. Generally, it would be ideal if we could **offload the knowledge part to the outside retrieval system and let the language model only focus on reasoning.** This is because:
    - The model’s internal knowledge is always cut off at a certain time. The model always needs up-to-date knowledge to answer up-to-date questions.
    - Recall we have discussed that is 175B parameter is heavily used for storing knowledge. If we could offload knowledge to be outside the model, then the model parameter might be significantly reduced such that eventually, it can run on a cellphone (call this crazy here, but ChatGPT is already science fiction enough, who knows what the future will be).
    `

discuss: "Chain of Thought"

#### Use Cases with Reasoning

* Arithmetic reasoning
* Problem solving
* Commonsense reasoning

https://github.com/Mooler0410/LLMsPracticalGuide

> "Scaling of LLMs~(e.g. parameters, training computation, etc.) can greatly empower pretrained language models. With the model scaling up, a model generally becomes more capable in a range of tasks. Reflected in some metrics, the performance shows a power-law relationship with the model scale."


#### Use Cases with Emergent Abilities

* Word manipulation
* Logical deduction
* Logical sequence
* Logic grid puzzles
* Simple math problems
* Coding abilities
* Concept understanding

https://github.com/Mooler0410/LLMsPracticalGuide



### In-Context Learning

todo

https://datascience.stackexchange.com/questions/115554/how-exactly-does-in-context-few-shot-learning-actually-work-in-theory-under-the

https://arxiv.org/pdf/2005.14165.pdf

https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00485/111728/True-Few-Shot-Learning-with-Prompts-A-Real-World

http://ai.stanford.edu/blog/understanding-incontext/

### Chain of Thought


### Decomposed Prompting

[ICLR 2023] Decomposed Prompting: A Modular Approach for Solving Complex Tasks. [paper][code]



## Comparing LLMs' Ability to do Complex Tasks

Paper: https://arxiv.org/abs/2305.17306

> As large language models (LLMs) are continuously being developed, their evaluation becomes increasingly important yet challenging. This work proposes Chain-of-Thought Hub, an open-source evaluation suite on the multi-step reasoning capabilities of large language models. We are interested in this setting for two reasons: (1) from the behavior of GPT and PaLM model family, we observe that complex reasoning is likely to be a key differentiator between weaker and stronger LLMs; (2) we envisage large language models to become the next-generation computational platform and foster an ecosystem of LLM-based new applications, this naturally requires the foundation models to perform complex tasks that often involve the composition of linguistic and logical operations. Our approach is to compile a suite of challenging reasoning benchmarks to track the progress of LLMs. Our current results show that: (1) model scale clearly correlates with reasoning capabilities; (2) As of May 2023, Claude-v1.3 and PaLM-2 are the only two models that are comparable with GPT-4, while open-sourced models still lag behind; (3) LLaMA-65B performs closely to code-davinci-002, indicating that with successful further development such as reinforcement learning from human feedback (RLHF), it has great potential to be close to GPT-3.5-Turbo. Our results also suggest that for the open-source efforts to catch up, the community may focus more on building better base models and exploring RLHF.

https://github.com/FranxYao/chain-of-thought-hub

> The key differentiator is whether a model can do complex tasks, like the old saying: "chit-chat is cheap, show me the reasoning." This is why we compile a list of complex reasoning tasks including math (GSM8K), science (MATH, TheoremQA), symbolic (BBH), knowledge (MMLU, C-Eval), coding (HumanEval), factual (SummEdits) to measure the models' performance on challenging tasks.

Complex Reasoning Tasks:

* math (GSM8K)
* science (MATH, TheoremQA)
* symbolic (BBH)
* knowledge (MMLU, C-Eval)
* coding (HumanEval)
* factual (SummEdits)

[ this is where we'd put some radar plots comparing abilities of models ]








## Currrent Limitations of GPT-3.5

* on-the-fly overwriting the model's beliefs
* formal reasoning

While large language models have demonstrated remarkable capabilities, they also have several limitations:

Biases and unfairness: Language models learn from vast amounts of data, which may contain biases present in the text. As a result, they can inadvertently generate biased or unfair content, reflecting and perpetuating societal biases, stereotypes, or prejudices.

Lack of common sense: Large language models often struggle with common sense reasoning. They can generate plausible-sounding but incorrect or nonsensical responses. They lack true understanding of the world and may provide inaccurate or illogical information.

Contextual misunderstandings: Language models may misinterpret or misjudge the context of a prompt, leading to incorrect or nonsensical responses. They often rely heavily on the immediate preceding text and may not consider broader or long-term context.

Sensitivity to input phrasing: The phrasing or wording of a prompt can significantly impact the generated response. Small changes in the input can lead to different outputs, making the models less reliable for critical or sensitive tasks.

Limited knowledge and outdated information: Language models have a knowledge cutoff, meaning they are not aware of events or information that occurred after their training data. Therefore, they may provide outdated or incorrect information about recent events.

Ethical concerns: Language models raise ethical concerns, particularly regarding the potential for misuse, such as generating fake news or deepfake content, spreading misinformation, or engaging in malicious activities like impersonation or harassment.

High computational requirements: Training and deploying large language models require significant computational resources, making them inaccessible to many researchers and organizations. This can hinder widespread adoption and contribute to the concentration of AI capabilities in a few entities.

Addressing these limitations is an active area of research and development, with ongoing efforts to enhance model robustness, mitigate biases, improve understanding of context, and promote ethical use of large language models.

## Summary 

`- Will large language model replace search engine?
    - No. LLMs are good for reasoning, not for knowledge. The knowledge within LLMs are unreliable and cannot be verified.
    - On the other hand, the knowledge from search engine is orders or magnitude larger than LLM’s internal knowledge, one can easily verify credibility of search results by checking the source.
    - Combining LLMs and search is a good direction. Let search handle knowledge, let LLMs handle reasoning.`

# Why Are Large Language Models Compelling?

todo

## Tectonic Plate Shifts in Technology

todo

## Natural Language as a Driver for Any Application

toodo

ChatGPT was a nice demo, but there is a lot more here


## You Don't Have to Re-Train the Foundation Models to Do Things

It's amazing


# Summary

https://cube.dev/blog/conversational-interface-for-semantic-layer

https://github.com/approximatelabs/sketch


# References

Fu, Yao; Peng, Hao and Khot, Tushar. (Dec 2022). How does GPT Obtain its Ability? Tracing Emergent Abilities of Language Models to their Sources. Yao Fu’s Notion. https://yaofu.notion.site/How-does-GPT-Obtain-its-Ability-Tracing-Emergent-Abilities-of-Language-Models-to-their-Sources-b9a57ac0fcf74f30a1ab9e3e36fa1dc1

Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., Kaiser, L., & Polosukhin, I. (2017). Attention is All you Need. Neural Information Processing Systems, 30, 5998–6008. https://arxiv.org/pdf/1706.03762v5