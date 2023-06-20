

<!--
Yao Fu then goes on to offer a diagram (embedded below) showing the evolution tree of GPT-3

![GPT Abilities](https://yaofu.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F2ea67e8e-18e1-42d0-9bd9-dbb1f47e22f0%2FUntitled.png?id=a039705a-5a32-41ef-bfb7-1c2793e90e74&table=block&spaceId=281b3c78-d734-43fb-aa33-707babff9463&width=1150&userId=&cache=v2)

Some abilities of note in the above diagram:
-->


### More Abilities and the Evolution of GPT-3.5

TODO: consider including this section to better outline abilities of models

More Yao Fu:

> Now let’s look at code-davinci-002 and text-davinci-002, the two first GPT3.5 models, one for code and the other for text. There are four important abilities they exhibit that differentiate them from the initial GPT-3

- **Responding to human instruction**: previously, the outputs of GPT-3 were mostly high-frequency prompt-completion patterns within the training set. Now the model generates reasonable answers to the prompt, rather than related but useless sentences.
- **Generalization to unseen tasks**: when the number of instructions used for tuning the model is beyond a certain scale, the model can automatically generate completions for new instructions that are not in the training set. **This ability is crucial for deployment**, as users with always come up with new prompts.
- **Code generation and code understanding**: obviously, because the model is trained on code.
- **Complex reasoning** **with chain-of-thought**



### Conclusions on GPT-3.5 Abilities

* todo: need to decide where we're going w the line of thought for the abilities
   * is this to support ideas around focusing on specific tests for specific tasks -- short of retraining the model?
   * is this to push further with the in-context line of thought?


Below --- summarizes the source of abilities for GPT-3:

`The initial GPT-3 model gains its generation ability, world knowledge, and in-context learning from pretraining.`

`Then the instruction tuning branch gains the ability to follow instructions and generalization to unseen tasks. The training on code branch gains the ability of code understanding, and potentially the side product of complex reasoning. Combining the two branches, code-davinci-002 seems to be the most capable GPT-3.5 model with all the powerful abilities.`


### In-Context Learning

todo

https://datascience.stackexchange.com/questions/115554/how-exactly-does-in-context-few-shot-learning-actually-work-in-theory-under-the

https://arxiv.org/pdf/2005.14165.pdf

https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00485/111728/True-Few-Shot-Learning-with-Prompts-A-Real-World

http://ai.stanford.edu/blog/understanding-incontext/

### Chain of Thought


### Decomposed Prompting

[ICLR 2023] Decomposed Prompting: A Modular Approach for Solving Complex Tasks. [paper][code]






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



`- Will large language model replace search engine?
    - No. LLMs are good for reasoning, not for knowledge. The knowledge within LLMs are unreliable and cannot be verified.
    - On the other hand, the knowledge from search engine is orders or magnitude larger than LLM’s internal knowledge, one can easily verify credibility of search results by checking the source.
    - Combining LLMs and search is a good direction. Let search handle knowledge, let LLMs handle reasoning.`


<!--
<img style="float: right;" src="./images/19th_century_textile_loom.jpg">
-->




## Foundation Models

Large language models are basesd on [foundation models](https://arxiv.org/abs/2205.09911):

> Foundation Models (FMs) are models trained on large corpora of data that, at very large scale, can generalize to new tasks without any task-specific finetuning. As these models continue to grow in size, innovations continue to push the boundaries of what these models can do on language and image tasks.

https://hai.stanford.edu/news/reflections-foundation-models

> The term Foundation Model (FM) was coined by Stanford researchers to introduce a new category of ML models. They defined FMs as models trained on broad data (generally using self-supervision at scale) that can be adapted to a wide range of downstream tasks.

> The Stanford team made a point to note that FMs are NOT foundational models in the sense that they are not the foundation for AI — that is, such models are not implied to be AGI.


> We define foundation models as models trained on broad data (generally using self-supervision at scale) that can be adapted to a wide range of downstream tasks. These models, which are based on standard ideas in transfer learning and recent advances in deep learning and computer systems applied at a very large scale, demonstrate surprising emergent capabilities and substantially improve performance on a wide range of downstream tasks. Given this potential, we see foundation models as the subject of a growing paradigm shift, where many AI systems across domains will directly build upon or heavily integrate foundation models.

> Naming The name “foundation model” has also drawn significant attention; given this attention, we want to provide context on how the name came about. We began by surveying existing terms (e.g., “(large) language model”, “self-supervised model”, “pretrained model”). Of these terms, we found several did not identify the correct class or characteristics of models: “(large) language model” was too narrow given our focus was not only language; “self-supervised model” was too specific to the training objective; and “pretrained model” suggested that the noteworthy action all happened after “pretraining”. In general, we found most terms did not convey the care with which we felt these models should be built.



Chat gpt -- check this: 
> Foundation models are the initial versions of pre-trained language models that serve as the starting point for the development of large language models. They are typically trained on a diverse range of texts to learn the underlying patterns and structures of language.

> Large language models, on the other hand, are more advanced versions that are built upon the foundation models. They undergo an extensive training process using vast amounts of data to improve their language understanding and generation capabilities. Large language models like GPT-3 are designed to perform a wide array of language-related tasks, such as text completion, translation, summarization, and more.

> In essence, foundation models provide the basic building blocks for language understanding, while large language models are the enhanced and refined versions that have been trained on massive datasets to achieve impressive language processing abilities. They represent the culmination of iterative improvements and advancements in natural language processing research and technology.

examples of foundation models

* [BERT](https://arxiv.org/abs/1810.04805)
* ChatGPT
* GPT-3
* [DALL-E](https://www.journal-dogorangsang.in/no_1_NECG_21/14.pdf)
* Stable Diffusion






### Raw Source Notes

```
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
```



### ChatGPT on Vector Databases

Vector databases play a crucial role in large language model applications by enabling efficient and scalable retrieval of relevant information or embeddings for various tasks. Here's an explanation of their role in the context of large language models:

* Efficient Similarity Search: Large language models often operate in high-dimensional vector spaces, where each word, sentence, or document is represented as a numerical vector. Vector databases provide efficient indexing and search capabilities, allowing for similarity-based retrieval of vectors. This is essential for tasks like semantic search, where the goal is to find similar or related content based on vector representations.

* Document and Text Retrieval: Large language models can be utilized for document or text retrieval tasks, where given a query, the goal is to retrieve the most relevant documents or passages. Vector databases help accelerate this process by efficiently indexing and querying large collections of text embeddings, allowing for fast retrieval of relevant documents or text snippets.

* Nearest Neighbor Search: Vector databases enable nearest neighbor search, which is fundamental in various applications. For example, in text completion or language generation tasks, a large language model may need to find the most semantically similar or contextually appropriate words or phrases to complete a given prompt. Vector databases enable efficient search for nearest neighbors in the embedding space, aiding in generating relevant and coherent responses.

* Clustering and Categorization: Vector databases facilitate clustering and categorization tasks by grouping similar vectors together. These clusters can help in organizing and structuring large amounts of text data, supporting tasks such as topic modeling, content recommendation, or information retrieval.

* Contextual Embedding Storage: Large language models like GPT-3.5 generate contextual embeddings that capture the meaning and context of words, sentences, or documents. Vector databases allow for the storage and retrieval of these embeddings, enabling efficient access to contextual information for downstream tasks such as question answering, sentiment analysis, or text summarization.

* Scalability and Indexing: Vector databases provide efficient indexing and storage mechanisms that can handle large-scale language models and extensive text collections. They optimize memory usage, enable parallel processing, and support distributed computing to handle the high-dimensional vector representations generated by large language models.

In summary, vector databases play a vital role in large language model applications by facilitating efficient search, retrieval, clustering, and categorization of vector representations. They enable scalability and accelerate various tasks that rely on vector-based operations, enhancing the overall performance and usability of large language models.

