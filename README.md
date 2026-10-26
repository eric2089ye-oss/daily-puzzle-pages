# Daily puzzle answers — static build pipeline

Cloudflare Pages build pipeline for a daily puzzle-answers website.

- Data and build code live in a private Cloudflare KV namespace; this repo holds
  no site code, domains, project names or credentials (all injected via secrets).
- Workflow: pull data + build scripts + edge middleware + static bundle from KV,
  build the static site, deploy to Cloudflare Pages, ping IndexNow, verify live.
- Triggered by the collector Worker via `repository_dispatch` (`data-updated`),
  plus a 05:35 UTC schedule backstop and a manual `force` repair escape hatch.
