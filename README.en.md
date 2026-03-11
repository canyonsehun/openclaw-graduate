# openclaw-graduate

> 🌐 Language: [中文](./README.md) | **English (current)**

This repository mirrors the active local `openclaw` skill used for OpenClaw setup, operations, provider/model routing, remote Codespaces deployment, and troubleshooting.

## Contents

- `SKILL.md`: main skill instructions
- `references/`: topic-specific references
- `scripts/`: helper scripts
- `assets/`: bundled assets

## What It Covers

- **Install and repair**: `openclaw setup`, `openclaw doctor --repair`, `gateway start/restart/status`, `channels status`, and `agents list`
- **Provider and model switching**: working setups for `codex`, `anthropic / Claude`, and OpenAI-compatible relay providers, including defaults, fallbacks, and smoke tests
- **Bot and channel onboarding**: Telegram bot onboarding, agent binding, default model assignment, multi-bot routing, and `/model` catalog maintenance
- **Remote deployment**: GitHub Codespaces / github.dev bootstrap patterns, env-file driven startup, and `~/.secrets/openclaw.env` conventions
- **Plugin and memory diagnostics**: `memory-lancedb-pro`, Jina embedding checks, plugin registration failures, and session lock issues
- **Claude Code integration**: practical fallback flow when Claude Code works remotely and OpenClaw needs a usable execution path
- **Troubleshooting and verification**: concrete paths for 403 / 429, Cloudflare challenge pages, wrong-model routing, no-reply cases, malformed JSON, and provider config mistakes

## Highlights

- **Built from real operations**: distilled from actual local macOS and remote Codespaces runs, not just generic product documentation
- **Execution-ready guidance**: focuses on commands, file paths, verification steps, and failure signals
- **Local vs remote clarity**: explicitly separates what works locally, what fails remotely, and when a Claude fallback is the right move
- **Ops-first focus**: optimized for “why it broke”, “what to change”, and “how to confirm it is fixed”
- **Reusable helper scripts**: includes scripts for Telegram bot provisioning and relay model catalog sync

## Scope

- OpenClaw install, upgrades, and gateway ops
- Channel setup for Telegram / WhatsApp / Slack and more
- Provider/model configuration and switching
- Remote deployment on Codespaces / github.dev
- Troubleshooting 403 / 429, wrong-model routing, no-reply, session locks, and plugin issues

## Sync Policy

- Mirror only the current local `~/.codex/skills/openclaw` content
- Keep only operator-relevant procedures, commands, config, and troubleshooting conclusions
- Never commit real keys, tokens, or chat identifiers
