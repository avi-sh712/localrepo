# 🧠 Sidekick Agent (LangGraph)

A personal **agentic sidekick** built using **LangGraph** and **LangChain**, designed to assist with research, browsing, automation, and self-directed reasoning.  
This project is **actively under development** and currently optimized for **cost-effective experimentation** using lightweight LLMs.

---

## ✨ What is this project?

This Sidekick Agent is an **LLM-powered autonomous assistant** that can:
- Search the web
- Browse pages like a real user
- Execute Python code on its own
- Manage files
- Notify me proactively
- **Verify its own work** via a dedicated Reviewer Agent
- Interact via a simple frontend

All of this is orchestrated using **LangGraph**, enabling structured, multi-step agent workflows rather than simple prompt chains.

---

## 🤖 Agent Core
- **Framework:** Built with **LangGraph** for stateful orchestration.
- **Multi-Agent Logic:** Features a **Primary Agent** for task execution and a **Reviewer Agent** for verification.
- **Verification Layer:** The Reviewer Agent intercepts the final output, cross-references it with the initial query, and ensures the answer is accurate and complete before delivery.
- **Model:** Currently powered by **`gpt-4o-mini`** (flexible and cost-efficient).

---

## 📊 Output Gallery
Query	Sidekick Response	Reviewer Verdict	Evidence (Screen & Pushover)
"Find the latest price of BTC and check wikipedia for it"	"BTC is currently at $X..."	✅ Verified	<img src="https://github.com/user-attachments/assets/183c0703-d082-4a53-afe7-a758b6a5c397" width="400">
"Find an interesting topic on wikipedia and give me a brief intro"	"Introduction to Artificial Intelligence..."	✅ Verified	<img src="https://github.com/user-attachments/assets/56cfd2c8-5b9d-412e-86e1-101305548efb" width="400">
"List good hotels in NYC and send me pushover notifications"	"Found 5 top-rated hotels..."	✅ Verified	
<img src="https://github.com/user-attachments/assets/e9c47521-0bb8-428d-b51b-64edc25b66a0" width="400">


<img src="https://github.com/user-attachments/assets/2f03d026-4e68-44fc-bd45-187deb2ca490" width="180"> <img src="https://github.com/user-attachments/assets/f050b65e-6669-483a-bacc-ae1c429f12f0" width="180">

---

## 🧰 Tools Available to the Agent

The agent currently has access to the following tools:

- **🔔 Pushover Notification Tool**
  - Sends real-time personal notifications using a Pushover key
- **🌐 Google Search (Serper API)**
  - Fast, structured Google search results via Serper
- **🧭 Browser Automation**
  - Uses **Microsoft Playwright** (Chromium) for realistic web browsing
- **📚 Wikipedia Tool**
  - For factual lookups and background information
- **🐍 Python REPL Tool**
  - Allows the agent to execute Python code autonomously
- **📁 File Management System**
  - Enables reading, writing, and managing files as part of workflows

---

## 🖥️ Frontend
- Simple **Gradio UI**
- Enables direct interaction with the agent during development and testing

---

## ⚙️ Model Strategy
- **Default model:** GPT-4o-mini
- Designed to easily switch between cheaper models for testing and powerful models for advanced reasoning.

---

## 🧪 Under Active Development
- 📧 **Email Tool:** Send and read emails via the agent.
- 📄 **PDF Reader Tool:** Allow the agent to summarize and reason over PDFs.
- 🧠 **Automatic RAG Pipeline:** Build and update a retrieval knowledge base dynamically.
- 💾 **Long-Term Memory:** Persist context using `MemorySaver` checkpoints.
- 🔄 **Improved Routing:** Smarter decision-making between browsing, searching, or internal reasoning.

---

## 🛠️ Tech Stack
- **Python**
- **LangGraph** & **LangChain**
- **OpenAI API**
- **Gradio**
- **Playwright (Chromium)**
- **Serper API** & **Pushover**
- **uv** (Dependency management)

---

## 🔐 Environment Variables
This project relies on environment variables for secrets. A sample file is provided in `.env.example`.
