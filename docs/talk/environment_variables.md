Envrionment Variables

## Environment variables

| Variable | Required | Description |
|----------|----------|-------------|
| `DWANI_API_BASE_URL_ASR` | Yes | ASR URL |
| `DWANI_API_BASE_URL_TTS` | Yes | TTS URL |
| `DWANI_API_BASE_URL_LLM` | Yes | LLM URL (OpenAI-compatible) |
| `DWANI_LLM_MODEL` | No | Model name (default: `gemma3`) |
| `DWANI_AGENT_BASE_URL` | No | Agents service URL in agent mode (e.g. `http://agents:8081`) |
| `DWANI_API_KEY` | No | Optional API key required by talk-server when set |
| `DWANI_REDIS_URL` | No | Redis URL for persistent chat sessions |
| `AGENTS_API_KEY` | No | Optional API key required by agents service when set |
| `AGENTS_REDIS_URL` | No | Redis URL for agent conversation history persistence |
| `DWANI_TALK_SERVER_TAG` | No | Docker image tag for talk-server (default: `latest`) |
| `DWANI_TALK_UI_TAG` | No | Docker image tag for talk-ui (default: `latest`) |
| `DWANI_TALK_AGENTS_TAG` | No | Docker image tag for agents (default: `latest`) |

See [.env.example](.env.example) for timeouts, limits, and session options.
