# TALK— Conversational AI Agents for Indian languages

Try it: [talk.dwani.ai](https://talk.dwani.ai)

---

## Prerequisites

- **Local:** Python 3.10+, ASR / TTS / LLM services (see [External services](#external-services)).
- **Docker:** Docker and Docker Compose. Integrated stack needs GPU with ≥24 GB VRAM.

## Quick start

| Goal | Command |
|------|--------|
| **Docker (host ASR/TTS/LLM)** | `cp .env.example .env` → `docker compose up -d` → http://localhost |
| **Docker dev (build from source)** | `docker compose -f compose-dev.yml up -d --build` |
| **Production (integrated TTS + LLM + ASR)** | `docker compose -f compose-integrated-qwen.yml up -d` |
| **Local Python** | Set env URLs → `cd talk-server && pip install -r requirements.txt && python main.py` |

## Running

**Docker (backend + UI in containers; ASR/TTS/LLM on host):**  
Copy `.env.example` to `.env`, set `DWANI_API_BASE_URL_*` if needed (defaults use `host.docker.internal:10803/10804/10802`). Run `docker compose up -d`. Open http://localhost.

**Integrated stack (TTS + LLM + ASR in compose; ASR):**  
> 16 GB VRAM - GPU on server
Run `docker compose -f compose-integrated-qwen.yml up -d`. Needs GPU. Open http://localhost.

> 6GB < 16 GB VRAM - GPU on laptop
Run `docker compose -f compose-integrated-qwen-local.yml up -d`. Needs GPU. Open http://localhost.


**Local Python (no UI):**  
Export `DWANI_API_BASE_URL_ASR`, `DWANI_API_BASE_URL_TTS`, `DWANI_API_BASE_URL_LLM`. Then `cd talk-server && pip install -r requirements.txt && python main.py`. API at http://localhost:8000.

## Agent mode

The UI can use the **LLM** or an **ADK agent** (travel planner, viva examiner, fix-my-city, orchestrator, warehouse, chess). See [agents/README.md](agents/README.md).

## External services

| Service | Port | Notes |
|---------|------|--------|
| **ASR** | 10803 | [asr-indic-server](https://github.com/dwani-ai/asr-indic-server) |
| **TTS** | 10804 | [tts-indic-server](https://github.com/dwani-ai/tts-indic-server) |
| **LLM** | 10802 | vLLM / OpenAI-compatible; [docs/llm-setup.md](docs/llm-setup.md) |


## Test

```bash
curl -X POST 'http://localhost:8000/v1/speech_to_speech?language=kannada' \
  -H 'Content-Type: multipart/form-data' -F 'file=@sample.wav' -o out.mp3
```

(Use `http://localhost/v1/...` if the UI proxy is on port 80.)

## Docs

- [agents.md](agents.md) — Agent mode, ADK setup, and agents service.
- [ARCHITECTURE.md](docs/ARCHITECTURE.md) — Architecture diagram, tech stack, Docker build, Chess tab.
- [environment_variables](environment_variables.md) - Environment Variables
- [docs/runbook.md](docs/runbook.md) — Production runbook and incident handling.
