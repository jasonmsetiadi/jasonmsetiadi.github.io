---
layout: post
comments: true
title: "LLM Optimization Techniques"
excerpt: "3 common patterns/techniques to optimize performance of LLM systems."
date:   2023-11-08 07:00:00
mathjax: false
---

There are two types of challenges that can hinder the performance of LLMs. One challenge is knowledge / context limitation, as pre-trained LLMs are limited to the knowledge they were pre-trained on. Hence, they tend to hallucinate repsponses (being confidently wrong, providing false information), whenever the answer to the user query doesn't exist in their pretraining knowledge. Another challenge relates to reliability, where pre-trained LLMs may exhibit variability in their outputs due to their inherently random nature. Here, we will discuss on a high-level, 3 common techniques to mitigate these challenges and improve LLM performance.

## Prompt Engineering

People often have the misconception that prompt engineering is just trying out random prompts and eye ball results for a one time job/task. Real prompt engineering involves creating prompts that is going to be used repeatedly in high frequencies/volumes as part of an LLM system, with an engineered approach, e.g., define problem/spec, build, version, **testing prompts and outputs** (speed, accuracy, toxicity, etc), finding edge cases, runtime monitoring, and iterative improvements. Moreover, it can serve as your **baseline performance** for system evaluations before adding more complex patterns. 

> Prompt engineering is the process of searching through program space to find the program that empirically seems to perform best on your target task. 
-**François Chollet**

One way we can use prompt engineering for context challenges is to augment knowledge beyond the pre-training data (e.g. current data, confidential/internal data, domain-specific data, etc). However, this becomes a problem when we have a large knowledge base we want to augment as LLMs have limited context length. Maxing out the input context with augmented knowledge is not a good idea since LLMs tends to get [lost in the middle of long contexts](https://arxiv.org/abs/2307.03172) and the number of input tokens is bloated. Furthermore, LLMs can still hallucinate if we augment context that is unrelated to the user query. Therefore, it is crucial to augment knowledge that is relevant to answering the user query.

To address reliability concerns, we can use one prompt engineering technique called few-shot learning. We can augment/provide input-output examples before the user prompt to help LLMs follow the given examples. Nevertheless, this can become problematic as we increase the number of examples, given the context length limitation and the increase in number of tokens.

Prompt engineering is indeed a good start when building LLM systems. However, given the challenges mentioned above, we may need other approaches to overcome them and optimize our system's performance. The following techniques present solutions to these problems, namely RAG for context limitation and Fine-tuning for reliability concerns.

<!-- 
For example, you may need an LLM to classify customer reviews as "positive" or "negative". Without few-shot, LLM can answer in a variety of ways. However, few-shot can guide the LLM to only respond with "positive" or "negative". 
Write clear instructions (provide steps to reach the solution), split complex task into simpler subtasks, give GPTs time to think (step by step), show output structure (JSON)
limited context length, hallucinations, constrained knowledge, not so reliable (random), expensive
-->

## RAG
<!-- 
limited context length, hallucinations, constrained knowledge,
Function calling is part of RAG by using external tools to retrieve knowledge (API)

evals:
- is the generated answer factually accurate? (faithfulness)
- does the generated output answer the question? (relevancy)
- does the retreived context contain noise (not used to answer the question)? (precision)
- is the answer to the question contained in the retrieved context? (recall)
-->
The main difference between RAG and prompt engineering is the Retrieval step. It is a way to **retrieve only the relevant content** for the user query. This way, we can retrieve knowledge that is relevant as well as within the context length. This step helps achieve the goals of **obtain knowledge beyond their pre-training data** and **reduce hallucination (false information)** but in a more scalable and robust way. Common use cases for RAG are question answering or summarization over large amounts of unstructured data (documents) or structured data (database). 

We can think of the *Retrieval* step as a tool that LLMs can utilize (calling functions). The retrieval method depends on the data type of the knowledge source. For example, given we have large amount of documents (unstructured data), we can use embedding models to retrieve the most relevant text chunks from a vector store to augment the user query. Another example is to retrieve via the internet (e.g. google search, wikipedia, etc) by sending API requests. For retrieval over structured data, we can use a text-to-SQL model to generate queries given user prompt and database information. Then, we can execute the query to obtain the query result as the retrieved context.

<!-- Typically, documents will be split into smaller text chunks. Then, we use embedding models on each text chunk to obtain its embeddings (a numerical representation of the text chunk, used to calculate relevancy against a given prompt). These text chunk - embedding pairs can be stored in a vector store. Finally, given a user prompt, we can compute its embedding and search over the vector store to obtain only the most relevant (highest cosine similarity) text chunks (aka Retrieval), and pass it as input to the LLM (aka Augmented Generation). -->

> **Note:**
The retrieval step (only using embedding models) can be used for other use cases such as [semantic search](https://cookbook.openai.com/examples/semantic_text_search_using_embeddings) or [recommendations](https://cookbook.openai.com/examples/recommendation_using_embeddings), without the need for augmented generation (without using LLMs).
<!-- > - RAG can also be a [tool of an agent](https://cookbook.openai.com/examples/how_to_call_functions_for_knowledge_retrieval) when the documents you want to retrieve depends on the user query. -->

Some helpful examples:
- [Preparing Dataset for Retrieval](https://cookbook.openai.com/examples/embedding_wikipedia_articles_for_search)
- [RAG](https://cookbook.openai.com/examples/question_answering_using_embeddings)
<!-- https://github.com/jxnl/n-levels-of-rag -->

<!-- ## Tools
The purpose of tools is similar to RAG, it serves as context enrichment tool for LLM.
There are 2 use case for tools. it can serve as context enrichment (prompt augmentation) or to answer directly (calculator)
What if we want to apply the same solution that RAG offers but for data types other than unstructured (structured, code).
One main difference between Tools and RAG is that RAG uses embedding models while Tools use functions to obtain relevant context.
Functions are used only when it depends on the user query.
one example tool is google search api
Tools can help by offering a flexible way to obtain such relevant data.
Build agents. 
QA over structured data = prompts -> queries -> structured data + prompt -> output
QA over code (code interpreter) = prompts -> code -> code result + prompt -> output

- [Function Calling](https://cookbook.openai.com/examples/how_to_call_functions_with_chat_models)
- [Retrieval as Search Tool](https://cookbook.openai.com/examples/how_to_call_functions_for_knowledge_retrieval)
when the documents you want to retrieve depends on the user query. -->

## Fine-Tuning

<!-- 
not so reliable (random) -> we have seen that we can use few-shot learning to make LLMs somewhat reliable. 
expensive -> with prompt engineering, you may need to provide examples in every single API call. this can lead to inflated costs. fine tuning can mitigate this so the LLM learns those examples while keeping your input tokens low.
(consistent instruction following)
One example of this is if you wanted to build a classifier for sentiment analysis. Your inputs would be some text and your outputs would be specific classes (e.g. “positive” or “negative”).
-->
Given the randomness of LLMs, prompt engineering may not be the only solution if you need reliable outputs. Fine-tuning allows LLMs to get better at specific tasks and produce **more reliable outputs**. This involves providing example inputs and outputs of your specific task, so that LLMs can learn and perform according to your examples. Unlike few-shot learning where the number of examples is limited by the LLM context length, fine-tuning enables us to provide **unlimited number of examples** to the LLM. In addition, it offers **reduced cost and latency** through less token usage and a smaller model. Some common use cases for fine-tuning include respond in a specific style or structure, follow complex instructions, perform a specific task (e.g. code interpreter), or handle edge cases. 

We can think of fine-tuning as continuing the model training process on our dataset. We can first create a training dataset that has examples of how to perform our desired task. We may optionally create a validation dataset for evaluation to avoid overfitting. If using a fine-tuning API, we may need to validate our datasets so that they adhere to the expected format. Once the datasets are ready, we can start the fine-tuning process to train the pre-trained LLM with the training examples we have formed. We can experiment with different hyperparameters (batch size, learning rate, number of epochs) when fine-tuning. Finally, we can use this fine-tuned LLM for inference. Note that it is best practice to first evaluate the fine-tuned model before serving it for inference.

> **Note:**
> - Try to maximize your efforts using prompt engineering (few shot learning), prompt chaining, or function calling, before moving towards fine-tuning.
> - Start small and focus on quality when preparing your training datasets for fine-tuning.

Some helpful examples:
- [Preparing Dataset for Fine-tuning](https://cookbook.openai.com/examples/chat_finetuning_data_prep)
- [Fine-tuning](https://cookbook.openai.com/examples/how_to_finetune_chat_models)

## References
- [OpenAI DevDay Session](https://youtu.be/ahnGLM-RC1Y?si=A4dLdsSo2twnWH6X)
- [OpenAI Prompt Engineering Guide](https://platform.openai.com/docs/guides/prompt-engineering)
- [OpenAI Fine-Tuning Guide](https://platform.openai.com/docs/guides/fine-tuning)
- [OpenAI Cookbook](https://cookbook.openai.com/)
- [Lilian Weng Prompt Engineering](https://lilianweng.github.io/posts/2023-03-15-prompt-engineering/)
<!-- (https://help.openai.com/en/collections/3675942-prompt-engineering)
(https://help.openai.com/en/articles/6654000-best-practices-for-prompt-engineering-with-openai-api)
(https://fchollet.substack.com/p/how-i-think-about-llm-prompt-engineering)
(https://www.anthropic.com/index/prompting-long-context)
(https://learnprompting.org/)
(https://github.com/f/awesome-chatgpt-prompts#prompts)
(https://developers.generativeai.google/guide/concepts) -->