# 🧠 AI Interview Prep Coach (Mem0 + LangChain + Groq)

An AI-powered interview preparation coach that remembers candidate responses, strengths, and improvement areas across sessions using **Mem0**, **LangChain**, and **Groq**.

---

## 🚀 Features

- **Personalized Coaching**: Tailors interview questions and feedback dynamically based on prior interactions.
- **Cross-Session Memory**: Leverages [Mem0](https://github.com/mem0ai/mem0) and local Qdrant vector storage to persist conversation insights.
- **Fast Inference**: Uses Groq-hosted open LLMs (Qwen) via LangChain.
- **Interactive UI**: Clean chat interface powered by Streamlit.
- **Exploration Notebooks**: Includes Jupyter notebooks for testing memory extraction and retrieval.

---

## 🛠️ Project Structure

```text
├── app.py                  # Streamlit web application
├── memory_agent.py         # Core agent logic, Mem0 config & LangChain pipeline
├── notebooks/
│   └── experiments.ipynb   # Experimentation notebook
├── flow.excalidraw         # Architecture diagram
├── pyproject.toml          # Project dependencies and metadata
├── .env.example            # Environment variables template
└── .gitignore              # Git ignore configuration
```

---

## 📦 Setup & Installation

### 1. Clone the repository
```bash
git clone https://github.com/mayank4574/mem0.git
cd mem0
```

### 2. Install dependencies
Using `uv` (recommended):
```bash
uv sync
```
Or with standard `pip`:
```bash
pip install -e .
```

### 3. Configure Environment Variables
Copy `.env.example` to `.env` and fill in your API keys:
```bash
cp .env.example .env
```

Required keys in `.env`:
- `GROQ_API_KEY`: API key from [Groq Console](https://console.groq.com/)
- `GOOGLE_API_KEY` / `GEMINI_API_KEY`: API key from [Google AI Studio](https://aistudio.google.com/)

---

## 🖥️ Running the Application

Launch the Streamlit app:
```bash
streamlit run app.py
```

Open your browser at `http://localhost:8501`.
