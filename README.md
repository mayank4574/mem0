# 🧠 AI Interview Prep Coach (Mem0 + LangChain + Groq)

An AI-powered interview preparation coach that remembers candidate responses, strengths, weaknesses, and target roles across multiple sessions using **Mem0**, **LangChain**, **Groq (Qwen)**, and **Google Gemini Embeddings**.

---

## 🌟 Key Features

- **Long-Term Memory Persistence**: Powered by [Mem0](https://github.com/mem0ai/mem0) and local Qdrant vector storage. The coach automatically extracts candidate facts and preserves them across sessions.
- **Personalized Coaching**: Adapts questions based on historical strengths and improvement areas rather than asking generic or repetitive questions.
- **Ultra-Fast LLM Inference**: Uses Groq-hosted open-source models (`qwen/qwen3.8-27b`) via LangChain for near-instant responses.
- **Semantic Search**: Embeds user interactions with Google Gemini Embeddings (`models/gemini-embedding-001`) to retrieve the most contextually relevant past feedback.
- **Interactive UI**: Built with Streamlit, featuring real-time chat, session user switching, memory inspection, and transcript controls.
- **Experimentation Suite**: Includes Jupyter notebooks (`notebooks/experiments.ipynb`) and architectural flows (`flow.excalidraw`).

---

## 🏗️ System Architecture

```text
┌─────────────────┐       User Prompt
│                 │ ──────────────────────┐
│  Streamlit UI   │                       ▼
│    (app.py)     │             ┌───────────────────┐
│                 │ ◄────────── │   Memory Agent    │
└─────────────────┘   Feedback  │ (memory_agent.py) │
                                └─────────┬─────────┘
                                          │
                  ┌───────────────────────┴───────────────────────┐
                  ▼                                               ▼
       ┌─────────────────────┐                         ┌─────────────────────┐
       │   Mem0 + Qdrant     │                         │  LangChain + Groq   │
       │ (Local Vector DB &  │ ── Past Candidate ──►   │ (Qwen 3.8 27B LLM   │
       │  Gemini Embeddings) │     Memories            │   Prompt Engine)    │
       └─────────────────────┘                         └─────────────────────┘
```

---

## 📂 Project Structure

```text
├── app.py                  # Streamlit web application interface
├── memory_agent.py         # Mem0 orchestration, Groq LLM chain & memory pipeline
├── notebooks/
│   └── experiments.ipynb   # Jupyter notebook for testing retrieval & extraction
├── flow.excalidraw         # Architecture diagram
├── pyproject.toml          # Project metadata and dependencies
├── .env.example            # Environment variables template
├── .gitignore              # Ignored files (secrets, runtime vector data, caches)
└── README.md               # Project documentation
```

---

## 🚀 Getting Started

### 1. Prerequisites

- Python `>= 3.12`
- API Keys:
  - **Groq API Key**: [Groq Console](https://console.groq.com/)
  - **Google Gemini API Key**: [Google AI Studio](https://aistudio.google.com/)

### 2. Clone the Repository

```bash
git clone https://github.com/mayank4574/mem0.git
cd mem0
```

### 3. Install Dependencies

Using [uv](https://github.com/astral-sh/uv) (recommended):
```bash
uv sync
```

Or using standard `pip`:
```bash
pip install -e .
```

### 4. Configure Environment Variables

Create a `.env` file from the provided `.env.example`:
```bash
cp .env.example .env
```

Open `.env` and add your API keys:
```env
GROQ_API_KEY=your_groq_api_key_here
GEMINI_API_KEY=your_gemini_api_key_here



---

## 🖥️ Usage

Run the Streamlit application:
```bash
streamlit run app.py
```

Open `http://localhost:8501` in your browser.

- Enter a **User ID** (e.g., `alice` or your name) in the sidebar to maintain a persistent persona.
- Begin practicing by stating your target role (e.g. *"I'm preparing for a Senior Backend Engineer role at a fintech company"*).
- Click **Show stored memories** in the sidebar to inspect the candidate profile facts that Mem0 automatically extracted and saved into Qdrant!

---

## 🛡️ Privacy & Excluded Files

The repository is configured to keep runtime vector storage and sensitive data private:
- Local database storage (`.mem0/`, `qdrant_data/`) is ignored by `.gitignore`.
- Secrets (`.env`, credentials) are strictly excluded from version control.
