# 🟡 Goldsmith RAG Chatbot using n8n, Pinecone, OpenAI & Google Drive

> 🔗 **[Click here to use the chatbot](https://nithishkaranam2002.app.n8n.cloud/webhook/e6977065-e5be-4436-9585-7c3a95049d32/chat)**  
> Start chatting with your custom AI assistant built on top of your documents!

---

## 📌 Overview

This project is a **Retrieval-Augmented Generation (RAG)** system built using [n8n](https://n8n.io/), integrated with:

- **Google Drive** – to upload `.txt` files containing knowledge.
- **OpenAI** – for embeddings and response generation.
- **Pinecone** – as a vector store for document retrieval.
- **Google Sheets** – to log user interactions.
- **n8n Webhook Chat Interface** – for real-time AI chatbot experience.

It enables a jewelry business (Goldsmith) to serve customers with an AI chatbot that answers queries based on uploaded knowledge such as product lines, Q&A, etc.

---

## 🧠 How It Works

### 🔁 Workflow 1: Document Upload → Vector Store

📂 **Trigger**: Google Drive folder (`Rag App`)  
When a `.txt` file is uploaded:

1. **Google Drive Trigger**: Detects new file in `Rag App` folder.
2. **Download File**: Fetches the uploaded `.txt` file.
3. **Split Text**: Uses `Recursive Character Text Splitter` to chunk the text.
4. **Generate Embeddings**: Sends chunks to `OpenAI Embeddings`.
5. **Store in Pinecone**: Uploads the vectorized chunks into the Pinecone Vector DB.

📁 Sample knowledge files:
- `Gold Digger – Q&A.txt`
- `Product Line.txt`

---

### 💬 Workflow 2: User Chat → AI Response

📩 **Trigger**: User sends a message to the webhook chat.

1. **Webhook Trigger**: `When chat message received`
2. **AI Agent**: 
   - Pulls context from memory (via `Simple Memory`)
   - Retrieves relevant chunks using `goldsmith_q` (RAG tool)
3. **OpenAI Chat Model**: Generates a natural language response.
4. **Google Sheets**: Logs `name`, `phone`, `email`, and query for CRM/follow-up.

✅ **Response is returned instantly to the user via webhook chat.**

---

## 🗂 Project Structure

🚀 Try It Live

👉 Click to start chatting

📨 Example input:

name:Nithish
phone:9897865741
email:nithish@gmail.com
I am interested in gold rings.
🧠 The chatbot will retrieve answers from the knowledge base stored in Pinecone and respond appropriately using OpenAI.
