# ProofX — Content Protection for Cursor

Protect and verify your digital content directly from Cursor. ProofX creates cryptographic proof of ownership for any file — images, audio, video, code, documents — with timestamped digital signatures.

## What This Plugin Does

| Feature | Description |
|---------|-------------|
| **Protect** | Hash and sign any file to prove you owned it at a specific time |
| **Verify** | Check if content is registered with ProofX by ID or file hash |
| **Audit** | Scan your project for unprotected media assets before deploying |
| **API Guide** | Rules and guidance for integrating ProofX into your apps |

## How It Works

1. **Files never leave your machine** — only the SHA-256 hash is sent to ProofX
2. ProofX signs the hash with a cryptographic key and timestamps it
3. You get a `content_id` and verification URL proving ownership
4. Anyone can verify your content at `proofx.co.uk/verify?id={content_id}`

## Quick Start

After installing the plugin, authenticate with your ProofX account when prompted by the MCP server.

Then use natural language:

- *"Protect all images in my public/ folder"*
- *"Is this photo registered with ProofX?"*
- *"Audit my project for unprotected assets"*
- *"Verify content ID ab12cd34"*
- *"Help me integrate the ProofX API into my Next.js app"*

## Components

### Skills
- **protect-asset** — Hash + sign files for cryptographic proof of ownership
- **verify-content** — Check content by ID or file hash
- **audit-assets** — Scan project for unprotected media files

### Rules
- **content-protection** — Best practices for ProofX API integration
- **asset-hygiene** — Reminders to protect media assets before deployment

### Agent
- **proofx-assistant** — Content protection specialist for your projects

### Commands
- **protect** — Protect files with ProofX signatures
- **verify** — Verify content registration
- **audit** — Scan project assets

### MCP Server
Connects to `proofx-mcp.fly.dev` for:
- `protect_content` — Register content with cryptographic signature
- `verify_content` — Verify by content ID
- `verify_hash` — Verify by SHA-256 hash
- `get_creator` — Look up creator profiles
- `my_account` — View your ProofX account
- `compute_hash` — Compute content hash

## ProofX API

For developers building with ProofX:

- **Base URL**: `https://api.proofx.co.uk`
- **Docs**: `https://proofx.co.uk/developer`
- **API Keys**: Generate at `proofx.co.uk/developer` (format: `pk_live_` + 32 hex)

## Links

- [ProofX Website](https://proofx.co.uk)
- [Developer Portal](https://proofx.co.uk/developer)
- [API Documentation](https://proofx.co.uk/developer)
- [Verify Content](https://proofx.co.uk/verify)

## License

MIT
