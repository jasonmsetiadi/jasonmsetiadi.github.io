---
layout: post
comments: true
title: "LLM Optimization Techniques"
excerpt: "3 common patterns/techniques to optimize performance of LLM systems."
date:   2023-11-08 07:00:00
mathjax: false
---

There are two types of challenges that can hinder the performance of LLMs. One challenge is knowledge/context limitation, as pre-trained LLMs are limited to the knowledge they were pre-trained on. Another challenge relates to reliability, where pre-trained LLMs may exhibit variability in their outputs due to their inherently random nature. Here, we will discuss 3 common techniques to mitigate these challenges and improve LLM performance.

## Prompt Engineering

People often have the misconception that prompt engineering is just trying out random prompts and eye ball results for a one time job/task. Real prompt engineering involves creating prompts that is going to be used repeatedly in high frequencies/volumes as part of an LLM system, with an engineered approaches, e.g., define problem/spec, build, version, **testing prompts and outputs** (speed, accuracy, toxicity, etc), finding edge cases, runtime monitoring, and iterative improvements. Moreover, it can serve as your **baseline performance** for system evaluations before adding the following complex patterns. 

> Prompt engineering is the process of searching through program space to find the program that empirically seems to perform best on your target task. 
-**François Chollet**

Prompt engineering is a good start when building LLM systems. We can augment knowledge beyond the pre-training data (current data, confidential/internal data, domain-specific data, etc) to solve context challenges. However, this becomes a problem when we have a large knowledge base we want to augment as LLMs have limited context window. Furthermore, it can still hallucinate if we retrieve context that is unrelated to the user prompt. We can also use few-shot learning to make LLMs more reliable, but this can become problematic as we increase the number of examples. Each call will be more expensive and the number of examples is limited to the LLM context window. The following techniques present solutions to these problems, namely RAG for context limitation and Fine-tuning for reliability concerns.


<!-- limited context window, hallucinations, constrained knowledge, not so reliable (random), expensive.  -->

<!-- For example, you may need an LLM to classify customer reviews as "positive" or "negative". Without few-shot, LLM can answer in a variety of ways. However, few-shot can guide the LLM to only respond with "positive" or "negative". 
Write clear instructions (provide steps to reach the solution), split complex task into simpler subtasks, give GPTs time to think (step by step), show output structure (JSON)
limited context window, hallucinations, constrained knowledge, not so reliable (random), expensive
-->

## RAG

While prompt engineering can steer model’s output / behavior, it is still limited to the data the LLM is pre-trained on. RAG allows LLMs to **obtain knowledge beyond their pre-training data**, such as current data, confidential/internal data, etc. Furthermore, it can **reduce hallucination (false information)** through providing accurate content. RAG is commonly used for question answering over unstructured data (documents).

Ideally, we should only utilize the most relevant knowledge / context for the given user prompt. One reason is because LLMs have context length limitations. Besides, it wouldn't be so efficient to provide too much knowledge that may be irrelevant to the prompt, and it would also cost a lot more. So, RAG only takes text chunks from a collection of documents that are most relevant to a user prompt through the use of embedding models! 

Typically, documents will be split into smaller text chunks. Then, we use embedding models on each text chunk to obtain its embeddings (a numerical representation of the text chunk, used to calculate relevancy against a given prompt). These text chunk - embedding pairs can be stored in a vector store. Finally, given a user prompt, we can compute its embedding and search over the vector store to obtain only the most relevant (highest cosine similarity) text chunks (aka Retrieval), and pass it as input to the LLM (aka Augmented Generation).

> **Note:**
The retrieval step (only using embedding models) can be used for other use cases such as [semantic search](https://cookbook.openai.com/examples/semantic_text_search_using_embeddings) or [recommendations](https://cookbook.openai.com/examples/recommendation_using_embeddings), without the need for augmented generation (without using LLMs).
<!-- > - RAG can also be a [tool of an agent](https://cookbook.openai.com/examples/how_to_call_functions_for_knowledge_retrieval) when the documents you want to retrieve depends on the user query. -->

Some helpful examples:
- [Preparing Dataset for Retrieval](https://cookbook.openai.com/examples/embedding_wikipedia_articles_for_search)
- [RAG](https://cookbook.openai.com/examples/question_answering_using_embeddings)

<!-- ## Tools
The purpose of tools is similar to RAG, it serves as context enrichment tool for LLM.
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
-->

## Fine-Tuning

<!-- 
not so reliable (random) -> we have seen that we can use few-shot learning to make LLMs somewhat reliable. 
expensive -> with prompt engineering, you may need to provide examples in every single API call. this can lead to inflated costs. fine tuning can mitigate this so the LLM learns those examples while keeping your input tokens low.
(consistent instruction following)
One example of this is if you wanted to build a classifier for sentiment analysis. Your inputs would be some text and your outputs would be specific classes (e.g. “positive” or “negative”).
-->
Given the randomness of LLMs, prompt engineering may not be the only solution if you need reliable outputs. Fine-tuning allows LLMs to get better at specific tasks and produce **more reliable outputs**. This involves providing example inputs and outputs of your specific task, so that LLMs can learn and perform according to your examples. Unlike few-shot learning where the number of examples is limited by the LLM context window, fine-tuning enables us to provide **unlimited number of examples** to the LLM. In addition, it offers **reduced cost and latency** through less token usage and a smaller model. Some common use cases for fine-tuning include respond in a specific style or structure, follow complex instructions, perform a specific task (e.g. code interpreter), or handle edge cases. 

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