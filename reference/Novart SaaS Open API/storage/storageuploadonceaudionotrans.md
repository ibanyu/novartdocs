---
title: 音频上传（不转码）
excerpt: |
  上传音频文件，不做转码处理，直接存储原始音频。
  请求体为 `multipart/form-data`，包含 `data`（音频文件）和 `json`（JSON 参数字符串）两个字段。
api:
  file: docsopenapi.yaml
  operationId: storageUploadOnceAudioNotrans
hidden: false
---