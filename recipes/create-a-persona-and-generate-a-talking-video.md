---
title: Create a Persona and generate a talking video
description: >-
  Create a custom Persona from a photo and voice sample, then use the returned
  `actor_id` to generate a talking-head video.
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

# Create the Persona



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

# Check Persona status



```bash
curl 'https://www.adsturbo.ai/klian/novartapi/openapi/v1/persona/status' \
  -H 'Authorization: Bearer sk_YOUR_API_KEY_HERE' \
  -H 'Content-Type: application/json' \
  --data-raw '{"actor_id":"YOUR_ACTOR_ID"}'
```

# Generate a talking video



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