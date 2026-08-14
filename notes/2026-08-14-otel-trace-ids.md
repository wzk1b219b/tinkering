# Trace ID lengths

Quick ref for OTel trace/span IDs (32 hex / 16 hex).

- Trace ID: 16 bytes (32 hex chars)
- Span ID: 8 bytes (16 hex chars)

W3C traceparent uses 32-16 format. Keep this in mind when parsing logs.
