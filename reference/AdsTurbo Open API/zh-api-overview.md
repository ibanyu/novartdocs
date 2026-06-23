---
title: API 介绍
excerpt: AdsTurbo Open API 的鉴权、异步任务与响应格式说明。
hidden: false
---

AdsTurbo Open API 可用于图片生成、视频生成与编辑、AI Actor、Persona、AdClone，以及异步任务状态查询。

英文文档：[View English API Reference](/reference/api-overview)。每个中文接口详情页也会链接回对应的英文接口详情页。

## Base URL

```text
https://www.adsturbo.ai/klian/novartapi
```

所有公开接口都是 `POST`，路径前缀为 `/openapi/v1/`。

## 鉴权

API Key 使用 Bearer token 发送：

```http
Authorization: Bearer sk_YOUR_API_KEY_HERE
Content-Type: application/json
```

公开 Open API 不使用 `x-pal-key`。

## 响应 envelope

业务成功响应格式：

```json
{
  "ret": 1,
  "data": {
    "ent": {}
  }
}
```

HTTP 200 不一定代表业务成功。只将 `ret === 1` 视为成功；如果 `ret` 不是 `1`，读取 `msg`，修正请求后再判断是否重试。

## 异步任务

大多数视频、Actor、Persona、AdClone 能力都是异步任务：

1. 提交任务。
2. 保存返回的 `workspace_id` 或 `actor_id`。
3. 调用 `/openapi/v1/work/status`、`/openapi/v1/work/batch-status` 或 `/openapi/v1/persona/status` 查询状态。
4. 使用 `callback_id` 将结果关联到你系统里的任务记录。

具体字段和响应结构见左侧各接口详情页。
