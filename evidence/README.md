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

Do not commit credentials, private keys, session cookies, personal access tokens, or sensitive account screenshots.

A PASS label without artifact/environment/replay evidence is not sufficient for release-critical verification.
