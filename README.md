# YUZ.AI — Intelligent Search Engine

A Perplexity-style AI chat and search engine built with HTML, Tailwind CSS, and Vanilla JavaScript.

## Features

- **Split viewport** — Chat left, Sources & Research right
- **Real AI streaming** — OpenRouter API with SSE token streaming
- **5 free models** — Llama 3.3 70B, Llama 3.1 8B, Mistral 7B, Gemma 3 27B, DeepSeek R1
- **Simulated RAG** — Query classified → domain-matched sources → context injected into prompt
- **Markdown rendering** — Bold, headers, lists, code blocks, citation superscripts `[1]`
- **Conversation history** — Last 8 turns kept for multi-turn context
- **Search toggle** — Disable source injection for pure chat mode
- **New Chat** — Clears history and resets the UI

## Setup (2 minutes)

1. Go to [openrouter.ai](https://openrouter.ai) → Create free account → Keys → Create Key
2. Open `index.html` in a browser (or deploy to GitHub Pages)
3. Click **Set Key** in the top bar → paste your key → Save
4. Start asking questions

## Deploy to GitHub Pages

```bash
git init && git add . && git commit -m "Launch YUZ.AI"
git remote add origin https://github.com/YOUR_USER/yuz.ai.git
git push -u origin main
# Settings → Pages → Deploy from main branch root
```

## Architecture

```
User Query
    │
    ├── simulateSearch()      ← keyword extraction + domain classification
    │       └── buildSystemPrompt()  ← RAG context injection
    │
    └── streamAIResponse()    ← OpenRouter SSE streaming
            └── renderMarkdown()    ← live token rendering
```

## Tech Stack

- HTML5 · Tailwind CSS (CDN) · Vanilla JS ES2022
- OpenRouter API (free tier, no credit card)
- Google Favicons API (source icons)
