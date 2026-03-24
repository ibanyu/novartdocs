---
title: 用量查询（SaaS 控制台 · 会话登录）
excerpt: >
  与其它 `/openapi/v1/*` 不同：走 **标准会话鉴权**（`InitStandardReq`），**不要**使用请求头
  `x-pal-key`。

  JSON body 与站内标准 POST 相同：先绑定会话头字段，再绑定下方业务字段（`offset` / `limit`）。
api:
  file: docsopenapi.yaml
  operationId: openGetUsage
hidden: true
---