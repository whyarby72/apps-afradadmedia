# Bootstrap Acceptance Criteria

## Gate: Repository + Deployment Foundation

This gate covers the repository foundation and the verified one-time deployment probe. It does **not** authorize future deployment, final publication, `app-ads.txt`, privacy-policy publication, or application-page publication.

### Repository foundation

- [x] Repository is private.
- [x] Default branch is `main`.
- [x] Bootstrap work occurs on a non-main branch.
- [x] Draft pull request is open and reviewable.
- [x] `AGENTS.md` defines scope, source-of-truth, release boundaries, secret handling, and deployment verification model.
- [x] `PROJECT_STATE.json` is valid JSON.
- [x] `public/index.html` is self-contained and has no external runtime dependency.
- [x] `public/.htaccess` disables directory indexes.
- [x] `public/robots.txt` prevents indexing during bootstrap.
- [x] No privacy, data-safety, AdMob, SDK, retention, deletion, or tracking claim is fabricated.

## Static semantic checks

Verified for the bootstrap artifact:

1. HTML contains exactly one primary `h1`.
2. The page has a descriptive `title` and viewport metadata.
3. No external script, stylesheet, image, font, iframe, analytics, or tracking request is required.
4. `.htaccess` includes `Options -Indexes`.
5. `robots.txt` blocks crawling during bootstrap.
6. JSON project state parses successfully.

## Verified DomaiNesia deployment environment

The first authorized deployment probe used:

- production hostname: `apps.afradadmedia.com`;
- document root: `/home/afradadm/apps.afradadmedia.com/`;
- GitHub repository: `whyarby72/apps-afradadmedia`;
- deployment branch: `deploy/production`;
- deployed commit: `099992d84875818cbb246103fa89731ef7c77e73`;
- Git Deploy mode: manual;
- GitHub authentication: dedicated read-only SSH Deploy Key;
- SSH alias: `github-apps-afradadmedia`.

Hosted checks verified for that exact deployment probe:

- [x] HTTP→HTTPS redirect works.
- [x] HTTPS root returns the expected bootstrap artifact.
- [x] Expected bootstrap content is present.
- [x] `robots.txt` is reachable with the expected blocking content.
- [x] `README.md`, `AGENTS.md`, and `PROJECT_STATE.json` are not publicly exposed.
- [x] `/.git/HEAD`, `/.git/config`, and `/.git/` are not publicly exposed/browseable.
- [x] Deployed Git HEAD matches the authorized exact commit.
- [x] Tracked deployment files match the expected payload.
- [x] No tracked Git drift exists.

## Verification-control repair: hosting residue

The original strict requirement that `git status` be completely clean is **superseded for this DomaiNesia environment**.

DomaiNesia preserves untracked hosting-managed entries in the document root. The verified model is:

`CLEAN_TRACKED_PLUS_HOSTING_ALLOWLIST`

Allowed top-level hosting residue:

- `.user.ini`;
- `php.ini`;
- `.well-known/`.

These entries were classified `HOSTING_MANAGED_LIKELY`, contained no credential-like material in the inspected directives, and returned HTTP 403 when tested publicly.

Rules:

1. tracked Git drift must remain absent unless an approved deployment changes the tracked artifact;
2. the three allowlisted hosting residues do not make the deployment HOLD by themselves;
3. any new untracked top-level entry outside the allowlist is HOLD until classified;
4. any allowlisted entry that becomes publicly exposed, changes purpose materially, contains credentials, or creates a security conflict invalidates the PASS;
5. do not delete hosting-managed residue merely to make `git status` appear clean.

## Still HOLD / not yet applicable

The following remain unresolved or not yet produced:

- final Apps AfradadMedia hub content;
- canonical `app-ads.txt` publisher entry;
- product-specific privacy/data-flow truth;
- per-app privacy/support pages;
- production indexing/SEO policy after bootstrap;
- final Artifact Freeze;
- future publication/deployment authorization.

## Evidence requirements for future hosted PASS

Each material hosted PASS must identify:

- exact Git commit;
- exact URL/environment;
- observed timestamp;
- command/browser/runtime;
- machine-observable result;
- replay steps;
- tracked-tree state;
- untracked entries reconciled against the current hosting allowlist.

## Release boundary

Merge to `main` is not publication approval.

The one-time deployment-probe authorization for commit `099992d84875818cbb246103fa89731ef7c77e73` has been consumed. Any later material deployment requires a new scoped approval for the exact candidate state.
