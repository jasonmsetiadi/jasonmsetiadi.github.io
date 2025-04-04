---
layout: post
comments: true
title: "How to use ChatGPT"
excerpt: "A comprehensive guide to leveraging all of ChatGPT's current capabilities."
date:   2025-03-08 07:00:00
mathjax: false
---

<div style="text-align: center;">
    <img src="/assets/chatgpt/default.png" width="75%"/>
</div>

The ChatGPT interface resembles a chat application, allowing users to interact with the AI seamlessly. At the center of this interface is a text input box where users can type their queries. 

Here are some basic examples of how to utilize ChatGPT effectively:

### 1. Writing Assistance
<div style="text-align: center;">
    <img src="/assets/chatgpt/examples/example-1.png" width="75%"/>
</div>

Users can request help with writing essays, reports, or emails, making it a versatile tool for various writing tasks. 

### 2. Information Retrieval
<div style="text-align: center;">
    <img src="/assets/chatgpt/examples/example-2.png" width="75%"/>
</div>

ChatGPT can provide comprehensive information on a wide range of historical topics, offering quick access to reliable facts and knowledge. 
However, it's important to understand that the model's knowledge is limited to data available up until its training cutoff date. 
For real-time information or current events that occurred after this cutoff, additional tools are required - which we'll explore later in this guide.

### 3. Language Translation
<div style="text-align: center;">
    <img src="/assets/chatgpt/examples/example-3.png" width="75%"/>
</div>

The model can assist in translating text across different languages and can also be a valuable tool for learning new languages, facilitating communication and understanding in multilingual contexts.

## Tools

We have seen the general capabilities of ChatGPT's base model in the examples above. However, despite its impressive performance, the model still has inherent limitations that restrict its ability to perform certain types of tasks.

This is where tools come into play. The integration of various specialized tools helps bridge these limitations, significantly enhancing the model's capabilities and allowing it to perform more complex and powerful tasks. Let's explore these tools and how they extend ChatGPT's functionality:

### 1. Image & Document Processing
<div style="text-align: center;">
    <img src="/assets/chatgpt/file-upload.png" width="75%"/>
</div>

ChatGPT supports uploading various file formats, which can be categorized into two main types:

- **Images**: PNG (.png), JPEG (.jpeg and .jpg), and non-animated GIF (.gif).
- **Text documents**: Including PDFs, spreadsheets (CSV/Excel), presentations, Microsoft Word documents, and text files.

While we typically think of ChatGPT as a tool for processing text inputs, it also has the capability to handle images, introducing a new modality beyond just text. It's important to note that text documents are treated as text input, meaning any embedded images within them will not be processed. For optimal results, if you're working with scanned documents (which are essentially images), it's best to upload them as images rather than documents.

This file upload tool enables three key types of tasks:

1. **Synthesis**: Combine or analyze information, such as comparing two documents or visualizing data from a spreadsheet.

2. **Transformation**: Reshape information from documents, like summarizing a complex research paper or rewriting a document in a specific style.

3. **Extraction**: Pull specific information from documents, such as finding references to a topic in a PDF or extracting metadata.

For more detailed information about this feature, visit the [official ChatGPT File Uploads documentation](https://help.openai.com/en/articles/8555545-file-uploads-faq).

Here are a couple of examples showcasing the file upload capabilities:

<div style="text-align: center;">
    <img src="/assets/chatgpt/examples/ocr.png" width="75%"/>
    <p><i>Extracting text from an invoice image using Optical Character Recognition (OCR)</i></p>
</div>

<div style="text-align: center;">
    <img src="/assets/chatgpt/examples/summarize.png" width="75%"/>
    <p><i>Summarizing the BCA February 2025 financial report</i></p>
</div>

### 2. Web Browsing
<div style="text-align: center;">
    <img src="/assets/chatgpt/search.png" width="75%"/>
</div>

The search tool effectively addresses ChatGPT's knowledge limitations regarding current events and up-to-date information. By integrating internet search capabilities, ChatGPT can access real-time data, providing more accurate and timely responses to your questions. 

A key advantage of this feature is transparency — ChatGPT will provide links to the web sources it references, allowing you to verify information and explore topics further on your own. This makes the search tool particularly valuable for research, fact-checking, and staying informed about recent developments that occurred after the model's training cutoff date.

For more detailed information about this feature, visit the [official ChatGPT Search documentation](https://help.openai.com/en/articles/9237897-chatgpt-search).

Here’s a straightforward example of using the search tool to browse for daily news:
<div style="text-align: center;">
    <img src="/assets/chatgpt/examples/search.png" width="75%"/>
</div>

### 3. Reasoning
<div style="text-align: center;">
    <img src="/assets/chatgpt/reason.png" width="75%"/>
</div>

Humans operate with two distinct thinking systems: system 1 (fast, automatic, intuitive) and system 2 (slow, deliberate, analytical). This dual-process framework allows us to switch between quick responses and deep reasoning based on task complexity.

Traditional GPT models, trained through supervised fine-tuning (SFT) with labeled data, primarily exhibited system 1 thinking capabilities. They excelled at immediate responses but struggled with problems requiring deeper analysis. OpenAI's breakthrough O series models represent a significant advancement in AI reasoning capabilities. Unlike their predecessors, these models are trained using pure reinforcement learning (RL) without SFT, better mimicking human cognitive processes.

Similar to how humans pause to think through complex problems rather than answering immediately, these reasoning models engage in system 2 thinking. They're specifically designed to take time processing information before responding, making them particularly effective for complex tasks in science, coding, and mathematics. This ability to "think before answering" enables these models to tackle intricate problems that previous generations of AI struggled to solve.

For more information about reasoning capabilities, check out these resources:
- [Reasoning Examples](https://openai.com/index/learning-to-reason-with-llms/)
- [Reasoning Best Practices](https://platform.openai.com/docs/guides/reasoning-best-practices)
- [Research Paper: Incentivizing Reasoning Capability in LLMs via RL](https://arxiv.org/abs/2501.12948)

### 4. Image Creation
<div style="text-align: center;">
    <img src="/assets/chatgpt/image-gen.png" width="75%"/>
</div>

ChatGPT isn't limited to just text responses—it can also generate images on demand. You don't need to craft a perfect description; simply tell ChatGPT what you'd like to see using natural, everyday language. ChatGPT can also make edits to images, you can simply attach one.

For more detailed information about this feature, visit the [official ChatGPT Image Creation documentation](https://help.openai.com/en/articles/8932459-creating-images-in-chatgpt).

Here are some practical applications:
<div style="text-align: center;">
        <img src="/assets/chatgpt/examples/image-gen.png" width="75%"/>
        <p><i>Creating compelling real estate advertisements with custom imagery</i></p>
</div>

<div style="text-align: center;">
    <img src="/assets/chatgpt/examples/image-edit.png" width="75%"/>
    <p><i>Changing President Trump's suit and tie to batik</i></p>
</div>