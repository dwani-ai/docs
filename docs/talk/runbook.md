# Architecture and tech stack

## High-level overview

- **Frontend (Talk UI)** – React/Vite SPA in `talk-ui/`: records audio, calls `/v1/speech_to_speech` or `/v1/chat` with `X-Session-ID`, and lets the user choose LLM or agent mode (travel, viva, fix-my-city, orchestrator, warehouse, chess).
- **Backend (Talk server)** – FastAPI in `talk-server/`: ASR → text; sends text to LLM or to the agents service; reply text → TTS → MP3. In-memory session only.
- **Agents service** – FastAPI + Google ADK in `agents/`: `POST /v1/agents/{agent_name}/chat`; agents call the same LLM via LiteLlm; Fix my city uses SQLite.
- **External services** – ASR (10803), TTS (10804), LLM (10802, OpenAI-compatible).

```mermaid
flowchart LR
  subgraph client["Client"]
    talkUi["TalkUI"]
  end

  subgraph api["TalkServer_FastAPI"]
    chatEp["ChatEndpoint_/v1/chat"]
    s2sEp["Speech2Speech_/v1/speech_to_speech"]
  end

  subgraph modelServices["ModelAndSpeechServices"]
    asrSvc["ASRServer"]
    ttsSvc["TTSServer"]
    llmSvc["LLMServer_vLLM_or_Qwen"]
  end

  subgraph agentsService["AgentsService_FastAPI_ADK"]
    httpChat["AgentsHTTP_/v1/agents/{agent_name}/chat"]

    subgraph adkCore["ADKRunnersAndSessions"]
      sessionStore["InMemorySessionService"]
      runnerTravel["Runner_travel_planner"]
      runnerViva["Runner_viva_examiner"]
      runnerCity["Runner_fix_my_city"]
      runnerOrch["Runner_orchestrator"]
    end

    subgraph adkAgents["ADKAgents"]
      agentTravel["TravelPlannerAgent"]
      agentViva["VivaExaminerAgent"]
      agentCity["FixMyCityAgent"]
      agentOrch["OrchestratorAgent"]
    end

    subgraph cityStorage["FixMyCityStorage"]
      cityDb["SQLiteComplaintsDB"]
    end
  end

  talkUi -->|text_or_audio\nX-Session-ID| chatEp
  talkUi -->|audio\nX-Session-ID| s2sEp

  s2sEp -->|audio| asrSvc
  asrSvc -->|text| s2sEp

  chatEp -->|mode=llm\ntext_plus_context| llmSvc
  chatEp -->|mode=agent\ntext_plus_session_id| httpChat
  s2sEp -->|text_plus_mode\n(agent_or_llm)| chatEp

  httpChat -->|agent_name=travel_planner| runnerTravel
  httpChat -->|agent_name=viva_examiner| runnerViva
  httpChat -->|agent_name=fix_my_city| runnerCity
  httpChat -->|agent_name=orchestrator| runnerOrch

  runnerTravel --> agentTravel
  runnerViva --> agentViva
  runnerCity --> agentCity
  runnerOrch --> agentOrch

  agentOrch -->|tool_call_travel_planner| runnerTravel
  agentOrch -->|tool_call_viva_examiner| runnerViva
  agentOrch -->|tool_call_fix_my_city| runnerCity

  agentTravel -->|LiteLlm_calls| llmSvc
  agentViva -->|LiteLlm_calls| llmSvc
  agentCity -->|LiteLlm_calls| llmSvc
  agentOrch -->|LiteLlm_calls| llmSvc

  agentCity -->|create_get_update_complaints| cityDb

  chatEp -->|reply_text| ttsSvc
  s2sEp -->|reply_text| ttsSvc
  ttsSvc -->|mp3_audio| talkUi
```

## Tech stack

| Layer | Stack |
|-------|--------|
| **Frontend** | React, Vite, MediaRecorder, fetch |
| **Backend** | Python 3.10+, FastAPI, Uvicorn, httpx, OpenAI client, slowapi, Pydantic v2 |
| **Agents** | FastAPI, Google ADK, LiteLlm, InMemorySessionService, SQLite (fix-my-city) |
| **ASR/TTS/LLM** | [asr-indic-server](https://github.com/dwani-ai/asr-indic-server), [tts-indic-server](https://github.com/dwani-ai/tts-indic-server), vLLM/OpenAI-compatible API |
| **Infra** | Docker, Docker Compose, .env for config |

## Build Docker images

```bash
# Backend
cd talk-server && docker build -t dwani/talk-server:latest -f Dockerfile .

# Frontend
cd talk-ui && docker build -t dwani/talk-ux:latest -f Dockerfile .

# Agents
cd agents && docker build -t dwani/talk-agents:latest -f Dockerfile .
```

Image names are consistent across compose files: `dwani/talk-server:latest`, `dwani/talk-ux:latest`, `dwani/talk-agents:latest`. Use with `compose.yml`, `compose-dev.yml`, or `compose-integrated.yml`.

## Chess tab (agent-driven)

The UI has a **Chess** tab: chat commands go to `/v1/chat` with `agent_name: "chess_orchestrator"`. The agents service returns `chess_state`; the UI also polls `/v1/chess/state`.

**Supported commands:** `new game`, `new game human vs ai as white`, `new game human vs human`, `e2 to e4` / `e2e4`, `ai move`, `show board state`, plus natural-language moves. Rules and turn order are enforced. The tab renders 3D with move interpolation and capture effects.