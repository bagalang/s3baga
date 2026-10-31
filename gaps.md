# s3baga gaps

## Open

### A1 — ~~std HTTP client bodies are `str`~~ — closed 2026-10-31

`http_build_request_bytes` + `http_request_bytes` в std/net/http_client.baga:
хедъри като str, тяло като `bytes` (с null байтове). Content-Length от
`bytes_len`. Plain и TLS варианти. Този пакет продължава с raw TCP за S3,
но std клиентът вече носи binary bodies.

### A3 — ~~no chunked bodies~~ — closed 2026-10-31

`s3_parse` детектира `Transfer-Encoding: chunked` и декодира през
`s3_decode_chunked` (hex размер + CRLF + данни + CRLF, терминиращ 0-chunk).
Content-Length пътят остава за non-chunked отговори.

## Closed

### A2 — virtual-hosted style — closed 2026-10-31

`S3_STYLE=virtual` (or `vhost`): host = `bucket.endpoint_host`, uri = `/key`.
Default `path`: host = endpoint host, uri = `/bucket/key`. Signing uses the
resolved host/uri, so SigV4 is correct for both styles.
