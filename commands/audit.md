---
name: audit
description: Scan the current project for media assets and check their ProofX protection status
---

# Audit Project Assets

Scan the project for media files and check which are protected.

## Steps

1. Find all media files in the project (images, audio, video, documents)
2. Skip node_modules, .git, dist, build directories
3. Compute SHA-256 hash for each file
4. Check each hash against ProofX registry
5. Display results as a table showing protection status
6. Offer to protect any unregistered files
