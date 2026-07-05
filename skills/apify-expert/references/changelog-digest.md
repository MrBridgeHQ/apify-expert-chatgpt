# Apify changelog digest

**Newest-first.** Curated digest from <https://apify.com/change-log>. Verify recency against official Apify sources before publication-sensitive decisions; stable facts live in the other `references/*` files.

**Format per entry:**
```
## YYYY-MM-DD - <title>  [<area tag(s)>]
<1–2 sentence digest of what changed + why it matters.>
Source: https://apify.com/change-log
```

**Area tags** describe which part of the platform an entry touches (e.g. `Actor`, `Console`, `Integrations`, `MCP`, `Storage`). Use them to decide whether a change affects what you are building or operating.

This digest is maintained **by hand**. Periodically review the official changelog and add new entries under the marker below, newest-first; update the baseline `references/*` files when an entry changes a fact they state.

---

<!-- INSERT-NEW-ENTRIES-BELOW - new changelog entries go directly under this marker, newest-first. Do not remove this marker. -->

## 2026-06-09 - MCP connectors are live. Actors now work where you do.  [Console, Actor, Integrations, MCP]
Apify Actors can now securely connect to third-party apps that require login (Notion, Slack, GitHub, etc.) via **MCP connectors** - Apify manages the OAuth/credential handshake so the Actor (and the end user) never needs to handle tokens manually. This is a significant new capability for Standby/MCP Actors that call authenticated external services.
Source: https://apify.com/change-log

## 2026-05-05 - Interactive OpenAPI documentation for Standby Actors  [Actor]
Standby Actors that ship an OpenAPI spec now expose an **Endpoints** tab in Console to browse and test API calls in-browser. Relevant for documenting MCP/Standby Actors and for the API tab of Store listings.
Source: https://apify.com/change-log

## 2026-05-04 - Full-permission Actors now require approval  [Actor, Console]
Actors requesting full account permissions now trigger a **one-time confirmation modal** before first run - a security gate aimed at AI-agent Actors. Affects onboarding UX expectations for permission-heavy Actors.
Source: https://apify.com/change-log

## 2026-04-23 - Deploy agents faster with an improved MCP configurator  [Integrations, MCP]
The Apify MCP configurator was redesigned with a simpler flow to connect Apify across multiple LLM clients, speeding up agent setup.
Source: https://apify.com/change-log

## 2026-04-23 - Multiple datasets for Actors  [Actor]
Actors can now output to **multiple datasets simultaneously**, each with its own schema and validation rules - previously a run wrote to a single default dataset. Affects output-schema design and scraper architecture.
Source: https://apify.com/change-log

## 2026-04-02 - Edit Actor build tags in Apify Console  [Actor, Console]
Build tags can be added, removed, and reassigned directly in Console without rebuilding.
Source: https://apify.com/change-log

---

_Baseline established 2026-06-04 from the changelog's most recent visible entries. Entries before 2026-04-02 were not backfilled. Move entries older than ~18 months to an archive file if this digest grows long._
