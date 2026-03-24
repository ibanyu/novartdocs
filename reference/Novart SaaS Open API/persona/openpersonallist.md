---
title: 自定义 Persona 列表
excerpt: >
  对应 proto `OpenPersonalList`：个人创建演员（`novart_actor_from_user`）。分页返回
  `OpenPersonaData` 列表。

  请求体中的 `api_key` / `uid` / `owner_uid` 可与网关填充的身份字段一并省略（由 SaaS 网关注入）。
api:
  file: docsopenapi.yaml
  operationId: openPersonalList
hidden: false
---