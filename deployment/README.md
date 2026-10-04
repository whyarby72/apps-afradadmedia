# Deployment Integration — HOLD

## Intended production target

- Hostname: `apps.afradadmedia.com`
- Observed cPanel document root: `/home/afradadm/apps.afradadmedia.com/`
- Hosting: DomaiNesia/cPanel
- GitHub source: `whyarby72/apps-afradadmedia`

The hostname/document-root mapping and HTTPS redirect were observed during the hosting setup flow. They must still be revalidated as part of the actual deployment evidence pack.

## Intended release flow

`Codex / ChatGPT → GitHub → verification → human release approval → cPanel Git deployment → live verification`

The production server should consume an approved Git state. Manual editing in the production document root should not become the normal source-of-truth workflow.

## Deliberately not configured yet

A production `.cpanel.yml` is intentionally absent.

Before creating it, audit the actual cPanel **Git Version Control** environment and capture:

- repository clone destination;
- remote authentication method for the private GitHub repository;
- available Git/cPanel deployment controls;
- exact deployment task shell/runtime behavior;
- executable paths required by any copy/sync task;
- destination-path restrictions;
- whether `rsync` is available and its exact path if used;
- failure/rollback behavior;
- how deployment logs/evidence are retrieved.

Do not assume that a command available on a generic cPanel server exists at the same path here.

## Public artifact boundary

Only intended public output should be copied to:

`/home/afradadm/apps.afradadmedia.com/`

Repository governance, evidence, source notes, and Git metadata should not be exposed as public web content.

The current candidate public payload is the contents of `public/`.

## Private repository authentication

The exact cPanel↔GitHub authentication path is still HOLD until audited. Prefer a least-privilege read-only mechanism for production pull access.

Never commit:

- GitHub tokens;
- private SSH keys;
- cPanel credentials;
- service-account credentials;
- AdMob account secrets.

## Publication boundary

A successful pull/deploy command proves only technical execution. It does not authorize publication and does not prove buyer/compliance correctness.
