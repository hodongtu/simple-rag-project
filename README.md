# Simple RAG Project

A minimal Retrieval-Augmented Generation (RAG) example in a single notebook.

## Goal

Understand the **core mechanics of RAG** by building a minimal working example and watching the components interact.

## What the demo shows

- Loading a plain-text knowledge base
- Splitting it into paragraph-based chunks
- Embedding chunks with `paraphrase-multilingual-mpnet-base-v2` (runs locally)
- Storing the vectors in a FAISS index
- Retrieving the most relevant chunks for a question
- Building a RAG prompt from the retrieved context
- Generating the answer with the OpenAI Chat Completions API

## Setup

Requires Python 3.12 or another recent version.

1. Clone the repository and open a terminal in its root.

2. Create and activate a virtual environment.

   Linux / macOS:
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```
   Windows:
   ```bash
   python -m venv .venv
   .venv\Scripts\activate.bat
   ```

3. Install the packages:
   ```bash
   pip install -r requirements.txt
   ```

4. Create a `.env` file in the root directory:
   ```
   OPENAI_API_KEY=your_key_here
   OPENAI_API_BASE=https://api.openai.com/v1
   MODEL_ECONOMY=gpt-4o-mini
   ```
   Get a key at [platform.openai.com/api-keys](https://platform.openai.com/api-keys). `.env` is excluded via `.gitignore` and never committed.

5. Open `simple_rag_project.ipynb` and run the cells top to bottom.

On the first run, the notebook downloads the embedding model (about 1 GB) and caches it locally.

## Configuration

| Variable | Required | Purpose |
| --- | --- | --- |
| `OPENAI_API_KEY` | yes | API credential; the notebook stops with a clear error if it is missing |
| `OPENAI_API_BASE` | no | API endpoint, defaults to `https://api.openai.com/v1`; change it to use a compatible provider |
| `MODEL_ECONOMY` | no | Chat model, defaults to `gpt-4o-mini` |

Only the answer generation calls the API. Embedding and retrieval run locally, so experimenting with chunks, questions and `k` costs nothing.

## License

Apache License 2.0
