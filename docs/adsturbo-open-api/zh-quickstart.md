---
title: 快速开始
excerpt: 发起第一个 AdsTurbo Open API 请求。
hidden: false
---

AdsTurbo Open API 可用于图片生成、视频生成与编辑、AI Actor、Persona、AdClone，以及异步任务状态查询。

## Base URL

```text
https://www.adsturbo.ai/klian/novartapi
```

所有公开接口都是 `POST`，路径前缀为 `/openapi/v1/`。

## 鉴权

API Key 通过 Bearer token 放在请求头：

```http
Authorization: Bearer sk_YOUR_API_KEY_HERE
Content-Type: application/json
```

不要把 API Key 放在 URL 查询参数里，也不要提交到代码仓库。

## 第一个请求

```bash
curl 'https://www.adsturbo.ai/klian/novartapi/openapi/v1/img/create' \
  -H 'Authorization: Bearer sk_YOUR_API_KEY_HERE' \
  -H 'Content-Type: application/json' \
  --data-raw '{
    "prompt": "白色背景上的跑鞋商品图",
    "model": "nanobanana-pro",
    "image_urls": [],
    "ratio": "1:1",
    "resolution": "2k",
    "concurrency": 1,
    "sync_mod": false
  }'
```

成功响应使用统一 envelope：

```json
{
  "ret": 1,
  "data": {
    "ent": {}
  }
}
```

如果 `ret` 不是 `1`，读取 `msg` 并修正请求后再重试。

## 异步任务流程

大多数视频、Actor、Persona、AdClone 能力都是异步任务：

1. 提交任务，保存返回的 `workspace_id` 或 `actor_id`。
2. 调用 `/openapi/v1/work/status` 或 `/openapi/v1/persona/status` 查询状态。
3. 任务完成后使用返回的素材 URL。

使用 `callback_id` 可以把回调结果和你系统里的任务记录关联起来。
