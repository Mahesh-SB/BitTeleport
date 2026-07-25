# Chunk-Based Transfer and Azure Egress Cost

## Scenario

- Source: Azure Blob Storage
- Destination: AWS S3 (or any other cloud)
- File Size: **100 MB**
- Chunk Size: **5 MB**
- Total Chunks: **20**

---

## Case 1: All Chunks Transfer Successfully

- Azure reads and transfers all **20 chunks (100 MB)**.
- No retries are required.

| Item | Value |
|------|------:|
| Data transferred | 100 MB |
| Azure egress charged | **100 MB** |

**Conclusion:** Chunking does **not** reduce egress cost when the transfer succeeds on the first attempt.

---

## Case 2: 5 Chunks Fail

### First Attempt

- 20 chunks are read from Azure.
- 15 chunks succeed.
- 5 chunks fail.

| Item | Value |
|------|------:|
| Data transferred | 100 MB |
| Azure egress charged | **100 MB** |

### Retry

Only the failed chunks are read again.

- Failed chunks: **5**
- Chunk size: **5 MB**

```
5 × 5 MB = 25 MB
```

| Item | Value |
|------|------:|
| Data retransferred | 25 MB |
| Additional Azure egress | **25 MB** |

### Total Egress

| Attempt | Azure Egress |
|---------|-------------:|
| First transfer | 100 MB |
| Retry failed chunks | 25 MB |
| **Total** | **125 MB** |

---

## Case 3: No Chunking

If the entire 100 MB file must be retried after a failure:

| Attempt | Azure Egress |
|---------|-------------:|
| First transfer | 100 MB |
| Retry entire file | 100 MB |
| **Total** | **200 MB** |

---

# Summary

| Scenario | Azure Egress |
|----------|-------------:|
| Successful transfer | **100 MB** |
| Chunked transfer with 5 failed chunks | **125 MB** |
| Full file retry without chunking | **200 MB** |

## Key Takeaway

Chunking **does not reduce the cost of a successful transfer**.

Chunking **reduces retry cost** because only the failed chunks need to be read and transferred again, instead of retransferring the entire file.
