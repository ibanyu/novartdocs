---
title: 模型、素材与错误
excerpt: 了解模型参数、素材 URL 要求和错误处理方式。
hidden: false
---

不同模型支持的参数范围可能不同。生产请求前，应确认 `model`、`duration`、`ratio`、`resolution` 和参考素材数量是否合法。

## 素材 URL 要求

请使用 AdsTurbo 服务端可以访问的 HTTPS URL。

推荐：

- 公网可访问的 HTTPS URL
- 任务完成前持续有效的 URL
- 正确的文件扩展名和 Content-Type
- 不依赖浏览器登录态、不加密的视频和音频文件

如果使用短期签名 URL，请确保有效期足够覆盖排队和处理时间。

## 与模型相关的字段

常见字段：

| 字段 | 说明 |
| --- | --- |
| `model` | 当前操作使用的模型 |
| `ratio` | 输出比例，如 `16:9`、`9:16`、`1:1` |
| `duration` | 视频时长或延长秒数，含义取决于接口 |
| `resolution` | 输出分辨率，如 `1080p`、`2k`、`4k` |
| `reference_images` | 支持模型可传参考图片 |
| `reference_videos` | 支持模型可传参考视频 |
| `reference_audios` | 支持模型可传参考音频 |

## 错误 envelope

接口可能返回 HTTP 200，但业务失败：

```json
{
  "ret": 10001,
  "msg": "invalid parameter"
}
```

只将 `ret === 1` 视为成功。其他值都应读取 `msg`，修正请求后再判断是否重试。

## 停用接口

`/openapi/v1/usage` 不发布到公开 API Reference。
