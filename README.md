# RAG Chatbot — Dialogflow + OpenAI Integration

A webhook service for Dialogflow that uses the OpenAI API with Retrieval-Augmented Generation (RAG) to power an intelligent chatbot. Instead of generic responses, this chatbot retrieves relevant context from your data before generating answers — producing accurate, grounded responses.

## How It Works

```
User Query → Dialogflow Intent → Webhook → Document Retrieval → OpenAI LLM → Grounded Response
```

1. **User asks a question** through Dialogflow
2. **Webhook receives** the intent and extracts the query
3. **Retrieval layer** searches chunked documents using embeddings to find relevant context
4. **OpenAI API** generates a response grounded in the retrieved context
5. **User receives** an accurate, knowledge-based answer

## Architecture

```
├── chunks/          # Pre-chunked document data
│   └── chunks.json  # Chunked text for retrieval
├── data/            # Raw source documents
│   └── about_us.txt # Source knowledge base
├── embeddings/      # Vector embeddings for semantic search
├── chunks.js        # Document chunking logic
├── embed.js         # Embedding generation pipeline
├── index.js         # Main webhook server & RAG pipeline
├── package.json     # Dependencies
├── .env             # API keys (not tracked)
└── .gitignore
```

## Tech Stack

- **Runtime:** Node.js / JavaScript
- **LLM:** OpenAI API (GPT)
- **Chatbot Platform:** Dialogflow (webhook integration)
- **Retrieval:** Embedding-based semantic search
- **Data Processing:** Custom chunking and embedding pipeline

## Features

- Connects Dialogflow intents to a retrieval layer and LLM response pipeline
- Chunks source documents and generates embeddings for semantic search
- Retrieves relevant context before generation — reducing hallucination
- Webhook architecture for easy integration with Dialogflow
- Modular design: swap data sources, models, or platforms independently

## Setup

1. Clone the repository:
```bash
git clone https://github.com/Nebiyu-6249/rag-chatbot.git
cd rag-chatbot
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file with your API keys:
```
OPENAI_API_KEY=your_openai_key_here
```

4. Prepare your data:
```bash
node chunks.js    # Chunk your documents
node embed.js     # Generate embeddings
```

5. Start the webhook server:
```bash
node index.js
```

6. Connect to Dialogflow:
   - Set your webhook URL in Dialogflow fulfillment settings
   - Map intents to the webhook

## Use Cases

- Customer support chatbots grounded in company documentation
- Internal knowledge base assistants
- FAQ systems with accurate, context-aware responses
- Any chatbot that needs to answer from specific data sources

## Author

**Nebiyu Gemedu** — AI Developer | [GitHub](https://github.com/Nebiyu-6249)
