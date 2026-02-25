---
name: verify-content
description: Verify if content is ProofX-protected by checking its hash or content ID against the registry
---

# Verify Content

Check whether a file or content ID is registered with ProofX.

## When to use
- To check if an image, audio, or video file has been protected by someone
- To verify a ProofX content ID is legitimate
- When investigating the provenance of third-party content
- To confirm your own content was successfully protected

## Instructions

### Verify by Content ID
1. If the user provides a content ID (format: 8 hex characters like `ab12cd34`):
   - Use the ProofX MCP server's `verify_content` tool with the `content_id`
   - Show: creator name, protection date, content type, verification status

### Verify by File Hash
1. If the user provides a file path:
   - Compute SHA-256: `shasum -a 256 "<file_path>" | awk '{print $1}'`
   - Use the ProofX MCP server's `verify_hash` tool with the hash
   - If found: show the matching content record with creator info
   - If not found: inform the user the file is not in the ProofX registry

### Verify by URL
1. If the user provides a URL to a verification page:
   - Extract the content ID from the URL query parameter
   - Use `verify_content` with that ID

## Output
Present results clearly:
- **Protected**: Show creator, date, content type, and verification URL
- **Not found**: State that the content is not registered with ProofX
- Never claim content is "unprotected" in a negative sense — it may simply not be registered yet
