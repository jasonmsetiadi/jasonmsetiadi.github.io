---
layout: post
comments: true
title: "LLM Optimization Patterns"
excerpt: "3 common patterns/ways to improve performance of LLM systems."
date:   2023-11-08 07:00:00
mathjax: false
---

Here we will discuss 3 existing patterns that are commonly used to optimize LLM systems performance.

## Prompt Engineering

People often have the misconception that prompt engineering is just trying out random prompts and eye ball results for a one time job/task. Real prompt engineering involves creating prompts that is going to be used repeatedly in high frequencies/volumes as part of an LLM system, with an engineered approaches, e.g., define problem/spec, build, version, **testing prompts and outputs** (speed, accuracy, toxicity, etc), finding edge cases, runtime monitoring, and iterative improvements. Moreover, it can serve as your **baseline performance for system evaluations** before adding the following complex patterns. 

> Prompt engineering is the process of searching through program space to find the program that empirically seems to perform best on your target task. 
-**François Chollet**

<!-- One of the most common prompt engineering techniques is called few-shot prompting. In simple terms, we can provide examples of our desired output to help the LLM follow the examples. For example, you may need an LLM to classify customer reviews as "positive" or "negative". Without few-shot, LLM can answer in a variety of ways. However, few-shot can guide the LLM to only respond with "positive" or "negative".

Another example is preventing LLMs from answering out of scope questions. We can provide detailed instructions by telling the scope of task, how to respond when given out of scope questions, even calling out edge cases. -->

## RAG

While prompt engineering can steer model’s output / behavior, it is still limited to the data the LLM is pre-trained on. RAG allows LLMs to **obtain knowledge beyond their pre-training data**, such as current data, confidential/internal data, etc. Furthermore, it can **reduce hallucination (false information)** through providing accurate content. RAG is commonly used for question answering over unstructured data (documents).

Ideally, we should only utilize the most relevant knowledge / context for the given user prompt. One reason is because LLMs have context length limitations. Besides, it wouldn't be so efficient to provide too much knowledge that may be irrelevant to the prompt, and it would also cost a lot more. So, RAG only takes text chunks from a collection of documents that are most relevant to a user prompt through the use of embedding models! 

Typically, documents will be split into smaller text chunks. Then, we use embedding models on each text chunk to obtain its embeddings (a numerical representation of the text chunk, used to calculate relevancy against a given prompt). These text chunk - embedding pairs can be stored in a vector store. Finally, given a user prompt, we can compute its embedding and search over the vector store to obtain only the most relevant (highest cosine similarity) text chunks (aka Retrieval), and pass it as input to the LLM (aka Augmented Generation).

> **Note:**
The retrieval step (only using embedding models) can be used for other use cases such as [semantic search](https://cookbook.openai.com/examples/semantic_text_search_using_embeddings) or [recommendations](https://cookbook.openai.com/examples/recommendation_using_embeddings), without the need for augmented generation (without using LLMs).

Some helpful examples:
- [Preparing Dataset for Retrieval](https://cookbook.openai.com/examples/embedding_wikipedia_articles_for_search)
- [RAG](https://cookbook.openai.com/examples/question_answering_using_embeddings)

<!-- ## Tools
What if we want to apply the same solution that RAG offers but for data types other than unstructured (structured, code). Tools can help by offering a flexible way to obtain such relevant data.
Build agents. 
QA over structured data = prompts -> queries -> structured data + prompt -> output
QA over code (code interpreter) = prompts -> code -> code result + prompt -> output
-->

## Fine-Tuning

Given the randomness of LLMs, prompt engineering may not be the solution if you need reliable outputs. Fine-tuning allows LLMs to get better at specific tasks and produce **more reliable outputs**. Furthermore, fine-tuning can achieve this with **less token usage** compared to prompt engineering. This involves providing example inputs and outputs of your specific task, so that LLMs can learn and perform according to your examples. One example of this is if you wanted to build a classifier for sentiment analysis. Your inputs would be some text and your outputs would be specific classes (e.g. “positive” or “negative”). In general, some common use cases for fine-tuning include respond in a specific style or a specific output, follow complex prompts, perform a new task, or handle edge cases.

We can think of fine-tuning as the typical ML model training process. We can first create a training dataset that has examples of how to perform our desired task. We may optionally create a validation dataset for evaluation to avoid overfitting. If using a fine-tuning API, we may need to validate our datasets so that they adhere to the expected format. Once the datasets are ready, we can start the fine-tuning process to train the pre-trained LLM with the training examples we have formed. Finally, we can save this fine-tuned LLM for inference.

> **Note:**
Try to maximize your efforts using prompt engineering (few shot examples), prompt chaining, or function calling, before moving towards fine-tuning.

Some helpful examples:
- [Preparing Dataset for Fine-tuning](https://cookbook.openai.com/examples/chat_finetuning_data_prep)
- [Fine-tuning](https://cookbook.openai.com/examples/how_to_finetune_chat_models)

## References
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