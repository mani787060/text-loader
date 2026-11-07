# LangChain Text Document Loader

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Framework](https://img.shields.io/badge/Framework-LangChain-green)
![Data Ingestion](https://img.shields.io/badge/Focus-Text%20Data%20Ingestion-orange)
![Status](https://img.shields.io/badge/Project-Learning%20Implementation-blueviolet)

A practical implementation of **LangChain's `TextLoader`** for loading plain-text files and converting their contents into structured LangChain `Document` objects.

This project introduces the fundamentals of document ingestion, an essential step in building Generative AI and Retrieval-Augmented Generation (RAG) applications.

---

## Project Overview

Not all knowledge used in AI applications comes from PDFs, websites, or databases. A significant amount of useful information is stored in simple text files, including documentation, notes, application logs, and text-based reports.

LangChain provides `TextLoader` to simplify the process of reading these files and preparing their contents for further processing.

This project explores how to:

- Load plain-text files using LangChain.
- Handle character encoding during file ingestion.
- Convert file contents into LangChain `Document` objects.
- Access extracted content through `page_content`.
- Preserve source information using document metadata.
- Prepare loaded documents for downstream text splitting and RAG workflows.

## Key Concepts and Implementations

### 1. TextLoader Integration

`TextLoader` is a LangChain document loader designed to read text files and convert their contents into `Document` objects.

Example:

```python
from langchain_community.document_loaders import TextLoader

loader = TextLoader("sample.txt", encoding="utf-8")

documents = loader.load()

print(documents)
```

Instead of manually opening and reading files, you can use LangChain's loader interface to prepare documents for an AI pipeline.

### 2. File Encoding Management

Text files can contain different characters, symbols, and languages.

Choosing an appropriate encoding helps prevent decoding errors when reading files.

For example:

```python
loader = TextLoader(
    "sample.txt",
    encoding="utf-8"
)
```

UTF-8 is a widely used encoding that supports a broad range of characters.

The appropriate encoding depends on how the original file was saved.

### 3. Understanding the LangChain Document Object

After loading a text file, LangChain represents its content using a `Document` object.

A `Document` generally contains two important attributes:

**`page_content`**

Stores the extracted text from the source file.

**`metadata`**

Stores additional information associated with the document, such as its source file path.

Example:

```python
for document in documents:
    print("Content:")
    print(document.page_content)

    print("Metadata:")
    print(document.metadata)
```

This structure makes it easier to pass document content into other LangChain components.

### 4. Metadata Preservation

Document metadata helps maintain information about where the content originated.

For example, the source path can help identify the original file when processing multiple documents.

This becomes especially useful in RAG applications, where retrieved information should be traceable to its source.

### 5. Preparing Documents for RAG Pipelines

Loading a document is usually only the first step in a RAG application.

The extracted text can subsequently be passed to a text splitter, embedding model, and vector database.

This project focuses on the initial ingestion stage rather than implementing the complete RAG pipeline.

---

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| LangChain | Document-processing framework |
| langchain-community | Provides `TextLoader` |
| python-dotenv | Environment variable management, if required |

---

## Project Structure

```text
text-loader/
│
├── sample.txt
├── text_loader.py
├── requirements.txt
└── README.md
```

The sample text file is an example input. Adjust the structure according to your actual repository files.

---

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/mani787060/text-loader.git
cd text-loader
```

### 2. Create a Virtual Environment

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

Activate it on Linux/macOS:

```bash
source .venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -U langchain-community python-dotenv
```

### 4. Prepare a Text File

Create a file named `sample.txt` in the project directory.

Add some sample content, such as:

```text
Generative AI enables machines to generate
new content based on patterns learned from data.

LangChain provides reusable components
for building applications powered by language models.
```

Make sure the filename and path match the ones configured in your Python script.

### 5. Run the Implementation

```bash
python text_loader.py
```

The script should load the text file and return its contents as LangChain `Document` objects.

---

## How TextLoader Fits into RAG

A simplified document-processing workflow looks like this:

```text
      Text File
          |
          v
      TextLoader
          |
          v
   Document Object
          |
          v
    Text Splitting
          |
          v
  Embedding Generation
          |
          v
    Vector Database
          |
          v
       Retrieval
          |
          v
    LLM Response
```

This repository focuses on the **text document loading stage**. The remaining components can be integrated to build a complete RAG-based question-answering application.

---

## Learning Outcomes

By exploring this project, you can understand:

- How LangChain loads plain-text files.
- How to configure file encoding.
- How LangChain `Document` objects work.
- The difference between `page_content` and `metadata`.
- Why source tracking is useful in document processing.
- How document loaders contribute to RAG applications.

## Future Improvements

- Support loading multiple text files.
- Explore different character encodings.
- Integrate `RecursiveCharacterTextSplitter`.
- Generate embeddings using an embedding model.
- Store document vectors using FAISS or Chroma.
- Build a question-answering system using retrieved document context.

---

