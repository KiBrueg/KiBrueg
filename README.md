# AI Automation & Backend Engineer

Building AI-powered automation that ships to **production** — not tutorials. Python · n8n · Docker · LLMs.

<img src="https://github.com/user-attachments/assets/270bf26f-ed76-4cbf-bf1b-24ee9ea63ea1" width="640" alt="AI Automation Hub demo" />

💻 **Code & docs:** [AI Automation Hub](https://github.com/KiBrueg/n8n-automation)

![CI](https://github.com/KiBrueg/n8n-automation/actions/workflows/ci.yml/badge.svg)

---

## 🚀 AI Automation Hub

A modular AI-automation platform: **one engine, pluggable "modes" added by config — no code rewrite.**
Built with hard data contracts, switchable LLM providers, and full production ops (CI/CD, backups, monitoring).

### 🧩 System architecture

```mermaid
flowchart LR
    user([Channels: web / Telegram / email]) -->|HTTPS| caddy[Caddy<br/>reverse-proxy + TLS]
    caddy --> n8n[n8n<br/>orchestration]
    caddy --> gw[FastAPI gateway]
    caddy --> kuma[Uptime Kuma<br/>monitoring]
    n8n -->|/v1/process| gw
    gw --> llm[[LLM<br/>OpenRouter / Ollama]]
    gw --> pg[(PostgreSQL)]
    gh[GitHub Actions<br/>CI/CD] -->|build → GHCR → SSH deploy| caddy
```

### 🔄 Core n8n workflow

```mermaid
flowchart LR
    t[Webhook trigger] --> n[Normalize → ConversationEvent]
    n --> g[Gateway /v1/process<br/>PII sanitize → LLM → Decision]
    g --> s{escalate?}
    s -->|yes| h[Escalate to human]
    s -->|no| r[Respond to channel]
    g -. on error .-> e[Error handler / alert]
```

### ✅ What's inside
- 🐳 Full Docker stack: **n8n · FastAPI · PostgreSQL · Caddy (auto-HTTPS)**
- ⚙️ **Green CI** (ruff + tests) and **automated CD** — every push builds, pushes to GHCR and deploys to a live VPS
- 💾 Daily Postgres backups · 📊 uptime monitoring · 🔒 PII sanitizer before the LLM
- 🔌 Switchable LLM providers (OpenRouter / Ollama) and pluggable modes — **new product = new config, core untouched**

---

### 🛠️ Tech
`Python` · `FastAPI` · `Pydantic` · `n8n` · `Docker / Compose` · `PostgreSQL` · `Caddy / HTTPS` · `GitHub Actions (CI/CD)` · `LLM APIs` · `Linux / VPS`

### 🎯 Open to (remote)
**AI Automation Engineer · Junior Backend · AI Workflow Engineer · Junior Platform / DevOps**

### 📫 Connect
[LinkedIn](https://www.linkedin.com/in/ki-brueg-2520033bb) · [AI Automation Hub repo](https://github.com/KiBrueg/n8n-automation)
