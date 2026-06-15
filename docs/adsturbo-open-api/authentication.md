---
title: Authentication
excerpt: Authenticate AdsTurbo Open API calls with Bearer API keys.
hidden: false
---

AdsTurbo Open API uses HTTP Bearer authentication.

```http
Authorization: Bearer sk_YOUR_API_KEY_HERE
```

Create and manage API keys in the AdsTurbo console. Treat each API key as a secret.

## Required headers

```http
Authorization: Bearer sk_YOUR_API_KEY_HERE
Content-Type: application/json
Accept: application/json
```

`x-pal-key` is not used for the public ReadMe documentation. Examples and generated SDK snippets should use `Authorization: Bearer`.

## Key handling

Store API keys in your server environment, not in browser code or mobile clients. Rotate a key if it is exposed in logs, screenshots, source control, or client-side bundles.

## Common failures

| Symptom | Likely cause | Fix |
| --- | --- | --- |
| `ret` is not `1` and `msg` mentions authentication | Missing or invalid token | Send `Authorization: Bearer <token>` |
| Requests work in staging but not production | Wrong Base URL | Use `https://www.adsturbo.ai/klian/novartapi` |
| Generated examples use a different header | Old local docs or SDK config | Regenerate from the latest OpenAPI spec |
