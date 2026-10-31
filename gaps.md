# s3baga gaps

## Open

### A1 — std HTTP client bodies are `str`

`http_request` cannot carry a null byte. This package writes the request
as `bytes` over TCP/TLS instead.

### A3 — ~~no chunked bodies~~ — closed 2026-10-31

`s3_parse` детектира `Transfer-Encoding: chunked` и декодира през
`s3_decode_chunked` (hex размер + CRLF + данни + CRLF, терминиращ 0-chunk).
Content-Length пътят остава за non-chunked отговори.

## Closed

### A2 — virtual-hosted style — closed 2026-10-31

`S3_STYLE=virtual` (or `vhost`): host = `bucket.endpoint_host`, uri = `/key`.
Default `path`: host = endpoint host, uri = `/bucket/key`. Signing uses the
resolved host/uri, so SigV4 is correct for both styles.
