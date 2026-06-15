---
title: Quickstart
excerpt: Make your first AdsTurbo Open API request.
hidden: false
---

Use the AdsTurbo Open API to create images, generate and edit videos, run AI actor workflows, manage Personas, and check asynchronous job status.

## Base URL

```text
https://www.adsturbo.ai/klian/novartapi
```

All public endpoints are `POST` requests under `/openapi/v1/`.

## Authentication

Send your API key as a Bearer token:

```http
Authorization: Bearer sk_YOUR_API_KEY_HERE
Content-Type: application/json
```

Do not send the key in query parameters or commit it to source control.

## First request

```bash
curl 'https://www.adsturbo.ai/klian/novartapi/openapi/v1/img/create' \
  -H 'Authorization: Bearer sk_YOUR_API_KEY_HERE' \
  -H 'Content-Type: application/json' \
  --data-raw '{
    "prompt": "A clean product shot of a running shoe on a white background",
    "model": "nanobanana-pro",
    "image_urls": [],
    "ratio": "1:1",
    "resolution": "2k",
    "concurrency": 1,
    "sync_mod": false
  }'
```

Successful responses use this envelope:

```json
{
  "ret": 1,
  "data": {
    "ent": {}
  }
}
```

If `ret` is not `1`, read `msg` and adjust the request before retrying.

## Async workflow

Most video, actor, Persona, and AdClone operations are asynchronous:

1. Submit the job and store the returned `workspace_id` or `actor_id`.
2. Poll `/openapi/v1/work/status` or `/openapi/v1/persona/status`.
3. Use the returned asset URL when the task is complete.

Use `callback_id` to correlate webhook results with your internal job records.
