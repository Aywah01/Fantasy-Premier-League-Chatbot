# Fantasy Premier League Chatbot

A Flask-based chatbot powered by **Ollama Llama3.1** that answers user questions
within a configurable topic domain, with full conversation history support.

---

## 📁 Project Structure

```
ollama_code_FPL/ollama/
├── app.py                  # Flask backend
├── myfile.txt              # System prompt & key topic config
└── templates/
    └── chatbot.html        # Frontend UI
```

---

## ✨ Features

- **Topic-scoped responses** – A key topic is loaded from `myfile.txt` and automatically prepended to every user message, keeping the bot focused
- **Chat history** – Full conversation context is maintained per session so the bot gives coherent, context-aware replies
- **System prompt via text file** – Bot behavior and knowledge are configured through a plain `.txt` file, no code changes needed
- **Simple web UI** – Type a message and press Enter or click Send; the active key topic is displayed at the top

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend | Python, Flask |
| AI Model | Ollama Llama3.1 |
| Frontend | HTML, CSS, Vanilla JS |
| Config | Plain text file (`myfile.txt`) |

---

## 🚀 Getting Started

### Prerequisites

- Python 3.x
- [Ollama](https://ollama.com) installed and running locally
- Llama3.1 model pulled: `ollama pull llama3.1`

### Installation

```bash
git clone https://github.com/Aywah01/Fantasy-Premier-League-Chatbot.git
cd Fantasy-Premier-League-Chatbot/ollama_code_FPL/ollama

pip install flask ollama
```

### Configuration

Edit `myfile.txt` to set the chatbot's topic and system knowledge:

```
대표키워드:YOUR TOPIC HERE
(system knowledge lines follow...)
```

The first line's value after `대표키워드:` becomes the active key topic shown in the UI
and prepended to every user query.

### Running

```bash
python app.py
```

Then open `http://localhost:5000` in your browser.

---

## 🔌 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/` | Serves the chat UI |
| `GET` | `/keytopic` | Returns the current key topic as JSON |
| `POST` | `/chat` | Accepts `{ "message": "..." }`, returns `{ "message": "..." }` |

---

## 💬 Example

With `myfile.txt` configured for FPL:

> **You:** Who should I captain this week?  
> **Bot:** Based on current fixtures and form, here are my suggestions...

---

## ⚠️ Notes

- Chat history is stored **in memory** — it resets when the server restarts
- The bot will not respond to violent or political topics (enforced via system prompt in `myfile.txt`)
