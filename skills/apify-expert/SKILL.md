---
name: apify-expert
description: Current Apify platform guidance for Actors, runs, storage, Proxy, Standby, Store mechanics, CLI, SDKs, REST API, integrations, and recent platform changes. Use when Codex needs authoritative Apify facts or freshness checks before building, debugging, publishing, or updating an Actor.
---

# Apify Expert — platform-knowledge hub

A single source of truth for **Apify platform facts**. This skill owns *platform mechanics* and keeps a curated changelog digest as a freshness signal when recent platform changes may affect how you build or operate an Actor.

## Core principle

Platform facts drift. Notes that hard-code "Standby idle timeout default is X" or "templates are A/B/C" go stale silently. This skill centralizes a curated baseline. `references/changelog-digest.md` records recent platform changes from <https://apify.com/change-log>; verify recency before treating it as current. Everything else in this skill cross-references the baseline files instead of duplicating facts (and risking divergence).

## What this skill covers

| Topic | Where it lives |
|---|---|
| Actors, runs, builds, versioning/tags, memory↔CPU, resurrection | `references/platform-overview.md` |
| Storage: Dataset / Key-value store / Request queue, retention, limits | `references/platform-overview.md` |
| Apify Proxy: datacenter / residential / SERP, sessions, geo | `references/platform-overview.md` |
| Schedules, webhooks, native integrations, monitoring | `references/platform-overview.md` |
| `apify` CLI commands, JS/Python SDK, `apify create` templates | `references/cli-and-sdk.md` |
| REST API, tokens, scheduling via API, Apify MCP access pattern | `references/api-and-integrations.md` |
| Standby mode platform behavior, Store mechanics, account/limits | `references/platform-features.md` |
| **Recent platform changes** | `references/changelog-digest.md` |

## Scope — what this skill is NOT for

This skill gives you the *platform substrate* (e.g. "how Standby billing works", "current storage limits"). It is **not** a substitute for deep domain work. When a question is really about one of the following, treat it as a separate concern and reach for the appropriate specialized tooling or documentation:

| If the question is about… | Treat as… |
|---|---|
| Scraper Actor **code & architecture** (Crawlee, templates, no-code config) | scraper-building work |
| MCP server Actor **code & architecture** (proxy template, Standby wiring) | MCP-server-building work |
| **Pricing / PPE / `Actor.charge` / revenue** | monetization work |
| **README / input-output schemas / Store description / bios** | Actor-content-authoring work |
| **Anti-bot doctrine, tool ladder, hidden APIs** | scraping-strategy work |
| **Auditing** an existing scraper | scraper-audit work |

This skill explains *how the platform behaves*; it does not design scrapers, write pricing, or author Store copy.

## Freshness workflow

Before relying on platform-sensitive facts, inspect `references/changelog-digest.md` and, when necessary, verify against Apify's official docs or changelog. Do not assume the digest is automatically current; it is a curated reference that someone keeps up to date by hand. Entries tagged with an impacted area (see the digest legend) flag content that may need updating after a platform change.

## Keeping the digest current

`references/changelog-digest.md` is maintained **manually**. To keep it useful, periodically review <https://apify.com/change-log>, add new entries newest-first under the insertion marker, and update the baseline `references/*` files when an entry changes a fact they state. There is no automated updater shipped with this skill — refresh it on whatever cadence suits you.

## Freshness contract

- `references/*` = curated baseline, edited by hand when a digest entry warrants it.
- `changelog-digest.md` = newest-first log of recent platform changes; verify recency before using it for publication-sensitive decisions.
