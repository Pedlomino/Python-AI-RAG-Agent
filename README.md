This repository contains a Jupyter Notebook that demonstrates how to build a simple, educational AI coding tutor using a Tiny Retrieval-Augmented Generation (RAG) architecture.

It explores the foundational concepts of how AI agents use external memory and semantic search to improve their reasoning and provide context-aware responses.

## Overview

Large Language Models (LLMs) are powerful reasoning engines, but they lack access to private data and can confidently hallucinate when answering specific domain questions. This project addresses those limitations by building a "memory" pillar—a custom knowledge base that the LLM must consult before answering.

The notebook guides you through:

1. **Setting up the Environment:** Installing necessary dependencies (SentenceTransformers, FAISS, Google Generative AI, Groq) and configuring API access.
2. **Building the Knowledge Base:** Creating a Python dictionary filled with educational Python concepts (Lists, Functions, Loops, Strings).


3. **Generating Embeddings:** Using `SentenceTransformer` (`all-MiniLM-L6-v2`) to convert the text data into dense vector representations, allowing for semantic search based on meaning rather than just keyword matching.


4. **Indexing with FAISS:** Creating an index for the vectors to enable fast, efficient similarity searches.


5. **The Retrieval Function:** Querying the index to find the most relevant educational material and formatting it into plain text using a large language model.


6. **The Tutor Agent:** Constructing a prompt that forces the LLM to use the retrieved context, explain concepts simply, provide coding examples, highlight common mistakes, and ask follow-up questions.



## Requirements

To run this notebook, you will need:

* A Jupyter Notebook environment (like Google Colab or a local Jupyter installation).
* A Groq API Key (You can get a free one at `[https://console.groq.com/keys](https://console.groq.com/keys)`).


* *(Optional but recommended)* A Hugging Face token to avoid rate limits when downloading the embedding models.



## Quick Start

1. Clone this repository.
2. Open `Python-AI-RAG-Agent.ipynb` in your Jupyter environment.
3. Run the first code block to install the required libraries:
```python
!pip install -q sentence-transformers faiss-cpu google-generativeai groq

```


4. Insert your Groq API key in the specified cell:


```python
client = Groq(api_key="YOUR_API_KEY_HERE")

```


5. Run the subsequent cells sequentially to build the vector index and test the `ask_tutor()` function.



## Usage Example

Once the notebook is running, you can ask the tutor questions directly in the final cells:

```python
print(ask_tutor("How do you store a combination of letters in Python?"))

```

The tutor will semantically match your question to the "Python Strings" dictionary entry, retrieve the context, and generate a beginner-friendly explanation with examples and a follow-up question.
