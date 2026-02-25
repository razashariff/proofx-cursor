---
name: protect
description: Protect a file or directory of files with ProofX
---

# Protect Files

Protect one or more files with ProofX cryptographic signatures.

## Steps

1. If a file path was provided, protect that specific file
2. If a directory was provided, find all media files in it
3. If nothing was specified, ask the user what to protect
4. For each file:
   - Compute SHA-256 hash using `shasum -a 256`
   - Call the ProofX MCP `protect_content` tool
   - Report the content ID and verification URL
5. Show a summary of all protected files
