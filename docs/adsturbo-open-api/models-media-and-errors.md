---
title: Models, Media, and Errors
excerpt: >-
  Understand model-specific parameters, media URL requirements, and error
  handling.
hidden: false
---

Model capabilities can differ by endpoint. Validate `model`, `duration`, `ratio`, `resolution`, and reference media counts before sending production traffic.

## Media URL requirements

Use HTTPS URLs that AdsTurbo can fetch from the server side.

Recommended:

- Publicly reachable HTTPS URLs
- Stable URLs that remain available until the job completes
- Correct file extensions and content types
- Video and audio files that are not encrypted or behind browser-only authentication

Avoid short-lived signed URLs unless their expiry is long enough for queueing and processing.

## Model-sensitive fields

Common fields include:

| Field | Notes |
| --- | --- |
| `model` | Model name selected for the operation |
| `ratio` | Output aspect ratio, such as `16:9`, `9:16`, or `1:1` |
| `duration` | Video duration or extension seconds, depending on endpoint |
| `resolution` | Output resolution, such as `1080p`, `2k`, or `4k` |
| `reference_images` | Optional image references for supported models |
| `reference_videos` | Optional video references for supported models |
| `reference_audios` | Optional audio references for supported models |

## Error envelope

The API may return HTTP 200 with a business error:

```json
{
  "ret": 10001,
  "msg": "invalid parameter"
}
```

Treat `ret === 1` as success. For any other value, inspect `msg`, fix the request, and retry only when the failure is recoverable.

## Deprecated endpoints

`/openapi/v1/usage` is not published in the public API Reference.
