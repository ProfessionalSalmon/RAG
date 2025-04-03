# How to Keep Your Glasses Clean

## 👓Overview
This repository demonstrates **Retrieval-Augmented Generation (RAG)** using the **LangChain** framework to enhance text generation by retrieving relevant documents and generating contextually accurate responses. The focus is on improving customer care instructions for cleaning glasses.

## 👓Workflow
1. **Document Embedding**: Documents are embedded using the `sentence-transformers/bert-base-nli-mean-tokens`.
2. **Storing in Chroma**: The embedded document is stored in a **Chroma vector database** to facilitate efficient similarity-based retrieval.
3. **Querying with Similarity Search**: When a user query is received (e.g., "Use strong detergent"), the system performs a **similarity search** against the embedded documents to retrieve the most relevant context.
4. **Text Generation**: The model `google/flan-t5-large` uses the retrieved documents to answer queries such as whether a certain action should be done to the glasses.

## 👓Prompt Used
The prompt template is designed to help the model answer whether a certain action should be done to glasses based on given guidelines (i.e., document):

```python
# python
from langchain_core.prompts import ChatPromptTemplate

message = """
Should I {question} to clean my glasses? Consider the following guidelines:
Guidelines:
{guideline}

Answer:
"""

prompt_template = ChatPromptTemplate.from_messages([("human", message)])
```
