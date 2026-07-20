# 💬 WhatsApp Business Automation Suite

![n8n](https://img.shields.io/badge/n8n-Workflow%20Automation-EA4B71) ![Claude](https://img.shields.io/badge/AI-Claude%20%2F%20OpenAI-D97757) ![WhatsApp](https://img.shields.io/badge/WhatsApp-Business%20API-25D366) ![Status](https://img.shields.io/badge/Status-Shipped-success)

**Clients:** Insight Analytics & retainer clients
**What it is:** A family of WhatsApp-first automations covering loan reminders + mobile-money collection, plain-text-to-invoice generation, and reply-only AI support bots — built so a business's WhatsApp Business number does the work a person would otherwise do by hand.

---

## 📸 Preview — reply-only AI support bot (n8n canvas)

![WhatsApp bot workflow](../assets/whatsapp-bot-workflow.png)

*Inbound message → type router (text / voice / image / PDF) → transcription & vision → AI Agent with memory → reply, with duplicate-webhook protection and owner error alerts.*

---

## 1. Loan reminders & mobile-money collection

Automated reminder sequence (7 / 3 / 1 / 0 days before due, then daily while overdue) sent on **both WhatsApp and SMS in parallel**, since not every borrower has WhatsApp — followed by automatic mobile-money collection attempts once a payment is due.

```mermaid
flowchart TD
    A[(Loans sheet)] --> B{Days to due date}
    B -->|7 / 3 / 1 / 0| C[Send WhatsApp template]
    B -->|7 / 3 / 1 / 0| D[Send SMS]
    C --> E[On due date: wait, re-check status]
    D --> E
    E -->|unpaid| F[Trigger mobile-money charge]
    F -->|success| G[Send payment receipt]
    F -->|fail, capped retries| H[Mark defaulted / alert lender]
```

- Dual-channel delivery so no borrower is unreachable
- Mobile-money collection via a payments API (charge → verify → reconcile)
- Partial payments supported; capped retry attempts before flagging default
- Full activity log for audit purposes

## 2. WhatsApp invoice creator

A client texts a plain-language request ("invoice John for 3 units at K150 each, 10% discount") and gets back a branded PDF invoice on WhatsApp within seconds.

```mermaid
flowchart LR
    A[WhatsApp text request] --> B[Claude parses line items]
    B --> C[Compute subtotal / discount / VAT / total]
    C --> D[Fill branded invoice template]
    D --> E[Export PDF]
    E --> F[Send back on WhatsApp]
    E --> G[(Log to sheet)]
    H[Daily 9am check] --> I[WhatsApp overdue clients]
```

## 3. Reply-only AI support bots

Channel-native AI agents that answer inbound WhatsApp / Messenger / Instagram messages (text, voice, image, document) within the platform's session window and log every conversation as a lead. Built with duplicate-webhook protection, retry + error alerting, and a single clean credential per channel.

## 🛠️ Stack

n8n · Claude / OpenAI · WhatsApp Business Cloud API · Twilio · Meta Graph API · SMS gateway · mobile-money payment APIs · Google Sheets

## Status

Multiple variants shipped and hardened across clients; live delivery on some channels is pending Meta business verification (a client-side compliance step, not a system limitation).
