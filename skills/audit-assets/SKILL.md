---
name: audit-assets
description: Scan a project directory for media assets and check which ones are protected with ProofX
---

# Audit Assets

Scan a project for media files and report their ProofX protection status.

## When to use
- Before deploying a project to production
- When onboarding a new project that contains media assets
- To get an overview of which assets are protected and which are not
- During a content audit or IP review

## Instructions

1. Scan the project for media files using common patterns:
   ```bash
   find . -type f \( -name "*.png" -o -name "*.jpg" -o -name "*.jpeg" -o -name "*.gif" -o -name "*.webp" -o -name "*.svg" -o -name "*.mp4" -o -name "*.mp3" -o -name "*.wav" -o -name "*.pdf" \) -not -path "*/node_modules/*" -not -path "*/.git/*" -not -path "*/dist/*" -not -path "*/build/*"
   ```

2. For each file found, compute the SHA-256 hash:
   ```bash
   shasum -a 256 "<file_path>" | awk '{print $1}'
   ```

3. Check each hash against ProofX using the `verify_hash` MCP tool.

4. Present a summary table:
   ```
   File                    | Status      | Content ID | Protected By
   public/logo.png         | Protected   | ab12cd34   | Raza Sharif
   public/hero.jpg         | Unregistered| —          | —
   assets/promo.mp4        | Protected   | ef56gh78   | Raza Sharif
   ```

5. Provide a summary:
   - Total assets found
   - Number protected
   - Number unregistered
   - Offer to protect unregistered assets using the `protect-asset` skill

## Notes
- Skip files in node_modules, .git, dist, build directories
- For large projects, limit to the first 50 files and note if more exist
- This requires ProofX authentication for the verification checks
