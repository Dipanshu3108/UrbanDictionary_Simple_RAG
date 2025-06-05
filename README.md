# Urban Dictionary RAG System

A Retrieval-Augmented Generation (RAG) system built with LangChain and Hugging Face that answers questions about slang terms using Urban Dictionary data.

## Features

- **Local LLM**: Uses Qwen models (0.6B or 1.7B) for text generation
- **Vector Search**: Chroma vector database with sentence-transformers embeddings
- **Urban Dictionary Knowledge Base**: Answers questions about slang and informal language
- **Optimized for Google Colab**: Memory-efficient setup for free tier usage

## Requirements

```bash
pip install langchain langchain-chroma chromadb langchain-huggingface sentence-transformers transformers torch accelerate
```

## Setup

1. **Environment Variables**: Set your API keys
   ```python
   os.environ["LANGSMITH_API_KEY"] = "<your-key>"
   os.environ["HUGGING_FACE_API_KEY"] = "<your-key>"
   ```

2. **Data**: Place Urban Dictionary CSV file (`urbandict-word-defs.csv`) in your Google Drive

3. **Mount Drive**: Update the drive mount path in the notebook

## Usage

1. **Load and Process Data**: The notebook loads 5,001 rows from the Urban Dictionary dataset
2. **Create Embeddings**: Uses `sentence-transformers/all-mpnet-base-v2` for text embeddings
3. **Build Vector Store**: Creates a Chroma database for similarity search
4. **Setup LLM**: Loads a local Qwen model (default: 0.6B version)
5. **Query the System**: Ask questions about slang terms

## Example Queries

```python
query_urban_dictionary("What does 'janky' mean?")
query_urban_dictionary("Tell me about words related to being cool or awesome")
```

## Model Options

- `qwen3-0.6b`: Qwen/Qwen3-0.6B (default, faster)
- `qwen3-1.7b`: Qwen/Qwen3-1.7B (larger, more capable)

## Output

The system returns:
- Answer based on Urban Dictionary definitions
- Source documents with word definitions
- Confidence scores and metadata
