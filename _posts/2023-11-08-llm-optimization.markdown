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

## RAG

While prompt engineering can steer model’s output / behavior, it is still limited to the data the LLM is pre-trained on. RAG allows LLMs to **obtain knowledge beyond their pre-training data**, such as current data, confidential/internal data, etc. Furthermore, it can **reduce hallucination (false information)** through providing accurate content. Some common use cases of RAG include, query generation, document summarization, code generation, etc.

## Fine-Tuning

Given the randomness of LLMs, prompt engineering may not be the solution if you need reliable outputs. Fine-tuning allows LLMs to get better at specific tasks and produce **more reliable outputs**. Furthermore, fine-tuning can achieve this with **less token usage** compared to prompt engineering. This involves providing example inputs and outputs of your specific task, so that LLMs can learn and perform according to your examples. One example of this is if you wanted to build a classifier for sentiment analysis. Your inputs would be some text and your outputs would be specific classes (e.g. “positive” or “negative”). In general, some common use cases for fine-tuning include respond in a specific style or a specific output, follow complex prompts, perform a new task, or handle edge cases.

> **Note:**
Try to maximize your efforts using prompt engineering (few shot examples), prompt chaining, or function calling, before moving towards fine-tuning.

## References
- [OpenAI Prompt Engineering Guide](https://platform.openai.com/docs/guides/prompt-engineering)
- [OpenAI Cookbook](https://cookbook.openai.com/)
- [Lilian Weng Prompt Engineering](https://lilianweng.github.io/posts/2023-03-15-prompt-engineering/)
<!-- (https://help.openai.com/en/collections/3675942-prompt-engineering)
(https://help.openai.com/en/articles/6654000-best-practices-for-prompt-engineering-with-openai-api)
(https://fchollet.substack.com/p/how-i-think-about-llm-prompt-engineering)
(https://www.anthropic.com/index/prompting-long-context)
(https://learnprompting.org/)
(https://github.com/f/awesome-chatgpt-prompts#prompts)
(https://developers.generativeai.google/guide/concepts) -->