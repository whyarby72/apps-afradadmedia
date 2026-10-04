# Evidence Pack

Store non-secret, reviewable verification records here when a gate is executed.

A verification record should identify:

- artifact commit SHA;
- verification profile;
- exact claim/invariant;
- environment/URL;
- tool/browser/runtime;
- fixture or state;
- observed timestamp;
- machine-observable output;
- PASS / HOLD / FAIL;
- replay steps;
- unsupported claims or unresolved exceptions.

For DomaiNesia production verification also record:

- tracked-tree cleanliness;
- untracked top-level entries;
- reconciliation against `deployment/DOMAINESIA_HOSTING_ALLOWLIST.md`;
- public exposure status for Git metadata and hosting residue.

Do not commit credentials, private keys, session cookies, personal access tokens, passwords, or sensitive account screenshots.

A PASS label without artifact/environment/replay evidence is not sufficient for release-critical verification.

The initial hosted deployment-probe record is:

`evidence/2026-10-04-domainsia-deployment-probe.md`
