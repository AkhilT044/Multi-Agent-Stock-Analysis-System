
# 🤖 AI Hedge Fund Manager (Autonomous Multi-Agent System)

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://multi-agent-stock-analysis-system-ib22heed3d7ht3xdxsjwuz.streamlit.app/)
![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Gemini](https://img.shields.io/badge/AI-Google%20Gemini%201.5-orange)

**A professional-grade Multi-Agent System that acts as an autonomous financial analyst.** This project orchestrates a team of AI Agents—a Technical Analyst, a News Journalist, and a Chief Investment Officer (Supervisor)—to analyze real-time stock market data and generate investment decisions.

## 🔴 LIVE DEMO
### 👉 [Click Here to Launch the App](https://multi-agent-stock-analysis-system-ib22heed3d7ht3xdxsjwuz.streamlit.app/)
*(Note: The app supports BYOK (Bring Your Own Key) for security. If you don't have a key, it runs in Simulation Mode to demonstrate functionality.)*

---

## 🧠 The Architecture (How it Works)

This system is not just a chatbot. It is an **Agentic Workflow** built on the **"Boardroom Pattern"**:

### 1. The Workforce (Specialist Agents)
Instead of one general AI doing everything, we split the logic into specialized roles to prevent hallucinations and increase accuracy.

* **📊 Agent A: The Quantitative Analyst ("The Quant")**
    * **Role:** Mathematics & Trends.
    * **Tools:** Fetches raw price data via `yfinance` (Open, Close, Moving Averages).
    * **Logic:** Analyzes volatility, percentage changes, and price momentum. It effectively ignores news to remain objective.
* **📰 Agent B: The Financial Journalist ("The Sentiment Scout")**
    * **Role:** Sentiment & Context.
    * **Tools:** Fetches live news headlines via `yfinance`.
    * **Logic:** Reads headlines to determine market mood (Fear vs. Greed). It effectively ignores charts to focus on the narrative.

### 2. The Supervisor (Decision Maker)
* **👔 Agent C: The Chief Investment Officer (CIO)**
    * **Role:** Synthesis & Final Decision.
    * **Mechanism:** Uses **A2A (Agent-to-Agent) Communication**. The CIO receives the conflicting reports from the Quant and the Journalist.
    * **Logic:** "If Technicals say BUY but News says PENDING LAWSUIT, override to HOLD." It applies high-level reasoning to resolve conflicts.

### 3. Fault Tolerance (Crash-Proofing)
* **Simulation Fallback:** If the Google Gemini API hits a rate limit (429 Error), the system automatically switches to a "Simulation Mode," generating mock data to ensure the application UI never crashes during a presentation.

---

## 🛠️ Tech Stack

* **Brain:** `google-genai` (Gemini 1.5 Flash) - Chosen for high speed and low latency.
* **Frontend:** `Streamlit` - For a responsive, interactive web dashboard.
* **Data Feed:** `yfinance` - Real-time stock market data and news.
* **Orchestration:** Custom Python Agent Classes (State Management & Retry Logic).
* **Notifications:** `smtplib` - Real-time email alert system using Gmail SMTP.

---

## 📂 Project Structure

```bash
AI-Hedge-Fund/
├── capstone.ipynb        # experimenting the process and logics before the main application
├── app.py                # The Main Application (Logic + UI)
├── requirements.txt      # Dependencies for Cloud Deployment
└── README.md             # Documentation
