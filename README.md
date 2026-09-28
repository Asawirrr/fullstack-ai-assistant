# AI Assistant — Full Stack

A production-ready full-stack AI chat application. It supports **Cloud AI models** (Google Gemini, OpenAI, Anthropic, xAI Grok, Meta Llama) as well as **Local Ollama models** (Gemma 4, Gemma 3, Llama 3.2, Qwen).

```
chatbot/
├── backend/    FastAPI · Python 3.13 · uv · Ruff · pytest · Ollama SDK · Cloud AI SDKs
└── frontend/   Next.js 16 · React 19 · TypeScript 7 · Tailwind CSS 4 · shadcn/ui
```

---

## Quick Start

**Prerequisites:** Python 3.12+ (uv automatically manages Python 3.13), Node.js 20.9+, and optionally [Ollama](https://ollama.com).

### 1. Configure Cloud AI (Recommended)
Add your free Google Gemini API key or any cloud API key to `backend/.env`:
```env
GEMINI_API_KEY=your_gemini_api_key_here
GEMINI_MODEL=gemini-2.5-flash
```
*(Get a free key from [Google AI Studio](https://aistudio.google.com/)).*

### 2. Run Backend (`port 8000`)
```bash
cd backend
uv sync
uv run uvicorn app.main:app --reload --port 8000
```
> API docs are live at [http://localhost:8000/docs](http://localhost:8000/docs).

### 3. Run Frontend (`port 3000`)
```bash
cd frontend
npm install
npm run dev
```
> Open [http://localhost:3000](http://localhost:3000) in your browser to start chatting.

### 4. Optional: Run Local Ollama Models
If you want to run offline local models:
```bash
ollama run gemma4
# or
ollama run llama3.2
```
Local models will automatically appear under **"Local · Ollama"** in the web UI.

---

## Supported AI Providers

Configured via `backend/.env`:

| Provider | Environment Variable | Recommended Models | Notes |
|---|---|---|---|
| **Google Gemini** | `GEMINI_API_KEY` | `gemini-2.5-flash`, `gemini-2.5-pro` | Free tier via Google AI Studio |
| **OpenAI** | `OPENAI_API_KEY` | `gpt-4o`, `gpt-4o-mini`, `o3-mini` | Paid API credits |
| **Anthropic** | `ANTHROPIC_API_KEY` | `claude-3-7-sonnet`, `claude-3-5-sonnet` | Paid API credits |
| **xAI Grok** | `GROK_API_KEY` | `grok-2` | xAI Console |
| **Local Ollama** | `OLLAMA_HOST` | `gemma4`, `llama3.2`, `qwen2.5` | Runs on localhost:11434 |

---

## Development & Quality Checks

Defined in [AGENTS.md](AGENTS.md):

* **Frontend:**
  ```bash
  cd frontend
  npm run typecheck    # Validate TypeScript types & Next routes
  npm run build        # Production build verification
  ```

* **Backend:**
  ```bash
  cd backend
  uv run pytest        # Run test suite
  uv run ruff check .  # Linting check
  uv run ruff format . # Format Python code
  ```
