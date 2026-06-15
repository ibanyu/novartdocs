---
title: Async Tasks and Callbacks
excerpt: Submit jobs, poll task status, and correlate callback results.
hidden: false
---

Long-running operations return immediately and complete in the background. This applies to most video tools, AI actor performance, Persona creation, and AdClone generation.

## Submit a job

Include a stable `callback_id` when your system needs to match a result to an internal record.

```json
{
  "prompt": "A cat running on a beach",
  "model": "veo-3.1",
  "ratio": "16:9",
  "duration": 8,
  "resolution": "1080p",
  "callback_id": "job_12345",
  "idempotency_key": "job_12345_video_generate"
}
```

Most submit responses return a `workspace_id`.

## Poll status

```bash
curl 'https://www.adsturbo.ai/klian/novartapi/openapi/v1/work/status' \
  -H 'Authorization: Bearer sk_YOUR_API_KEY_HERE' \
  -H 'Content-Type: application/json' \
  --data-raw '{"workspace_id":"YOUR_WORKSPACE_ID"}'
```

For multiple jobs, use `/openapi/v1/work/batch-status`.

## Polling guidance

Poll every 10 to 20 seconds for normal jobs. Avoid retrying the submit endpoint unless the task failed or you intentionally want a new output. If a client times out after submission, resume by polling the known `workspace_id`.

## Persona status

Persona creation returns actor data and may need additional processing time. Query `/openapi/v1/persona/status` with the `actor_id`.
