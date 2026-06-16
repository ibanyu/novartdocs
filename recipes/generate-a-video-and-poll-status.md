---
title: Generate a video and poll status
description: >-
  Submit a video generation task, store the `workspace_id`, then poll until the
  task finishes.
hidden: false
recipe:
  color: '#0B1220'
  icon: ''
---
```Shell cURL
curl 'https://www.adsturbo.ai/klian/novartapi/openapi/v1/video/generate' \
  -H 'Authorization: Bearer sk_YOUR_API_KEY_HERE' \
  -H 'Content-Type: application/json' \
  --data-raw '{
    "prompt": "A cat running on a beach",
    "model": "veo-3.1",
    "ratio": "16:9",
    "duration": 8,
    "resolution": "1080p",
    "callback_id": "recipe_video_generate_001",
    "idempotency_key": "recipe_video_generate_001"
  }'
```

```json Response Example
When the task completes, the status response contains the generated media URL under the returned `ent` object.
```

# Submit the video job



```bash
curl 'https://www.adsturbo.ai/klian/novartapi/openapi/v1/video/generate' \
  -H 'Authorization: Bearer sk_YOUR_API_KEY_HERE' \
  -H 'Content-Type: application/json' \
  --data-raw '{
    "prompt": "A cat running on a beach",
    "model": "veo-3.1",
    "ratio": "16:9",
    "duration": 8,
    "resolution": "1080p",
    "callback_id": "recipe_video_generate_001",
    "idempotency_key": "recipe_video_generate_001"
  }'
```

# Poll the workspace



```bash
curl 'https://www.adsturbo.ai/klian/novartapi/openapi/v1/work/status' \
  -H 'Authorization: Bearer sk_YOUR_API_KEY_HERE' \
  -H 'Content-Type: application/json' \
  --data-raw '{"workspace_id":"YOUR_WORKSPACE_ID"}'
```

## Expected result

When the task completes, the status response contains the generated media URL under the returned `ent` object.