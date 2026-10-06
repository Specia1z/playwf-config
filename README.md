# PlayWF Configuration

Public configuration consumed by the PlayWF launcher and WebView2 UI.

The launcher reads the stable configuration file from:

```text
https://raw.githubusercontent.com/Specia1z/playwf-config/main/servers.json
```

This repository may contain public connection details only. Do not add:

- account passwords or session tokens;
- database credentials;
- TLS private keys;
- administrator credentials;
- signing secrets.

## Configuration

`servers.json` contains the launcher release repository and the list of
servers shown in the UI. A server is available only when `enabled` is `true`
and `maintenance` is `false`.

Example entry:

```json
{
  "id": "public",
  "name": "PlayWF Public",
  "description": "Public PlayWF server",
  "host": "playwf.example.com",
  "httpPort": 80,
  "httpsPort": 443,
  "secureConnections": true,
  "enabled": true,
  "maintenance": false
}
```

The corresponding JSON schema is in `schema/servers.schema.json`.

## Update Rules

Keep changes small and validate `servers.json` before pushing. The launcher
uses the last valid cached configuration when GitHub is temporarily
unavailable. The launcher will reject malformed JSON, non-HTTPS server
configuration, invalid ports, and duplicate server IDs.
