# LangChain Text Document Loader
[![LangChain](https://img.shields.io/badge/Framework-LangChain-green)](https://www.langchain.com/)
[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/)
[![Data Ingestion](https://img.shields.io/badge/Pipeline-Data%20Ingestion-orange)](https://python.langchain.com/docs/modules/data_connection/document_loaders/)

## 🏗️ Project Overview
This repository focuses on **Foundational Data Ingestion**, the bedrock of any Retrieval-Augmented Generation (RAG) system. While AI systems frequently handle complex formats, an enormous amount of enterprise data—ranging from server logs to raw transcription outputs and markdown documentation—lives in plain text. This project demonstrates how to use LangChain's **`TextLoader`** to reliably read these files and package them into structured `Document` objects.

---

## 🛠️ Key Technical Implementations

### 1. Reliable File Ingestion
* **`TextLoader` Integration:** Utilizing LangChain's native loader to cleanly open, read, and close standard text files without writing boilerplate Python file-handling code.
* **Encoding Management:** Explicitly defining file encodings (like `utf-8`) to ensure the pipeline does not crash when encountering special characters or emojis in the source text.

### 2. The `Document` Object Model
* **Content Extraction:** Placing the entirety of the text file into the `page_content` attribute of the resulting object.
* **Metadata Preservation:** Automatically capturing the `source` (file path) and appending it to the metadata dictionary, ensuring that downstream AI responses can be traced back to the exact origin file.

### 3. Pipeline Readiness
* **Pre-Chunking State:** Outputting data in the exact, standardized format required by LangChain's Text Splitters, creating a seamless handoff to the tokenization and vectorization stages of the engineering pipeline.

---

## 💻 Tech Stack
* **Language:** Python 3.9+
* **Framework:** LangChain Community (`langchain-community`)
* **Environment:** Virtual Environment / `python-dotenv`

---

## 🚀 Getting Started

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/your-username/langchain-text-loader-fundamentals.git](https://github.com/your-username/langchain-text-loader-fundamentals.git)

2. **Install Dependencies:**
   ```bash
   pip install -U langchain-community python-dotenv

3. **Add a Sample Text File:**
   Place a sample text file (e.g., sample_logs.txt or notes.md) in the root directory.

4. **Run the Implementation:**
   ```bash
   python text_loader.py
   
