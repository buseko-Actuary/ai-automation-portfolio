# 🤖 AI & Automation Portfolio

**Case studies from client automation systems built as the AI & Automation Specialist at Insight Analytics.**

![n8n](https://img.shields.io/badge/n8n-Workflow%20Automation-EA4B71) ![Claude](https://img.shields.io/badge/Claude-Anthropic%20API-D97757) ![Google](https://img.shields.io/badge/Google-Workspace%20API-4285F4) ![Location](https://img.shields.io/badge/Based%20in-Lusaka%2C%20Zambia-informational)

*Real, deployed/in-progress client systems — architecture and design write-ups only, not exported workflow files or client data.*

---

## 🇿🇲 Start here: a phone agent that answers in Nyanja, in my own voice

**You ring a Lusaka restaurant. A Zambian voice answers in Nyanja, quotes the price of nshima with T-bone, gives directions past Manda Hill, and books your table into a live calendar.**

**The voice is mine, cloned from 101 seconds of audio.**

Most voice AI assumes the caller speaks English, or one of about thirty well-resourced languages. Zambia has 72. This build closes that gap, and documents exactly where it still cannot be closed.

The finding that shaped it: **speaking a language and understanding it are separate problems.** ElevenLabs supports Chichewa, so the agent speaks Nyanja fluently. No mainstream speech-to-text supports Nyanja at all, so it cannot understand a word of it. The demo is designed around that honestly rather than pretending otherwise.

**→ [Read the build: Zam Eat Nyanja voice agent](projects/08-zam-eat-nyanja-voice-agent.md)**

Seven documented failures in there, including an agent that could not read its own replies, one that answered a price question by reciting the menu, and a transcriber tweak that made it say *"confirm your Mumba"* instead of *"number"*.

---

## ✨ Case studies

| Project | What it does | Client |
|---|---|---|
| 📄 [AI CV Screening](projects/01-ai-cv-screening-zega.md) | Automated resume ranking with scheduled PDF reports | Zega |
| 📊 [Excel → Executive Dashboard → PDF](projects/02-excel-to-dashboard-reporting.md) | Self-service reporting pipeline | Insight Analytics |
| 💬 [WhatsApp Business Automation Suite](projects/03-whatsapp-business-automation-suite.md) | Reminders, collections, invoicing, support bots | Insight Analytics & clients |

> 📊 Looking for the Excel/VBA business systems (HR compliance matrix, fleet management)? They now live in their own repo: **[Excel-Business-Systems](https://github.com/buseko-Actuary/Excel-Business-Systems)**.

## 🛠️ Stack across these projects

`n8n` · `Claude (Anthropic API)` · `OpenAI` · `Pinecone (vector database)` · `Google Workspace API` · `WhatsApp Business Cloud API` · `Meta Graph API` · `PDF generation`

---

## 🌱 Where it started

Before any of the above, there was one small workflow that started everything — and unlike the client work, **it's fully open and free to import:**

| Project | What it does | |
|---|---|---|
| 🌱 [My First Workflow — Tax Status Notifier](projects/00-first-workflow-tax-status.md) | Form → Google Sheet → conditional logic → automated email | ⬇️ [Downloadable](workflows/tax-status-first-workflow.json) |

## 🔎 Open experiments

Personal builds exploring new tools. The write-ups cover the architecture and every failure; some include the workflow file, the voice agents do not.

| Project | What it does | |
|---|---|---|
| 🇿🇲 [Zam Eat Nyanja Voice Agent](projects/08-zam-eat-nyanja-voice-agent.md) | A restaurant phone agent that answers in Nyanja using my own cloned voice. Books real tables into a live calendar. Seven documented failures, including why the model could not read its own replies | 📖 Write-up only |
| ☎️ [Insight Dentist Voice Agent](projects/07-insight-dentist-voice-agent.md) | A real phone call books a real appointment. Vapi + GPT-4o answers, reads the live calendar, books it, logs it and sends a confirmation SMS. Eight documented failures, including an agent that confidently booked a date in 2023 | 📖 Write-up only |
| 📼 [YouTube to Markdown](projects/06-youtube-transcript-to-markdown.md) | Paste a YouTube link into a Google Sheet, get a clean markdown transcript in Drive, ready to hand to an AI assistant. Every failure reason written back to the row | ⬇️ [Downloadable](workflows/youtube-transcript-to-markdown.json) |
| 🧠 [WhatsApp RAG Agent](projects/05-whatsapp-rag-agent.md) | Drop a document in Google Drive, ask about it on WhatsApp. Pinecone vector store + OpenAI embeddings, retrieval wired to the agent as a tool | ⬇️ [Downloadable](workflows/whatsapp-rag-agent.json) |
| 🔎 [AI Research & Content Engine](projects/04-ai-research-content-engine.md) | Tavily live web search + OpenAI synthesis, queued and delivered through a Google Sheet | ⬇️ [Downloadable](workflows/ai-research-content-engine.json) |

---
Co-Founder & AI/Automation Specialist — [Insight Analytics](https://github.com/buseko-Actuary)
