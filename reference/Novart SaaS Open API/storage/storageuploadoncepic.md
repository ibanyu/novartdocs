---
title: 图片上传
excerpt: |
  上传图片文件，服务端自动存储原图并生成 400×400 自适应裁剪缩略图，响应同时返回原图与缩略图信息。
  请求体为 `multipart/form-data`，包含 `data`（图片文件）和 `json`（JSON 参数字符串）两个字段。
api:
  file: docsopenapi.yaml
  operationId: storageUploadOncePic
hidden: false
---