# s3baga gaps

## Open

### A1 — std HTTP client bodies are `str`

`http_request` cannot carry a null byte. This package writes the request
as `bytes` over TCP/TLS instead.

### A3 — no chunked bodies

The response is read to EOF. `Content-Length` trims the body when present.

## Closed

### A2 — virtual-hosted style — closed 2026-10-31

`S3_STYLE=virtual` (or `vhost`): host = `bucket.endpoint_host`, uri = `/key`.
Default `path`: host = endpoint host, uri = `/bucket/key`. Signing uses the
resolved host/uri, so SigV4 is correct for both styles.
