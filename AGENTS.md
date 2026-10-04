# AGENTS.md — Apps AfradadMedia

## Canonical identity

- Project: **Apps AfradadMedia**
- Repository: `whyarby72/apps-afradadmedia`
- Production hostname: `apps.afradadmedia.com`
- Hosting target observed in cPanel: `/home/afradadm/apps.afradadmedia.com/`
- Repository is the source of truth for production web artifacts once deployment is enabled.

## Product scope

This repository is the shared static web hub for Afradad Media Android/AdMob products. Intended public surfaces include:

- publisher/app hub pages;
- per-app landing pages;
- per-app privacy policies;
- per-app support pages;
- shared `app-ads.txt`;
- other publisher compliance/support surfaces when explicitly specified.

Do not infer product-specific privacy claims, SDK behavior, data collection, retention, deletion, or advertising behavior. Those claims require evidence from the corresponding app/source-of-truth.

## Engineering profile

Prefer static-first delivery:

- HTML;
- CSS;
- minimal JavaScript only when required;
- no database;
- no server-side framework;
- no analytics, trackers, ad tags, consent scripts, or third-party runtime dependencies unless explicitly approved.

The target hosted verification profile is **V2 — Hosted Static / PWA**. Before hosting exists, local/static checks do not prove the hosted environment.

## Change control

1. Work on a branch, not directly on `main`.
2. Keep commits scoped and reviewable.
3. A PASS must be bound to the exact artifact/commit and verification environment.
4. Do not treat file existence, successful commit, or successful PR creation as proof of runtime correctness.
5. Record unresolved assumptions as HOLD/UNKNOWN rather than silently filling gaps.
6. Repair both the defect and the earliest reusable control that should have caught it.

## Release authority

Agents may prepare code, tests, evidence, pull requests, and deployment instructions.

Agents must not:

- merge a release PR unless explicitly authorized;
- deploy to production unless explicitly authorized for that exact material state;
- infer `ARTIFACT_FREEZE` or `PUBLICATION` approval from general continuation;
- modify production files manually as a substitute for repository source-of-truth;
- expose secrets, tokens, private keys, or credentials.

Publication authorization and technical execution are separate states.

## Security and privacy

- Never commit secrets.
- Never place private keys, access tokens, account credentials, or service-account material in this repository.
- Disable directory listing for public deployment.
- Prefer same-origin assets.
- Privacy pages should remain tracker-light and free of scripts that create avoidable consent dependencies.
- Do not publish an `app-ads.txt` value until the canonical publisher entry has been verified.

## Deployment

Deployment configuration is intentionally **not finalized** in this bootstrap branch.

Do not create a production `.cpanel.yml` until the DomaiNesia/cPanel Git deployment environment has been inspected and command paths/behavior are verified.

The intended model is:

`Codex/ChatGPT → GitHub → verified release → human approval → DomaiNesia/cPanel → apps.afradadmedia.com`

