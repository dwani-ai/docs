# Talk Production Runbook

## Service Health Checks

- `talk-server`: `GET /health`, `GET /ready`, `GET /metrics`
- `agents`: `GET /healthz`, `GET /metrics`
- `redis`: `redis-cli ping`
- External dependencies:
  - ASR: `DWANI_API_BASE_URL_ASR`
  - TTS: `DWANI_API_BASE_URL_TTS`
  - LLM: `DWANI_API_BASE_URL_LLM`

## Common Incidents

### 502 from `/v1/chat` or `/v1/speech_to_speech`

- Validate upstream service URL env vars.
- Check dependency health (`/ready` response details).
- Check `agents` health if using `mode=agent`.

### 504 timeout from speech endpoint

- Verify ASR/TTS latency and service logs.
- Increase `DWANI_ASR_TIMEOUT`/`DWANI_TTS_TIMEOUT` if model nodes are healthy but slow.
- Inspect queue/load and scale upstream services.

### Authentication failures (401)

- Confirm `DWANI_API_KEY` and `AGENTS_API_KEY` values are set consistently.
- Ensure UI/backend clients pass `X-API-Key` when auth is enabled.

### Session loss after restart

- Confirm Redis container is healthy and reachable from `talk-server`.
- Validate `DWANI_REDIS_URL`.

## Operational Commands

```bash
docker compose ps
docker compose logs -f talk
docker compose logs -f agents
docker compose logs -f redis
```

## Rollback

1. Set image tags to previous known good versions (`DWANI_TALK_*_TAG`).
2. `docker compose pull`
3. `docker compose up -d`
4. Re-run health checks and a `/v1/chat` smoke test.