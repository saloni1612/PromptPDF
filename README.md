# PromptPDF
PromptPDF is a local Retrieval Augmented Generation (RAG) pipeline that allows you to query any PDF document using a Large Language Model (LLM). It includes PDF parsing, text chunking, embedding generation, semantic retrieval, and context-based response generation.

## Features

- Query any PDF document using natural language
- Local embedding generation and vector search
- Local LLM inference with no external API calls
- Built from scratch without LangChain or LlamaIndex
- Modular design, easy to extend and customize

## Installation

1. Clone the repository:

   git clone https://github.com/saloni1612/PromptPDF.git
   
   cd promptpdf


3. (Optional) Create and activate a virtual environment:

   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate

4. Install dependencies:

   pip install -r requirements.txt
   

5. Start your local LLM (e.g., using Ollama):

   ollama run mistral

## Usage

Run the main script with a sample query:

```python
from app import run_promptpdf

run_promptpdf("data/sample.pdf", "What are the key topics discussed in Chapter 3?")
```

This will load the PDF, create text chunks, generate embeddings, retrieve relevant context, and respond using a locally running LLM.

## Project Structure

```
promptpdf/
├── data/                   # PDFs and processed files
├── embeddings/             # Vector store and index
├── models/                 # LLM weights or loader interfaces
├── app.py                  # Main orchestrator script
├── chunker.py              # Handles PDF parsing and text chunking
├── embedder.py             # Embedding logic using sentence-transformers
├── retriever.py            # Vector similarity search
├── generator.py            # Handles prompt construction and LLM inference
├── utils.py                # Utility functions
├── requirements.txt        # Python dependencies
└── README.md               # Project documentation
```

## How It Works

1. **PDF Parsing**: The PDF is read and converted into plain text.
2. **Text Chunking**: The text is split into overlapping chunks suitable for embedding.
3. **Embedding Generation**: Each chunk is converted into a vector using a sentence-transformer model.
4. **Semantic Retrieval**: The most relevant chunks are retrieved using vector similarity search.
5. **Prompt Augmentation**: The user’s query is combined with the retrieved context.
6. **Response Generation**: A local LLM generates the final answer based on the augmented prompt.





### `requirements.txt`

```txt
PyPDF2==3.0.1
sentence-transformers==2.2.2
scikit-learn==1.3.0
numpy==1.24.4
faiss-cpu==1.7.4
transformers==4.39.3
torch>=2.0
llama-cpp-python==0.2.24
uvicorn==0.29.0
fastapi==0.110.0
````

