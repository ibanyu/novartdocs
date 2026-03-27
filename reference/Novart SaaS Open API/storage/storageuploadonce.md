---
title: 文件上传
excerpt: |
  通用文件上传接口。请求体为 `multipart/form-data`，包含 `data`（文件）和 `json`（JSON 参数字符串）两个字段。
  当 `storagetype = 1` 时使用大文件上传通道，其余走普通上传。
api:
  file: docsopenapi.yaml
  operationId: storageUploadOnce
hidden: false
---