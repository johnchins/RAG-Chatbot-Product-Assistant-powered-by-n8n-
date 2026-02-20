# n8n XYZ Product Assistant Chatbot (RAG + Pinecone)
![Screenshot 2026-02-20 231423](https://github.com/user-attachments/assets/6255558b-f814-4ed4-a0df-2702fab79cb0)
![Screenshot 2026-02-20 231523](https://github.com/user-attachments/assets/aa6175ae-bace-4985-bf3f-4115fb96e6ae)


🤖 **Intelligent customer-facing chatbot** for **XYZ** product and services information — built 100% with **n8n**.

Answers questions **strictly grounded** in official XYZ documentation stored in a Pinecone vector database (RAG pattern), collects high-intent leads into Google Sheets, remembers short conversation history, and provides an embeddable public chat interface.

Comes with two tightly coupled workflows:

1. Real-time chatbot (public-facing)
2. Automatic knowledge-base updater (Google Drive → Pinecone)

## ✨ Core Features

- **RAG architecture** — answers sourced exclusively from indexed XYZ manuals (no hallucinations, no external knowledge)
- **GPT-4o** reasoning + tool calling
- **12-message window memory** for natural multi-turn conversations
- **Lead capture** — name, email, phone, interest → appended to Google Sheet after product/hours/location questions
- **Automatic ingestion pipeline** — new or updated PDFs in Google Drive folder → chunked (500 chars) → embedded (OpenAI) → inserted into Pinecone
- **Public chat widget** — customizable title, placeholder, initial greeting, supports file uploads
- **Strong XYZ-positive persona** — proudly promotes XYZ strengths when asked

## Architecture at a glance
![Screenshot 2026-02-20 230856](https://github.com/user-attachments/assets/2d021bee-70bf-434c-a75c-32205e18f887)


## Included Workflows

| Filename                              | Purpose                              | Trigger                        | Key Action                                 |
|---------------------------------------|--------------------------------------|--------------------------------|--------------------------------------------|
| `RAG Chatbot Product Assistant (powered by n8n).json` | Customer-facing chatbot             | Chat message                   | RAG + memory + lead collection             |
| `Pinecone Workflow (feed data to Pinecone).json`      | Knowledge base updater              | File created in Drive folder   | PDF → chunks → embeddings → Pinecone upsert|


## 🛠️ Technologies / Services

- n8n (core orchestration + LangChain nodes)
- OpenAI (gpt-4o chat + text-embedding-ada-002 or similar)
- Pinecone (vector index: `XYZmanual`)
- Google Drive (source of XYZ product manuals & PDFs)
- Google Sheets (lead/contact storage)

## 🚀 Quick Setup Guide

1. Import both `.json` files into your n8n instance
2. Connect credentials:
   - OpenAI API key
   - Pinecone API key + index `XYZmanual`
   - Google Drive OAuth
   - Google Sheets OAuth
3. **Populate knowledge base** first:
   - Place current XYZ product manuals, brochures, FAQs (PDFs) into the watched Google Drive folder
   - Run "Pinecone Workflow" manually once (or wait for trigger)
4. **Activate chatbot**:
   - Customize system prompt / greeting if desired
   - Copy production webhook URL from "When chat message received" node
   - Embed the chat on website or share the link
5. Turn both workflows **active**

## Customization & Extension Ideas

- Replace chat trigger with WhatsApp / Telegram / Instagram / Facebook Messenger
- Add intent-based routing (e.g. branch to human support)
- Switch to cheaper/faster model (gpt-4o-mini, open-source via Groq / Together)
- Implement feedback collection → improve Pinecone re-ranking
- Add multi-language detection & translation layer
- Send real-time Slack/Email/WhatsApp alert on captured leads
- Use metadata filtering in Pinecone for versioned / product-specific answers

## ⚠️ Important Notes & Limitations

- Chatbot **must not** answer from general knowledge — system prompt enforces strict grounding
- Current Pinecone mode = `insert` (can create duplicates on re-upload → consider switching to upsert + metadata deduplication later)
- Lead capture only triggers after certain question types (opening hours, products, location, etc.)
- No rate limiting / abuse protection implemented yet — add if going public

## 📄 License

MIT — feel free to use, modify, fork. Attribution appreciated.

## ❤️ Show support

If this saves time building banking / financial-service chatbots — please ⭐ the repo!

Questions, improvements, or banking-specific forks → open an issue or PR.
