# Hybrid Search RAG

A Streamlit-powered Retrieval-Augmented Generation (RAG) application that combines hybrid search, reranking, and large language models (LLMs) to answer questions based on your uploaded PDF documents. The app supports OpenAI, Anthropic, and Cohere APIs for embedding, reranking, and language modeling.

---

## Features

- **PDF Document Upload:** Upload one or more PDF files for ingestion and semantic search.
- **Hybrid Search:** Combines dense and sparse retrieval for robust document chunk search.
- **Reranking:** Uses Cohere’s reranker to improve the relevance of retrieved chunks.
- **LLM-Powered Answers:** Answers questions using context from your documents via Anthropic Claude or OpenAI models.
- **Fallback to General Knowledge:** If no relevant document context is found, falls back to general LLM knowledge.
- **Streamlit UI:** User-friendly web interface for configuration, document upload, and chat.

---

## Project Structure

```
main.py               # Streamlit app and core logic
requirements.txt      # Python dependencies
README.md             # Project documentation
```

---

## Installation

1. **Clone the repository:**

   ```sh
   git clone https://github.com/Yavic2024/hybrid_search_rag.git
   cd hybrid_search_rag
   ```

2. **Create a virtual environment (recommended):**

   ```sh
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**

   ```sh
   pip install -r requirements.txt
   ```

---

## Configuration

You will need API keys for:
- [OpenAI](https://platform.openai.com/account/api-keys)
- [Anthropic](https://console.anthropic.com/settings/keys)
- [Cohere](https://dashboard.cohere.com/api-keys)

The app uses a SQLite database by default (`sqlite:///raglite.sqlite`), but you can provide any SQLAlchemy-compatible database URL.

---

## Usage

1. **Start the Streamlit app:**

   ```sh
   streamlit run main.py
   ```

2. **Configure API Keys and Database:**
   - Enter your OpenAI, Anthropic, and Cohere API keys in the sidebar.
   - Optionally, change the database URL.
   - Click **Save Configuration**.

3. **Upload Documents:**
   - Upload one or more PDF files.
   - Wait for processing confirmation.

4. **Ask Questions:**
   - Use the chat interface to ask questions about your uploaded documents.
   - If no relevant context is found, the app will use general LLM knowledge to answer.

---

## How It Works

- **Document Ingestion:** Uploaded PDFs are chunked and embedded using OpenAI’s embedding model.
- **Hybrid Search:** When you ask a question, the app performs a hybrid search (dense + sparse) to find relevant chunks.
- **Reranking:** Cohere’s reranker sorts the chunks by relevance.
- **LLM Answering:** The top chunks are provided as context to Anthropic Claude (or fallback LLM) to generate an answer.
- **Fallback:** If no relevant chunks are found, the app uses the LLM’s general knowledge.

---

## Environment Variables

The app sets API keys as environment variables internally, but you can also set them manually:

```sh
export OPENAI_API_KEY=your-openai-key
export ANTHROPIC_API_KEY=your-anthropic-key
export COHERE_API_KEY=your-cohere-key
```

---

## Dependencies

See [requirements.txt](requirements.txt) for the full list.

Key packages:
- `raglite` – Lightweight RAG framework
- `rerankers` – Reranking utilities
- `streamlit` – Web UI
- `anthropic`, `openai`, `cohere` – LLM and embedding APIs
- `sqlalchemy`, `psycopg2-binary` – Database support
- `pypdf` – PDF parsing
- `spacy`, `pydantic`, `python-dotenv` – NLP and configuration

---

## Troubleshooting

- **API Errors:** Ensure your API keys are correct and have sufficient quota.
- **Database Issues:** Check your database URL and permissions.
- **PDF Parsing:** Only PDF files are supported for upload.

---

## License

MIT License

---

## Acknowledgments

- [RAGLite](https://github.com/paulbricman/raglite)
- [Cohere](https://cohere.com/)
-
