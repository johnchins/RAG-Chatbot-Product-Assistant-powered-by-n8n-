# XYZ Product Assistant Chatbot (RAG + Pinecone)
![Screenshot 2026-02-20 231423](https://github.com/user-attachments/assets/6255558b-f814-4ed4-a0df-2702fab79cb0)
![Screenshot 2026-02-20 231523](https://github.com/user-attachments/assets/aa6175ae-bace-4985-bf3f-4115fb96e6ae)

---

## 🚀 Executive Summary

This project demonstrates a fully orchestrated AI knowledge system using RAG architecture.

The system:

- Monitors Google Drive for new product documents
- Automatically downloads and processes files
- Splits documents into optimized chunks
- Generates OpenAI embeddings
- Stores vectors in Pinecone
- Powers a contextual AI chatbot
- Maintains memory across conversations
- Uses tools to retrieve accurate answers
- Captures customer leads automatically into Google Sheets

This replicates how modern AI SaaS assistants and enterprise knowledge bots are built.

---

## 🏗️ System Architecture Overview

### Architecture Layer 1: Knowledge Ingestion Pipeline

```
        ┌──────────────────────────┐
        │ Google Drive Trigger     │
        │ (New Document Added)     │
        └────────────┬─────────────┘
                     ↓
        ┌──────────────────────────┐
        │ Download Document        │
        └────────────┬─────────────┘
                     ↓
        ┌──────────────────────────┐
        │ Recursive Text Splitter  │
        │ (Chunk: 500 | Overlap:20)│
        └────────────┬─────────────┘
                     ↓
        ┌──────────────────────────┐
        │ OpenAI Embeddings        │
        └────────────┬─────────────┘
                     ↓
        ┌──────────────────────────┐
        │ Pinecone Vector Store    │
        │ (Index: ubamanual)       │
        └──────────────────────────┘
```

---

### Architecture Layer 2: RAG Chatbot Layer

```
        ┌──────────────────────────────┐
        │ Public Chat Trigger (UI)     │
        └────────────┬─────────────────┘
                     ↓
        ┌──────────────────────────────┐
        │ AI Agent                     │
        │ - Tool Use Enabled           │
        │ - System Instructions        │
        └────────────┬─────────────────┘
                     ↓
        ┌──────────────────────────────┐
        │ Memory Buffer (Window = 12)  │
        └────────────┬─────────────────┘
                     ↓
        ┌──────────────────────────────┐
        │ Pinecone Vector Retrieval    │
        └────────────┬─────────────────┘
                     ↓
        ┌──────────────────────────────┐
        │ OpenAI Chat Model (gpt-4o)   │
        └────────────┬─────────────────┘
                     ↓
        ┌──────────────────────────────┐
        │ Google Sheets Lead Capture   │
        └──────────────────────────────┘
```

---

## ⚙️ Workflow Breakdown

---

### 1️⃣ Automated Knowledge Ingestion

#### Trigger:
- Google Drive folder monitoring
- Activates when new file is created

#### Process:
- File is downloaded automatically
- Binary document loaded
- Recursive character splitting applied:
  - Chunk size: 500
  - Overlap: 20
- Embeddings generated using OpenAI
- Vectors stored inside Pinecone index

#### Result:
Fully automated knowledge base indexing pipeline.

---

### 2️⃣ Vector Database (Pinecone)

- Stores semantic embeddings
- Enables similarity search
- Returns relevant document chunks for each query
- Ensures contextual answers instead of hallucinations

This mimics production AI retrieval systems.

---

### 3️⃣ AI Agent Orchestration

The AI Agent:

- Uses GPT-4o
- Has system-level behavioral instructions
- Uses Pinecone as a retrieval tool
- Uses Google Sheets as a lead capture tool
- Maintains conversation memory (12-message window)

Demonstrates advanced tool-using LLM architecture.

---

### 4️⃣ Conversational Memory

Window Buffer Memory:

- Stores last 12 exchanges
- Enables contextual follow-ups
- Maintains coherent multi-turn conversation
- Simulates real AI assistant behavior

---

### 5️⃣ Lead Capture Automation

When users inquire about:

- Products
- Opening hours
- Location
- Services

The agent:

- Asks for name
- Asks for email
- Asks for phone
- Asks for interest

Data is appended automatically into Google Sheets via tool integration.

This transforms the chatbot into a business asset, not just a demo bot.

---

## 🧠 Core Technologies Used

- n8n (AI Workflow Orchestration)
- OpenAI GPT-4o (LLM)
- OpenAI Embeddings API
- Pinecone (Vector Database)
- Google Drive API
- Google Sheets API
- Recursive Text Splitting
- Agent Tool Architecture
- Retrieval-Augmented Generation (RAG)

---

## 🎯 Real-World Use Cases

- SaaS Product Assistant
- Bank Knowledge Assistant
- Internal Company Knowledge Bot
- E-commerce Product Q&A
- Customer Support Automation
- AI-powered FAQ Systems
- Lead Qualification Assistant

---

## 💼 Portfolio Case Study (Recruiter Focused)

### Problem

Traditional chatbots:

- Hallucinate information
- Lack contextual memory
- Cannot access private documents
- Do not generate structured business value

Businesses need intelligent, document-aware AI systems.

---

### Solution

Designed and deployed a RAG-based AI assistant that:

- Automatically ingests and indexes documents
- Retrieves only relevant knowledge
- Uses LLM reasoning over retrieved context
- Maintains conversation memory
- Captures structured leads automatically
- Scales via vector database architecture

---

### Technical Strengths Demonstrated

- End-to-end RAG pipeline engineering
- Vector database integration
- Embedding architecture design
- Chunking strategy optimization
- AI agent tool orchestration
- Prompt engineering with system constraints
- Multi-API workflow integration
- Production-style automation architecture

---

## 📊 Business Impact

- Eliminates manual FAQ maintenance
- Reduces customer support load
- Prevents hallucinated responses
- Enables knowledge-based AI
- Converts conversations into leads
- Creates scalable AI knowledge infrastructure

---

## 🏢 Enterprise Positioning

This system can serve as:

- AI knowledge backend for fintech
- Enterprise internal knowledge assistant
- SaaS customer onboarding bot
- Product documentation chatbot
- Sales pre-qualification assistant

Easily extendable to:

- Multiple knowledge bases
- Multi-tenant SaaS deployments
- CRM integration
- Slack / WhatsApp integration
- Web widget embedding

---

## 🧩 Skills Demonstrated

- AI System Architecture
- RAG Engineering
- Vector Search Optimization
- LLM Tool Usage Design
- Automation Engineering
- API Integrations
- Data Pipeline Construction
- Scalable AI Workflow Design

