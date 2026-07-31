<!-- SEO Meta: AI email automation agent n8n Gmail workflow automation Bangladesh AutomateIQ Labs Gemini Groq dual-AI email responder sentiment detection OCR attachment processing prompt injection protection -->

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=160&section=header&text=Universal%20Email%20Agent&fontSize=38&fontColor=fff&animation=twinkling&fontAlignY=35&desc=Production-Grade%20AI%20Email%20Automation%20%7C%20n8n%20%2B%20Gemini%20%2B%20Groq&descAlignY=58&descAlign=50" width="100%"/>

[![n8n](https://img.shields.io/badge/n8n-2.25.7+-EA4B71?style=for-the-badge&logo=n8n&logoColor=white)](https://n8n.io)
[![Gemini](https://img.shields.io/badge/Gemini_2.0_Flash-4285F4?style=for-the-badge&logo=google&logoColor=white)](https://ai.google.dev)
[![Groq](https://img.shields.io/badge/Groq_Llama_3.3-F55036?style=for-the-badge&logoColor=white)](https://groq.com)
[![Gmail](https://img.shields.io/badge/Gmail_API-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](https://developers.google.com/gmail)
[![Self-Hosted](https://img.shields.io/badge/Self--Hosted-00B894?style=for-the-badge&logo=docker&logoColor=white)](https://docs.n8n.io/hosting/)
[![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](LICENSE)

<br/>

> **🤖 An intelligent, production-ready email automation agent that reads, classifies, and responds to every email — automatically.**

</div>

---

## 📌 What Is This?

**Universal Email Agent** is a fully automated, AI-powered email handling system built on **self-hosted n8n**. It connects to your Gmail inbox, processes every incoming email through a multi-layer AI pipeline, and handles responses — without any human involvement.

Built by **[Muhammad Antor](https://www.linkedin.com/in/muhammad-antor)** | [AutomateIQ Labs](https://www.facebook.com/automateiq.labs/)

---

## ⚡ Key Features

| Feature | Description |
|---|---|
| 🧠 **Dual-AI Brain** | Gemini 2.0 Flash (primary) + Groq Llama 3.3 (fallback) work together |
| 📎 **OCR on Attachments** | Reads and extracts content from PDF, image attachments via AI |
| 💬 **Smart Classification** | Categorizes every email: Spam / Urgent / Support / Inquiry / Partnership |
| 😤 **Sentiment Detection** | Detects frustrated or angry tone — auto-escalates to admin |
| 🛡️ **Prompt Injection Protection** | Blocks malicious emails attempting to manipulate the AI |
| 🔄 **Knowledge Base Cache** | Reads from Google Docs KB — cached hourly for performance |
| 📊 **Confidence Scoring** | High confidence → auto-reply. Low confidence → admin draft suggestion |
| 📋 **Full Audit Log** | Every email logged to Google Sheets with category, sentiment & confidence |
| 💀 **Dead Letter Queue** | Failed emails captured, logged & admin alerted via Telegram |
| 🔁 **Deduplication** | "AI-Processed" Gmail label prevents any email from being processed twice |
| 📱 **Telegram Notifications** | Real-time admin alerts for urgent emails, errors & low-confidence drafts |
| 🏠 **100% Self-Hosted** | Runs entirely on your own server — your data never leaves your infrastructure |

---

## 🏗️ System Architecture

### High-Level Flow

```
📧 Email Arrives
      ↓
📚 Knowledge Base Load (cache → Google Docs)
      ↓
🛡️ Security Layer (sanitize + injection check)
      ↓
📎 Attachment? ──YES──→ OCR Extract → AI Classify
      │
      NO
      ↓
🧠 AI Classify (category + sentiment + confidence)
      ↓
┌─────────────────────────────────┐
│         Category Router         │
├──────────┬──────────┬───────────┤
│  🚫 SPAM │ ⚡URGENT │ 💬 REPLY  │
│   Drop   │Telegram  │  Generate │
│          │  Alert   │ + Validate│
└──────────┴──────────┴───────────┘
      ↓
High Confidence → Auto Reply
Low Confidence  → Ack + Admin Draft Alert
      ↓
✅ Mark Read + Label + Log to Sheets

⚠️ Any Failure → Dead Letter Queue → Telegram Error Alert
```

### Architecture Diagram

![System Architecture](email_agent_architecture.png)

### Layer Overview

| Layer | Function |
|---|---|
| **L1 — Input** | Gmail trigger, polls every minute for unread emails |
| **L2 — KB Cache** | Loads knowledge base from Google Docs with 1-hour cache |
| **L3 — Security** | Input sanitization + prompt injection detection |
| **L4 — Routing** | Detects attachment presence and routes accordingly |
| **L5A — OCR Path** | AI-powered text extraction from attachments |
| **L5B — Text Path** | Direct processing for plain-text emails |
| **L6 — AI Brain** | Dual-AI classification + sentiment + confidence scoring |
| **L7 — Category Router** | Routes to Spam / Urgent / Reply Generator |
| **L8 — Output** | Auto-reply or admin alert based on confidence |
| **L9 — Finalize** | Mark as read, apply label, log to Google Sheets |
| **L10 — Error** | Dead Letter Queue + error logging + Telegram alert |

**Total: 46 nodes across 10 layers + sub-models**

---

## 🛠️ Tech Stack

### Automation Platform
![n8n](https://img.shields.io/badge/n8n-EA4B71?style=flat-square&logo=n8n&logoColor=white) Self-hosted, Docker · Version 2.25.7+

### AI / LLM Models
![Gemini](https://img.shields.io/badge/Gemini_2.0_Flash-4285F4?style=flat-square&logo=google&logoColor=white) Primary AI brain  
![Groq](https://img.shields.io/badge/Groq_Llama_3.3_70b-F55036?style=flat-square) Fallback AI model + speed layer

### Integrations
![Gmail](https://img.shields.io/badge/Gmail_API-EA4335?style=flat-square&logo=gmail&logoColor=white)
![Google Docs](https://img.shields.io/badge/Google_Docs-4285F4?style=flat-square&logo=googledocs&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google_Sheets-34A853?style=flat-square&logo=googlesheets&logoColor=white)
![Telegram](https://img.shields.io/badge/Telegram_Bot-26A5E4?style=flat-square&logo=telegram&logoColor=white)

---

## 📋 Prerequisites

Before setup, you need the following accounts and services:

| Service | Purpose | Cost |
|---|---|---|
| n8n (self-hosted) | Workflow engine | Free |
| Google Gemini API | Primary AI model | Free tier available |
| Groq API | Fallback AI model | Free tier |
| Gmail Account | Email monitoring | Free |
| Google Docs | Knowledge Base | Free |
| Google Sheets | Email audit log | Free |
| Google Cloud Service Account | Docs + Sheets auth | Free |
| Telegram Bot | Admin notifications | Free |
| Docker | n8n hosting | Free |

---

## 🚀 Setup Overview

### Step 1 — Deploy n8n

Host n8n using Docker. Required environment variable:
```bash
N8N_SKIP_AUTH_ON_OAUTH_CALLBACK=true
```
> This is critical for Gmail OAuth to work correctly.

### Step 2 — Configure Credentials

Set up the following credentials in n8n:
- **Gmail OAuth2** — with full Gmail scope
- **Google Service Account** — for Docs & Sheets access
- **Google Gemini API** — AI Studio key
- **Groq API** — from console.groq.com
- **Telegram Bot** — from @BotFather

### Step 3 — Prepare Google Services

1. **Knowledge Base** — Create a Google Doc with your business information, FAQs, and tone guidelines. Share with your Service Account.
2. **Email Log Sheet** — Create a Google Sheet with two tabs: `Email Log` and `Failed Emails`. Share with your Service Account as **Editor**.
3. **Gmail Label** — Create an `AI-Processed` label in Gmail. Note the Label ID.

### Step 4 — Import & Configure Workflow

1. Import the n8n workflow JSON
2. Connect all credentials to their respective nodes
3. Update the following in the workflow:
   - Google Doc URL (Knowledge Base)
   - Google Sheets ID
   - Telegram Chat ID
   - Gmail Label ID

### Step 5 — Activate

Toggle the workflow from **Inactive → Active**.

---

## 🧪 Testing Scenarios

Use these test cases to verify your setup:

| Test | How | Expected Result |
|---|---|---|
| **Basic email** | Send a simple inquiry email | Classified → auto-replied → logged in Sheets |
| **Urgent detection** | Send email with frustrated/angry tone | Escalated → Telegram alert → ack reply |
| **Attachment (PDF)** | Send email with PDF attached | OCR extracted → classified → replied |
| **Prompt injection** | Send `"Ignore previous instructions..."` | Blocked → marked as read → no reply |
| **Unsupported file** | Attach .mp3 or .mp4 | Auto-reply: unsupported file type |
| **Duplicate email** | Forward a processed email | No trigger (AI-Processed label blocks it) |
| **Spam** | Send obvious spam | Silent drop → marked as read |

---

## 📊 Email Categories

| Category | Detection Logic | Action |
|---|---|---|
| **Spam** | AI confidence + pattern | Silent drop + mark as read |
| **Urgent** | Keywords + angry/frustrated sentiment | Ack reply + Telegram alert |
| **Support** | Help/issue-related content | AI reply from Knowledge Base |
| **Inquiry** | Questions about services/pricing | AI reply from Knowledge Base |
| **Partnership** | Collaboration/business proposals | AI reply from Knowledge Base |

---

## 🔒 Security Features

- **Prompt Injection Detection** — Email content is scanned for AI manipulation attempts before any AI processing
- **Input Sanitization** — All email content is cleaned before entering the AI pipeline
- **Self-Hosted** — 100% on your own infrastructure. No third-party email data exposure
- **Deduplication** — Processed emails are labeled to prevent double-processing

---

## 📈 Why This Architecture?

| Design Choice | Reason |
|---|---|
| Dual AI (Gemini + Groq) | Redundancy + speed. Groq handles high-speed tasks, Gemini handles complex reasoning |
| KB Cache (1hr) | Reduces Google Docs API calls dramatically |
| Confidence Scoring | Prevents bad AI replies from being sent automatically |
| Dead Letter Queue | Zero email loss — every failure is captured and alerted |
| Self-hosted n8n | Full data ownership. No SaaS email data sharing |

---

## 🗺️ Roadmap

- [ ] Multi-inbox support (multiple Gmail accounts)
- [ ] Multilingual reply support (Bangla + English)
- [ ] Web dashboard for email analytics
- [ ] SaaS version — plug in your credentials & run
- [ ] WhatsApp notification support
- [ ] CRM integration (auto-create leads from emails)

---

## 👨‍💻 About The Builder

**Muhammad Antor** — AI Automation Engineer | Founder of AutomateIQ Labs

I build production-grade AI automation systems that eliminate manual business work.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/muhammad-antor)
[![Facebook](https://img.shields.io/badge/AutomateIQ_Labs-Follow-1877F2?style=flat-square&logo=facebook)](https://www.facebook.com/automateiq.labs/)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=flat-square&logo=github)](https://github.com/muhammadantor)
[![Email](https://img.shields.io/badge/Hire_Me-EA4335?style=flat-square&logo=gmail)](mailto:muhammadantor71@gmail.com)

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

---

<div align="center">

*Built with ❤️ by [AutomateIQ Labs](https://www.facebook.com/automateiq.labs/) · Bangladesh*

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=80&section=footer" width="100%"/>

</div>

<!-- 
SEO Keywords: AI email automation n8n, Gmail automation workflow, email responder agent, 
n8n email bot, AI email agent Bangladesh, AutomateIQ Labs, Gemini email automation,
workflow automation engineer, n8n Groq integration, self-hosted email agent,
email classification AI, sentiment detection email, prompt injection protection n8n
-->
