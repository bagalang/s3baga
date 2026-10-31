# s3baga

Path-style S3 client for content-addressed blobs. AWS Signature Version 4.
Binary bodies stay `bytes` (the std HTTP client is text-only).

| | |
|--|--|
| **sandak** | `s3baga` **0.1.0** |
| **Deps** | std |

```baga
// SECP_BLOB=s3
// S3_ENDPOINT=http://127.0.0.1:9000
// S3_BUCKET=secp
// S3_REGION=us-east-1
// S3_STYLE=path            # or "virtual" for bucket.endpoint host style
// S3_ACCESS_KEY=...
// S3_SECRET_KEY=...
s3_put("blobs/aa/bb/<sha256>", body)?
```

Chunked responses and multipart upload are not in 0.1.0. Virtual-hosted
style (`S3_STYLE=virtual`) is supported since 2026-10-31.

## License

[MIT](LICENSE) — Copyright (c) 2026 Dim Gigov.
