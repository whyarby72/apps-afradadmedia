# Privacy Publication Inputs — Human Decision Required

Date: 2026-10-04  
Project: Apps AfradadMedia  
Product: Photo Compressor: KB Limit  
Branch: `feature/photo-compressor-web-candidate`

## Status

`BLOCKED_ON_HUMAN_IDENTITY_AND_AUDIENCE_INPUTS`

The landing page can continue as a product candidate, but the Privacy Policy cannot be finalized for publication until the following four items are supplied or explicitly decided by the publisher/account holder.

## Required inputs

### 1. Publisher / legal identity

Current supported public brand:
`Afradad Media`

Final publisher/legal identity:
`UNKNOWN — HUMAN INPUT REQUIRED`

Do not infer a legal entity name from:
- brand name;
- repository owner;
- local filesystem names;
- domain registrant guesses;
- developer account display names.

### 2. Privacy contact email

Current value:
`UNKNOWN — HUMAN INPUT REQUIRED`

Requirement:
- must be a real monitored mailbox;
- must be suitable for privacy inquiries;
- may be the same mailbox as support if the publisher explicitly chooses that arrangement.

Do not invent `privacy@afradadmedia.com` or any other address unless the mailbox is confirmed to exist.

### 3. Support contact email

Current value:
`UNKNOWN — HUMAN INPUT REQUIRED`

Requirement:
- must be a real monitored mailbox;
- should be appropriate for app-support questions;
- may match the privacy contact only if explicitly chosen.

### 4. Google Play target audience / children declaration

Current project source truth:
`UNKNOWN_PENDING_TRUTHFUL_PLAY_DECLARATION`

Human must provide the exact intended/final Play target-audience state.

Do not infer "not for children" merely because the product is a utility.

If children are included in the declared audience, Families/child-directed advertising constraints require a separate compliance re-audit before ad serving.

## Information already supported

These do not require new human identity input:

- public brand: Afradad Media;
- product: Photo Compressor: KB Limit;
- package: `com.afradadmedia.reducephotosize`;
- website architecture: `https://apps.afradadmedia.com/`;
- candidate privacy URL: `https://apps.afradadmedia.com/photo-compressor-kb-limit/privacy/`;
- core photo processing is local/on-device;
- source photo is not uploaded to Afradad Media servers for compression;
- no account/login required for the core workflow;
- current architecture does not use Firebase Analytics, custom analytics, or mediation;
- AdMob/UMP processing must be disclosed separately from photo processing.

## Human response template

Fill exactly:

```text
Publisher/legal identity:
Privacy contact email:
Support contact email:
Google Play target audience:
Children included in target audience: YES / NO
```

If the same mailbox will be used for Privacy and Support, repeat the exact same address in both fields.

## Gate

After the four inputs are supplied:

1. replace Privacy Policy placeholders;
2. replace the target-audience blocker with exact release-specific wording;
3. set effective date only when publication timing is known;
4. rerun copy/static QA;
5. keep publication HOLD until final artifact/W2 reconciliation and explicit deployment/publication approval.

No deployment, merge, Artifact Freeze, or publication is authorized by this intake record.
