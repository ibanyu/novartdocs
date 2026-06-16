---
title: Authentication
excerpt: Authenticate AdsTurbo Open API calls with Bearer API keys.
api_config: authentication
hidden: false
icon: icon-key1
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

Store API keys in your server environment, not in browser code or mobile clients. Rotate a key if it is exposed in logs, screenshots, source control, or client-side bundles.