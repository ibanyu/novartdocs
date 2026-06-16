---
title: API Overview / API 介绍
excerpt: >-
  AdsTurbo Open API authentication, async jobs, response handling, and common
  workflows.
api_config: getting-started
hidden: false
icon: icon-book1
---
AdsTurbo Open API lets you create images, generate and edit videos, run AI Actor workflows, manage Personas, recreate ads with AdClone, and check asynchronous task status.

AdsTurbo Open API 可用于图片生成、视频生成与编辑、AI Actor、Persona、AdClone，以及异步任务状态查询。

## Base URL

```text
https://www.adsturbo.ai/klian/novartapi
```

All public endpoints are `POST` requests under `/openapi/v1/`.

## Authentication

Use your AdsTurbo API key as a Bearer token:

```http
Authorization: Bearer sk_YOUR_API_KEY_HERE
Content-Type: application/json
```

Do not use `x-pal-key` for the public Open API.

## Response envelope

Successful business responses use:

```json
{
  "ret": 1,
  "data": {
    "ent": {}
  }
}
```

HTTP 200 can still contain a business error. Treat only `ret === 1` as success. If `ret` is not `1`, read `msg` and fix the request before retrying.

## Async jobs

Most video, actor, Persona, and AdClone endpoints are asynchronous:

1. Submit the job.
2. Store the returned `workspace_id` or `actor_id`.
3. Poll `/openapi/v1/work/status`, `/openapi/v1/work/batch-status`, or `/openapi/v1/persona/status`.
4. Use `callback_id` to correlate results with your own job records.

Start with the endpoint pages in the sidebar for exact request and response schemas.

具体字段和响应结构见左侧各接口详情页。