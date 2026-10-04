# Deployment Integration — VERIFIED FOUNDATION

## Production target

- Hostname: `apps.afradadmedia.com`
- Document root: `/home/afradadm/apps.afradadmedia.com/`
- Hosting: DomaiNesia / cPanel
- GitHub source: `whyarby72/apps-afradadmedia`
- Deployment branch: `deploy/production`

## Verified release flow

`Codex / ChatGPT → GitHub → deploy/production → scoped human approval → DomaiNesia Git Deploy → live verification`

Production should consume an approved Git state. Manual editing in the document root must not become the normal source-of-truth workflow.

## DomaiNesia Git Deploy behavior

The verified manual deployment path:

1. initializes/uses a Git repository directly inside the domain document root;
2. fetches the configured branch shallowly;
3. checks out `FETCH_HEAD` in detached-HEAD state;
4. overwrites tracked files with the fetched repository version;
5. preserves untracked files.

The first probe deployed exact commit:

`099992d84875818cbb246103fa89731ef7c77e73`

The detached-HEAD state is expected for this deployment mechanism and is not a defect by itself.

## Private repository authentication

Verified least-privilege path:

- dedicated server-side ED25519 key;
- GitHub Deploy Key title: `DomaiNesia — apps.afradadmedia.com — Read Only`;
- GitHub Deploy Key is read-only;
- SSH alias: `github-apps-afradadmedia`;
- configured remote: `git@github-apps-afradadmedia:whyarby72/apps-afradadmedia.git`.

No private key, PAT, cPanel password, or credential belongs in this repository.

## Deployment payload boundary

The public deployment branch is `deploy/production`.

The bootstrap probe payload was exactly:

- `.htaccess`;
- `index.html`;
- `robots.txt`.

Governance files, evidence records, source notes, and internal project state are not deployment payload.

## Hosting-managed residue

DomaiNesia preserves untracked entries. The verified environment contains:

- `.user.ini`;
- `php.ini`;
- `.well-known/` with `acme-challenge`.

These are classified `HOSTING_MANAGED_LIKELY` for the current environment. Their public directory/file access tests returned HTTP 403, and no credential-like material was detected in the inspected PHP directive names.

Use the canonical environment-specific allowlist in:

`deployment/DOMAINESIA_HOSTING_ALLOWLIST.md`

## Verification model

Use:

`CLEAN_TRACKED_PLUS_HOSTING_ALLOWLIST`

Do **not** require a universally empty `git status` on this host.

A deployment is eligible for PASS only when:

- exact deployed commit matches the approved candidate;
- tracked Git drift is absent;
- tracked public files match expected payload;
- all untracked top-level entries are reconciled against the current allowlist;
- Git metadata is not publicly exposed;
- internal governance files are not publicly exposed;
- HTTP/TLS/content checks pass for the declared candidate;
- unexpected residue or changed allowlist semantics produce HOLD until reviewed.

## CI/CD

`Enable CI/CD` and `.cpanel.yml` are intentionally **not** part of the verified production path.

Manual deployment remains the baseline because it preserves an explicit human release boundary between GitHub state and public production state.

## Publication boundary

A successful fetch/checkout proves technical execution only.

The first probe's one-time publication/deployment approval has been consumed. Future deployments require a new scoped approval for the exact candidate material state.
