# Apify Expert — a ChatGPT / Codex skill

A Codex skill that serves as a **platform-knowledge hub for Apify** — Actors, runs, storage (Dataset / Key-value store / Request queue), Apify Proxy, schedules, webhooks, the REST API, the `apify` CLI, the JS/Python SDKs, Standby mode, and Store mechanics — plus a curated digest of recent platform changes so answers stay current.

It is built for the **ChatGPT / Codex skill format**: a `SKILL.md` entry point, an `agents/openai.yaml` interface descriptor, and a set of `references/*.md` baseline files loaded on demand.

## Why this skill exists

Apify platform facts drift. Default values, template names, storage limits, and Standby behavior all change over time, and notes that hard-code them go stale silently. This skill centralizes a curated baseline of platform mechanics and pairs it with a newest-first changelog digest, so a Codex session can check authoritative facts (and recent changes) **before** building, debugging, publishing, or updating an Actor — instead of answering from a stale memory.

## What it covers

- **Actors, runs, builds:** statuses, the memory↔CPU coupling (4096 MB = 1 vCPU), timeouts, resurrection, versioning, build tags.
- **Storage:** Dataset / Key-value store / Request queue semantics, retention, per-item limits, multiple-datasets support.
- **Apify Proxy:** datacenter / residential / SERP groups, sessions, geo-targeting, connection patterns (platform mechanism only).
- **Schedules, webhooks, integrations:** cron triggers, run-lifecycle webhooks, native integrations, monitoring.
- **CLI & SDKs:** the `apify` CLI command surface, `apify create` templates, JS/Python SDK lifecycle and helpers.
- **REST API:** base URL, auth, key endpoint families, pagination, the source-files exposure caveat.
- **Standby & Store:** Standby HTTP-server model, billing trap, cold start, idle timeout, Store mechanics, account plans/limits.
- **Changelog digest:** a curated, newest-first log of recent Apify platform changes.

## Scope

This skill explains **how the Apify platform behaves**. It is a *substrate*, not a substitute for deep domain work: scraper code & architecture, MCP-server code, pricing/PPE design, and Store README/schema authoring are separate concerns. The skill points those out rather than doing them.

## What's inside

```
apify-expert/
├── SKILL.md                          # Entry point: scope, freshness workflow, what it covers
├── README.md                         # This file
├── INSTALL.md                        # Installation instructions (Codex)
├── agents/
│   └── openai.yaml                   # ChatGPT/Codex interface descriptor + invocation policy
└── references/
    ├── platform-overview.md          # Actors, runs, builds, storage, proxy, schedules, webhooks
    ├── cli-and-sdk.md                # apify CLI commands, create templates, JS/Python SDK
    ├── api-and-integrations.md       # REST API, tokens, Apify MCP access pattern, integrations
    ├── platform-features.md          # Standby mode, Store mechanics, account/limits
    └── changelog-digest.md           # ⭐ newest-first digest of recent platform changes
```

## Installation

See `INSTALL.md`. This is a knowledge-only skill — no Python, no dependencies, no network calls. You drop the folder into your Codex skills directory and it activates on Apify platform questions.

## How to invoke

Once installed, the skill activates on Apify platform questions. Example prompts:

- "What's the current Standby idle-timeout behavior on Apify?"
- "How is CPU allocated relative to memory on an Apify Actor run?"
- "Did Apify change anything about datasets recently?"
- "What `apify create` templates are available right now?"
- "Use `apify-expert` to confirm the REST API auth pattern before I wire this up."

## Keeping it current

`references/changelog-digest.md` is maintained **by hand**. There is no automated updater shipped with this skill. To keep it useful, periodically review <https://apify.com/change-log>, add new entries newest-first under the insertion marker, and update the baseline `references/*` files when an entry changes a fact they state. Refresh on whatever cadence suits you.

## What's NOT inside

- **Scraper code & architecture** (Crawlee crawlers, no-code config, template internals): a scraper-building concern.
- **MCP server code & architecture** (proxy template, Standby wiring): an MCP-server-building concern.
- **Pricing / PPE / `Actor.charge` / revenue:** a monetization concern.
- **README / input-output schemas / Store description:** an Actor-content-authoring concern.
- **Anti-bot doctrine, proxy strategy, hidden APIs:** a scraping-strategy concern.

This skill provides the platform facts those tasks build on; it does not perform them.

## Part of the mr-bridge.com toolkit

This skill is part of the [mr-bridge.com](https://mr-bridge.com) toolkit for scraping, data, and content automation. Related resources:

- [mr-bridge.com](https://mr-bridge.com) — home
- [Scrapers](https://mr-bridge.com/scrapers) — the Apify Actor portfolio
- [MCP servers](https://mr-bridge.com/mcp-servers) — Model Context Protocol servers
- [AI workflows](https://mr-bridge.com/ai-workflows) — agents and automation
- [Studies](https://mr-bridge.com/studies) — data studies and one-pagers
- [Articles](https://mr-bridge.com/articles) — write-ups and guides
- [Solutions](https://mr-bridge.com/solutions) — end-to-end solutions

## License

Personal use. Customize freely. No warranty. Platform facts are curated from public Apify documentation and the official changelog; verify drift-prone figures (flagged *(verify)* in the reference files) against <https://docs.apify.com> before quoting them as hard limits.
