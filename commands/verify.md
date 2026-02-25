---
name: verify
description: Verify content by ProofX content ID or file hash
---

# Verify Content

Check if content is registered and protected with ProofX.

## Steps

1. If a content ID was provided (8 hex characters), verify it directly
2. If a file path was provided, compute its SHA-256 hash first
3. Call the appropriate ProofX MCP tool (`verify_content` or `verify_hash`)
4. Display the verification result:
   - Creator name and ID
   - Protection date and timestamp
   - Content type
   - Verification URL
5. If not found, offer to protect the file
