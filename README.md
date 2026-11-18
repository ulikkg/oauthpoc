# oauthpoc — JWKS host

Static **JWKS (public key set)** for an OAuth 2.0 Token Exchange (RFC 8693) PoC.

Salesforce's `Auth.TokenExchangeHandler` fetches `jwks.json` from here to verify the
RS256 signature of a Portal/Strapi-issued JWT. Hosting it as a static GitHub raw file
means Salesforce can always reach it (no local tunnel, survives corporate proxies).

**Raw URL (used as `JWKS_URL` in Apex + allow-listed as a Remote Site Setting):**

```
https://raw.githubusercontent.com/ulikkg/oauthpoc/main/jwks.json
```

- `kid` = `strapi-key-1`. Only the **public** key lives here — this is safe to be public.
- If the signing key is regenerated, re-commit the new `jwks.json` (same URL).
