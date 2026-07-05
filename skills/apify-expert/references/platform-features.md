# Standby mode, Store mechanics & account

Platform features that cut across building, pricing, and publishing. Confirm limits against <https://docs.apify.com>.

## Standby mode

Runs an Actor as a **persistent HTTP server** that stays warm and answers incoming requests, instead of the run-once-then-exit model. Powers MCP servers and real-time APIs.

- **HTTP:** standard methods (GET/POST/PUT/DELETE). Input via query string or request body.
- **Auth:** Bearer token in `Authorization`, or `?token=` query param.
- **Web server wiring:** the Actor must listen on the port given by `ACTOR_WEB_SERVER_PORT`; its public URL is in `ACTOR_WEB_SERVER_URL`. `APIFY_META_ORIGIN=STANDBY` signals a Standby invocation (vs a normal run).
- **Limits (verified 2026-06):** **2,000 requests/sec** per user account; **5-minute** maximum for the initial response.
- **Cold start:** when Standby scales up a new run, the first request waits a few seconds for warm-up. Keep init light to minimize it.
- **Idle timeout:** configurable (seconds). No requests within the window → the run terminates. Higher timeout = more responsive but more compute billed.
- **Billing:** Standby runs are billed **the same way as normal runs** (memory-GB × runtime), *including idle time while warm* - a real cost trap for low-traffic Standby Actors. PPE event charging still applies on top.
- **Interactive OpenAPI docs (2026-05-05):** Standby Actors that ship an OpenAPI spec now expose an **Endpoints** tab in Console to browse/test calls.

## Apify Store mechanics

- Public Actors appear in the **Store** with a README, input/output schemas, an Examples tab, reviews/ratings, and a changelog tab.
- **Pricing models:** Free, **Pay-per-event (PPE)**, Pay-per-usage, and legacy **Rental** (being phased out). Model choice + implementation is a monetization concern.
- **SEO & content:** Store title, slug, description, README, schema descriptions - an Actor-content-authoring concern.
- **`isSourceCodeHidden`** hides source in the UI only (the API still exposes source files to authenticated users - keep non-shippable files out of the push).
- **Full-permission Actors (2026-05-04):** Actors requesting full account permissions now trigger a **one-time approval modal** before first run - a security gate that especially affects AI-agent Actors. Factor this into onboarding/UX expectations.

## Account, limits & plans

- **Plans:** Free, Starter, Scale, Business, Enterprise - differ in monthly compute credits, max Actor memory, concurrent runs, data-retention period, and proxy access. Confirm current tiers/prices at <https://apify.com/pricing>.
- **Data retention:** unnamed/default storages expire after the plan's retention period; named storages persist (see `platform-overview.md`).
- **Cost levers (pick the cheapest viable config):** minimum RAM that runs the workload (256 MB MCP, 1024–2048 MB HTTP scrapers, 4096 MB Camoufox/Playwright), residential proxy only when datacenter fails, KV-store caching to avoid re-fetching.

## Related platform topics

- Memory↔CPU, storage, proxy, runs → `references/platform-overview.md`
- REST API, MCP access pattern → `references/api-and-integrations.md`
- CLI & SDK surface → `references/cli-and-sdk.md`
