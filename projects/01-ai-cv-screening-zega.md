# 📄 AI CV Screening — Zega

![n8n](https://img.shields.io/badge/n8n-Workflow%20Automation-EA4B71) ![Claude](https://img.shields.io/badge/AI-Claude%20%2F%20OpenAI-D97757) ![Google](https://img.shields.io/badge/Google-Drive%20%2F%20Sheets%20%2F%20Gmail-4285F4) ![Status](https://img.shields.io/badge/Status-Go--live%20prep-yellow)

**Client:** Zega
**What it is:** An automated resume-screening pipeline that ingests applications by email, ranks candidates per role using an AI agent, and archives a scheduled PDF shortlist report — no manual CV reading required to get to a shortlist.

---

## 📸 Preview — screening workflow (n8n canvas)

![AI CV Screening workflow](../assets/cv-screening-workflow.png)

*Intake (Gmail) → attachment picker → Drive upload → text extraction (PDF / Word / TXT) → role match → Recruiter Agent scoring → Candidates sheet, with a companion scheduled per-role PDF report flow below.*

---

## 🎯 The problem

HR was manually opening every CV emailed in against open roles, reading each one, and building shortlists by hand — slow, inconsistent, and hard to scale once multiple roles were open at once.

## 🔍 What it does

```mermaid
flowchart TD
    A[Gmail trigger — CV submission email] --> B[Pick best attachment]
    B --> C[Upload to Drive]
    C --> D[Extract text — PDF / Word / TXT]
    D --> E[Match role from email subject line]
    E --> F[AI screening agent — structured scoring]
    F --> G[(Candidates sheet — one row per applicant)]

    H[Daily cron 07:00] --> I[Read Candidates]
    I --> J[Group by role]
    J --> K[Rank per role]
    K --> L[Build styled HTML report]
    L --> M[Render to PDF]
    M --> N[(Archived to Drive — Reports folder)]
```

**Key design choices:**
- **Role matching from the subject line** using longest-match against a job-requirements sheet, so "Senior Data Analyst" doesn't get mis-matched to a generic "Analyst" posting.
- **Concurrency-safe by design** — applications are processed one at a time through a batched loop so simultaneous submissions can't overwrite each other.
- **Per-job ranking**, not a global score — a candidate is ranked against others applying for the *same* role, computed live off the sheet.
- **Reports, not raw data, go out** — the daily scheduled job only archives a formatted PDF shortlist (Shortlist / Maybe candidates), not the underlying spreadsheet.

## 🛠️ Stack

n8n · Claude / OpenAI · Gmail · Google Drive & Sheets · PDF rendering

## Status

Built and in go-live preparation.
