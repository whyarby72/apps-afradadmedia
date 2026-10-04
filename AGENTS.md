# AGENTS.md — Apps AfradadMedia

## Canonical identity

- Project: **Apps AfradadMedia**
- Repository: `whyarby72/apps-afradadmedia`
- Production hostname: `apps.afradadmedia.com`
- Production document root: `/home/afradadm/apps.afradadmedia.com/`
- Repository is the source of truth for production web artifacts.

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

The target hosted verification profile is **V2 — Hosted Static / PWA**. Repository/static checks do not substitute for hosted-environment checks.

## Change control

1. Work on a branch, not directly on `main`.
2. Keep commits scoped and reviewable.
3. A PASS must be bound to the exact artifact/commit and verification environment.
4. Do not treat file existence, successful commit, PR creation, or deployment command success as proof of runtime correctness.
5. Record unresolved assumptions as HOLD/UNKNOWN rather than silently filling gaps.
6. Repair both the defect and the earliest reusable control that should have caught it.
7. Production payload is projected to the dedicated `deploy/production` branch; governance/source material must not be copied there.

## Release authority

Agents may prepare code, tests, evidence, pull requests, deployment instructions, and deployment candidates.

Agents must not:

- merge a release PR unless explicitly authorized;
- deploy to production unless explicitly authorized for that exact material state;
- infer `ARTIFACT_FREEZE` or `PUBLICATION` approval from general continuation;
- modify production files manually as a substitute for repository source-of-truth;
- expose secrets, tokens, private keys, or credentials.

Publication authorization and technical execution are separate states. A one-time deployment-probe approval is consumed by that exact deployment and does not authorize later deployments.

## Security and privacy

- Never commit secrets.
- Never place private keys, access tokens, account credentials, or service-account material in this repository.
- Disable directory listing for public deployment.
- Git metadata in the production document root must remain non-public; verify `/.git/`, `/.git/HEAD`, and `/.git/config` are denied.
- Prefer same-origin assets.
- Privacy pages should remain tracker-light and free of scripts that create avoidable consent dependencies.
- Do not publish an `app-ads.txt` value until the canonical publisher entry has been verified.

## Deployment

Verified production flow:

`Codex/ChatGPT → GitHub → deploy/production → human scoped approval → DomaiNesia Git Deploy → apps.afradadmedia.com → live verification`

Current DomaiNesia binding:

- Git Deploy mode: manual;
- repository: `git@github-apps-afradadmedia:whyarby72/apps-afradadmedia.git`;
- branch: `deploy/production`;
- authentication: dedicated read-only GitHub Deploy Key via SSH alias `github-apps-afradadmedia`;
- production document root: `/home/afradadm/apps.afradadmedia.com/`;
- `.cpanel.yml`: intentionally not used for the verified manual-deploy path.

DomaiNesia initializes a Git repository inside the production document root and preserves untracked hosting files. Therefore production verification uses:

`CLEAN_TRACKED_PLUS_HOSTING_ALLOWLIST`

not a universal strict-clean working-tree rule.

Canonical hosting allowlist is documented in `deployment/DOMAINESIA_HOSTING_ALLOWLIST.md`. Any new untracked top-level entry outside that allowlist is HOLD until classified. Any unexpected tracked modification remains HOLD/FAIL according to impact.
