---
title: 创建 Persona 并生成口播视频
description: 用照片和声音样本创建自定义 Persona，再使用返回的 `actor_id` 生成口播视频。
hidden: false
recipe:
  color: '#0B1220'
  icon: ''
---
```Shell cURL
curl 'https://www.adsturbo.ai/klian/novartapi/openapi/v1/persona/create' \
  -H 'Authorization: Bearer sk_YOUR_API_KEY_HERE' \
  -H 'Content-Type: application/json' \
  --data-raw '{
    "photo_url": "https://example.com/photo.jpg",
    "voice_audio_url": "https://example.com/voice.mp3",
    "name": "Demo Persona",
    "callback_id": "recipe_persona_001"
  }'
```

# 创建 Persona



```bash
curl 'https://www.adsturbo.ai/klian/novartapi/openapi/v1/persona/create' \
  -H 'Authorization: Bearer sk_YOUR_API_KEY_HERE' \
  -H 'Content-Type: application/json' \
  --data-raw '{
    "photo_url": "https://example.com/photo.jpg",
    "voice_audio_url": "https://example.com/voice.mp3",
    "name": "Demo Persona",
    "callback_id": "recipe_persona_001"
  }'
```

# 查询 Persona 状态



```bash
curl 'https://www.adsturbo.ai/klian/novartapi/openapi/v1/persona/status' \
  -H 'Authorization: Bearer sk_YOUR_API_KEY_HERE' \
  -H 'Content-Type: application/json' \
  --data-raw '{"actor_id":"YOUR_ACTOR_ID"}'
```

# 生成口播视频



```bash
curl 'https://www.adsturbo.ai/klian/novartapi/openapi/v1/aiactor/perform' \
  -H 'Authorization: Bearer sk_YOUR_API_KEY_HERE' \
  -H 'Content-Type: application/json' \
  --data-raw '{
    "actor_id": "YOUR_ACTOR_ID",
    "script": "Welcome to our new product launch.",
    "auto_emotion": true,
    "speed": 1,
    "stability": 0.5,
    "similarity": 0.8,
    "callback_id": "recipe_persona_perform_001"
  }'
```