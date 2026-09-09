# Telegram Support Ticket Bot (n8n + Ollama)

Local AI-powered support ticket classifier and auto-responder.

## Stack
- n8n (self-hosted, Docker)
- Telegram Bot API
- Ollama running gemma4:e4b locally
- Airtable for logging

## Workflow
See `workflow.json` for the full export.
See `screenshots/` for the canvas view and active/published status.

## How it works
1. Telegram Trigger receives the message
2. HTTP Request node sends it to local Ollama (gemma4:e4b) for classification
3. Code node parses the JSON category
4. Switch node routes to billing / technical / general / fallback
5. Each ticket is logged to Airtable
6. A distinct reply is sent back per category
7. One branch calls a live external API (Open-Meteo)
8. Errors (empty input, bad JSON, Ollama offline) are caught and handled gracefully