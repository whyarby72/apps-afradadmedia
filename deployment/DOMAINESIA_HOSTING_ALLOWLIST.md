# DomaiNesia Hosting Residue Allowlist

## Scope

This allowlist applies only to the verified production document root:

`/home/afradadm/apps.afradadmedia.com/`

and only while the current DomaiNesia Git Deploy behavior remains materially equivalent to the verified 2026-10-04 environment.

Verification model:

`CLEAN_TRACKED_PLUS_HOSTING_ALLOWLIST`

## Allowed top-level untracked entries

### `.user.ini`

Classification: `HOSTING_MANAGED_LIKELY`

Verified properties at the deployment-probe checkpoint:

- regular file;
- owner/group matched the hosting account;
- permissions: `-rw-r--r--`;
- size: 374 bytes;
- directive names observed: `error_log`, `log_errors`;
- no credential-like content detected;
- public HTTP result: 403.

### `php.ini`

Classification: `HOSTING_MANAGED_LIKELY`

Verified properties at the deployment-probe checkpoint:

- regular file;
- owner/group matched the hosting account;
- permissions: `-rw-r--r--`;
- size: 374 bytes;
- same inspected digest as `.user.ini` at the checkpoint;
- directive names observed: `error_log`, `log_errors`;
- no credential-like content detected;
- public HTTP result: 403.

### `.well-known/`

Classification: `HOSTING_MANAGED_LIKELY`

Verified properties at the deployment-probe checkpoint:

- directory;
- owner/group matched the hosting account;
- permissions: `drwxr-xr-x`;
- immediate child observed: `acme-challenge`;
- public directory HTTP result: 403.

## Rules

1. These paths are allowlisted as **environment residue**, not application source.
2. Do not add them to the public deployment branch merely to mirror hosting state.
3. Do not delete, overwrite, move, chmod, or repurpose them solely to make Git status clean.
4. Tracked Git modifications are evaluated independently and are never excused by this allowlist.
5. Any new top-level untracked entry outside this list is `HOLD` until classified.
6. Any material change to the purpose, file type, ownership, permissions, public exposure, or credential-content state of an allowlisted entry invalidates its automatic acceptance and requires re-verification.
7. If `.well-known/` is needed for certificate/ACME operations, deployment must not overwrite or remove it.
8. Allowlist scope is provider/environment-specific and must not be generalized to other hosts.

## Replay check

For each production deployment:

- verify exact Git HEAD;
- verify no tracked Git drift;
- enumerate top-level untracked entries;
- compare them with this allowlist;
- verify no unexpected public exposure;
- record anomalies before declaring hosted PASS.
