---
title: 异步任务与回调
excerpt: 提交任务、轮询状态，并用 callback_id 关联结果。
hidden: false
---

耗时较长的能力会先返回任务信息，再在后台处理。视频工具、AI Actor 演出、Persona 创建、AdClone 生成通常都属于异步任务。

## 提交任务

如果你的系统需要把结果映射回内部任务，建议传稳定的 `callback_id`。

```json
{
  "prompt": "一只猫在沙滩奔跑",
  "model": "veo-3.1",
  "ratio": "16:9",
  "duration": 8,
  "resolution": "1080p",
  "callback_id": "job_12345",
  "idempotency_key": "job_12345_video_generate"
}
```

大多数提交接口会返回 `workspace_id`。

## 查询状态

```bash
curl 'https://www.adsturbo.ai/klian/novartapi/openapi/v1/work/status' \
  -H 'Authorization: Bearer sk_YOUR_API_KEY_HERE' \
  -H 'Content-Type: application/json' \
  --data-raw '{"workspace_id":"YOUR_WORKSPACE_ID"}'
```

多个任务可使用 `/openapi/v1/work/batch-status` 批量查询。

## 轮询建议

普通任务建议每 10 到 20 秒轮询一次。客户端提交后超时，不要直接重复提交；优先用已知 `workspace_id` 继续查询。只有任务失败或你明确需要一个新结果时，才重新提交。

## Persona 状态

Persona 创建返回 actor 信息后可能仍需要处理时间。使用 `/openapi/v1/persona/status` 并传入 `actor_id` 查询。
