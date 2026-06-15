---
title: 鉴权
excerpt: 使用 Bearer API Key 鉴权 AdsTurbo Open API。
hidden: false
---

AdsTurbo Open API 使用 HTTP Bearer 鉴权。

```http
Authorization: Bearer sk_YOUR_API_KEY_HERE
```

API Key 在 AdsTurbo 控制台创建和管理。每个 API Key 都应按密钥处理。

## 必需请求头

```http
Authorization: Bearer sk_YOUR_API_KEY_HERE
Content-Type: application/json
Accept: application/json
```

公开 ReadMe 文档不使用 `x-pal-key`。示例和 SDK 生成代码都应使用 `Authorization: Bearer`。

## 密钥处理

将 API Key 存在服务端环境变量或密钥管理系统里，不要放在浏览器代码、移动端包、截图、日志或仓库中。如果发生泄露，应立即轮换。

## 常见失败

| 现象 | 可能原因 | 处理 |
| --- | --- | --- |
| `ret` 不是 `1` 且 `msg` 提到鉴权 | token 缺失或无效 | 发送 `Authorization: Bearer <token>` |
| 测试环境可用，生产不可用 | Base URL 错误 | 使用 `https://www.adsturbo.ai/klian/novartapi` |
| 生成示例用了其他请求头 | 本地文档或 SDK 配置过旧 | 使用最新 OpenAPI 重新生成 |
