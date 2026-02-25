---
name: protect-asset
description: Protect a file with ProofX by computing its SHA-256 hash and registering it with a cryptographic signature and timestamp
---

# Protect Asset

Register any file with ProofX to create cryptographic proof of ownership.

## When to use
- Before deploying a project with images, audio, or video assets
- When a developer wants to timestamp and sign a specific file
- When preparing content for public release
- To create a tamper-proof record that a file existed at a specific time

## Instructions

1. Ask the user which file(s) to protect. Accept a path, glob pattern, or let them pick.

2. For each file, compute the SHA-256 hash:
   ```bash
   shasum -a 256 "<file_path>" | awk '{print $1}'
   ```

3. Determine the content type from the file extension:
   - Images: `image` (.png, .jpg, .jpeg, .gif, .webp, .svg)
   - Audio: `audio` (.mp3, .wav, .flac, .aac, .ogg)
   - Video: `video` (.mp4, .mov, .avi, .mkv, .webm)
   - Documents: `document` (.pdf, .doc, .docx, .txt)
   - Code: `code` (.js, .ts, .py, .swift, .go, .rs, .java)
   - Other: `file`

4. Use the ProofX MCP server's `protect_content` tool to register the content:
   - Provide: `content_hash`, `content_type`, `file_name`
   - The tool returns a `content_id` and verification URL

5. Present the result to the user:
   - Content ID for future reference
   - Verification URL: `https://proofx.co.uk/verify?id={content_id}`
   - Timestamp of when it was registered
   - Remind them the hash proves the file existed at this exact time

## Notes
- The file itself is never uploaded — only the hash is sent
- This requires the user to be authenticated via ProofX OAuth
- Multiple files can be protected in sequence
