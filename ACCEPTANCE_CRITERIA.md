# Bootstrap Acceptance Criteria

## Gate: Repository Foundation

This gate covers repository structure only. It does **not** authorize deployment or publication.

### Required

- [x] Repository is private.
- [x] Default branch is `main`.
- [x] Bootstrap work occurs on a non-main branch.
- [ ] Pull request is open and reviewable.
- [ ] `AGENTS.md` defines scope, source-of-truth, release boundaries, and secret handling.
- [ ] `PROJECT_STATE.json` is valid JSON and reports deployment/publication as not authorized.
- [ ] `public/index.html` is self-contained and has no external runtime dependency.
- [ ] `public/.htaccess` disables directory indexes.
- [ ] `public/robots.txt` prevents indexing during bootstrap.
- [ ] Deployment documentation records the observed production target but treats command/runtime details as unverified.
- [ ] No `.cpanel.yml` production deployment contract exists before cPanel environment audit.
- [ ] No privacy, data-safety, AdMob, SDK, retention, deletion, or tracking claim is fabricated.

## Static semantic checks

Before merge, verify against the branch commit:

1. HTML parses without obvious structural errors.
2. The page contains exactly one primary `h1`.
3. The page has a descriptive `title` and viewport metadata.
4. No external `script`, stylesheet, image, font, iframe, analytics, or tracking request is required.
5. No secrets or credentials are present.
6. `.htaccess` includes `Options -Indexes`.
7. `robots.txt` blocks crawling during bootstrap.
8. JSON files parse successfully.

## Hosted environment checks — HOLD until deployment integration

These cannot be marked PASS from repository inspection alone:

- DNS resolution;
- TLS certificate state;
- HTTP→HTTPS redirect behavior;
- cPanel Git clone/pull/deploy behavior;
- exact executable paths used by deployment tasks;
- `.htaccess` override support;
- directory-index behavior on the live vhost;
- response headers;
- cache behavior;
- live `app-ads.txt` reachability;
- live privacy/support page reachability.

Each hosted PASS must identify:

- exact Git commit;
- exact URL/environment;
- observed timestamp;
- command/browser used;
- machine-observable result;
- replay steps.

## Release boundary

Merge to `main` is not publication approval.

Deployment to `apps.afradadmedia.com` requires an explicit, material-state-bound human release/publication decision after the applicable verification evidence has been reviewed.
