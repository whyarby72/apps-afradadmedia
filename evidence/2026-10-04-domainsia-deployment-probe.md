# Evidence — DomaiNesia Deployment Probe — 2026-10-04

## Scope

Project: **Apps AfradadMedia**

Verification profile: `V2_HOSTED_STATIC`

Production URL:

`https://apps.afradadmedia.com/`

Production document root:

`/home/afradadm/apps.afradadmedia.com/`

GitHub repository:

`whyarby72/apps-afradadmedia`

Deployment branch:

`deploy/production`

Authorized/deployed commit:

`099992d84875818cbb246103fa89731ef7c77e73`

## Deployment execution evidence

DomaiNesia Git Deploy reported:

- deployment started: 2026-10-04 19:21:40 local operator context;
- document root matched the expected production path;
- `git init` exit: 0;
- shallow fetch of `deploy/production` exit: 0;
- checkout of `FETCH_HEAD` exit: 0;
- deployed HEAD: `099992d`;
- deployment completed: 2026-10-04 19:21:43;
- UI status: Success.

The deployment mechanism produced detached HEAD at the fetched commit. This is treated as expected behavior for the verified DomaiNesia Git Deploy path.

## GitHub authentication evidence

Private repository read path used:

- dedicated ED25519 key stored on the DomaiNesia server;
- GitHub Deploy Key title: `DomaiNesia — apps.afradadmedia.com — Read Only`;
- exact-title match count: 1;
- read-only status: true;
- SSH alias: `github-apps-afradadmedia`;
- repository read test: PASS;
- `refs/heads/main`: found;
- `refs/heads/deploy/production`: found.

No private-key material is recorded in this repository.

## Artifact-bound checks

Expected tracked payload:

- `.htaccess`;
- `index.html`;
- `robots.txt`.

Results:

- deployed commit exact match: PASS;
- tracked public files exact match: PASS;
- tracked Git drift: NONE;
- HTTP→HTTPS redirect: PASS;
- HTTPS root response: PASS;
- expected bootstrap content: PASS;
- `robots.txt`: PASS;
- `README.md` publicly exposed: NO;
- `AGENTS.md` publicly exposed: NO;
- `PROJECT_STATE.json` publicly exposed: NO;
- `/.git/HEAD` publicly exposed: NO;
- `/.git/config` publicly exposed: NO;
- `/.git/` publicly browseable: NO;
- security verification: PASS.

## Environment fingerprint

Remote preflight reported:

- remote home: `/home/afradadm`;
- Git: `2.48.2`;
- OpenSSH: `OpenSSH_9.9p1, OpenSSL 3.5.8`;
- server OS: Linux `marsala.id.rapidplex.com`, kernel `6.12.0-211.56.1.el10_2.x86_64`;
- production document root existence: PASS.

## Hosting residue finding

Initial full working-tree cleanliness check returned HOLD because these top-level untracked entries existed:

- `.user.ini`;
- `.well-known/`;
- `php.ini`.

A follow-up read-only classification established:

- tracked Git drift: NONE;
- untracked drift fully explained by those three entries: YES;
- `.user.ini`: `HOSTING_MANAGED_LIKELY`, HTTP 403;
- `php.ini`: `HOSTING_MANAGED_LIKELY`, HTTP 403;
- `.well-known/`: `HOSTING_MANAGED_LIKELY`, child `acme-challenge`, HTTP 403;
- credential-like content detected: NO;
- security result: PASS.

## Verification-control repair

The original `STRICT_CLEAN` working-tree assumption was too strong for this hosting environment because DomaiNesia preserves hosting-managed untracked files.

Repaired model:

`CLEAN_TRACKED_PLUS_HOSTING_ALLOWLIST`

Canonical allowlist:

`deployment/DOMAINESIA_HOSTING_ALLOWLIST.md`

This repair changes the verifier, not the public artifact.

## Claim ceiling

This evidence supports:

- GitHub private repository → DomaiNesia manual Git Deploy works for the tested branch/commit;
- exact tracked artifact can be deployed and verified;
- expected HTTPS bootstrap surface is reachable;
- tested internal/Git metadata paths were not publicly exposed;
- the current hosting-residue allowlist is benign at the tested checkpoint.

This evidence does **not** support:

- final Apps AfradadMedia website readiness;
- `app-ads.txt` correctness;
- app-specific privacy/data-flow claims;
- per-app support/privacy page correctness;
- CI/CD readiness;
- future deployment authorization;
- Artifact Freeze;
- final Publication authorization.

## Governance

The one-time deployment-probe authorization for commit `099992d84875818cbb246103fa89731ef7c77e73` was consumed by this deployment.

No continuing deployment/publication authorization is implied.
