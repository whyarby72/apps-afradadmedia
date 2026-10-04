# Photo Compressor Web Candidate — UI/UX, Typography, Responsive and Copy Audit

Date: 2026-10-04  
Project: Apps AfradadMedia  
Product: Photo Compressor: KB Limit  
Branch: `feature/photo-compressor-web-candidate`

## Verdict

`PASS_FOR_HUMAN_VISUAL_REVIEW / PUBLICATION_HOLD`

The landing-page and Privacy Policy candidates have been repaired for hierarchy, readability, responsive behavior, accessibility, and buyer-facing copy. The candidate remains intentionally `noindex,nofollow` and has not been deployed.

This audit is bound to the repository candidate, not to a hosted browser environment. A final rendered visual review at representative desktop/mobile widths remains required before Artifact Freeze or deployment approval.

## Audit lens

Reviewed:

- first-view information hierarchy;
- job-to-be-done clarity;
- desktop typography scale;
- mobile typography scale;
- reading measure;
- spacing and section rhythm;
- CTA hierarchy;
- conceptual-product visual truthfulness;
- responsive grid collapse;
- mobile navigation;
- keyboard focus visibility;
- skip-link accessibility;
- reduced-motion behavior;
- Privacy Policy scanning/readability;
- public-vs-internal copy separation;
- product-claim truth against the canonical handoff.

## Landing page findings and repairs

### 1. First-view job clarity

Before:
- the product name dominated the H1;
- the buyer job was primarily explained in the supporting paragraph.

Repair:
- eyebrow now carries `Photo Compressor: KB Limit`;
- H1 is job-first: `Compress to a KB/MB target. Verify before you upload.`;
- lead immediately explains JPEG selection, the user-provided limit, actual output checking, and on-device core compression.

Reason:
The first viewport should answer "what does this do for me?" before explaining product mechanics.

### 2. Hero visual truthfulness

Before:
- the stylized KB card could be mistaken for an app screenshot;
- the example showed a rounded KB value rather than the app's strongest exact-byte truth.

Repair:
- the visual is explicitly captioned `Workflow illustration — not an app screenshot.`;
- proof example uses exact bytes:
  `184,732 bytes ≤ 200,000-byte limit — PASS`.

Result:
The visual supports the product concept without pretending to be runtime evidence.

### 3. Typography

Desktop:
- H1 capped at 68px rather than 76px;
- section H2 capped at 46px;
- lead uses 18–21px with 1.55 line height;
- card headings use 20px;
- policy text measure is capped at 72ch.

Mobile:
- H1 resolves to approximately 39–48px;
- lead remains 18px;
- controls become full-width;
- dense multi-column content collapses to one column.

The design uses the system UI stack only. No external font dependency is required.

### 4. Workflow architecture

Changed from three broad steps to four buyer-recognizable steps:

1. Choose a JPEG.
2. Set the limit.
3. Compress on-device.
4. Check, save or share.

This maps more directly to the product's actual job flow.

### 5. Public copy cleanup

Removed/replaced copy that sounded like internal QA/specification language.

Notable repair:
- removed the public FAQ item asking whether production ads are already live;
- retained the necessary network nuance through the user-relevant question:
  `Does the app require internet access for compression?`

The answer distinguishes local core compression from advertising/consent network behavior without exposing internal release-process language.

### 6. Result states

The result-state section now uses three explicit user-facing states:

- PASS / Already ready;
- Target not met;
- Reduced.

JPEG/JPG scope moved to a separate format note rather than being presented as a result state.

### 7. CTA hierarchy

Primary:
`See how it works`

Secondary:
`Read Privacy Policy`

No Google Play download CTA is shown because a public Play listing/download destination is not yet part of the approved publication state.

## Privacy Policy findings and repairs

### 1. Legal-document hierarchy

Before:
- headline was marketing-like: `Privacy, explained around the actual app flow.`

Repair:
- H1 is now simply `Privacy Policy`;
- product identity is the subtitle;
- package identity and effective-date state are secondary metadata.

### 2. Scanability

Added:
- four-item privacy summary;
- in-page contents navigation;
- anchored sections;
- 72ch reading measure;
- clearer section grouping.

### 3. Storage wording

The Save destination is now stated from the handoff truth:

`Pictures/Reduce Photo Size`

Temporary-cache, saved-copy, share, and source-preservation behavior are separated.

### 4. Advertising boundary

The policy now uses release-conditional wording:

`When advertising is enabled in the app release you are using...`

This prevents the candidate from falsely describing production ad serving as already live while still making the policy structurally ready for an ad-enabled release.

### 5. Unsupported legal inference removed

The prior generic international-use paragraph was removed from the public candidate because the supplied product truth does not provide enough release-specific legal detail to make that section useful.

International/legal-region requirements remain a final compliance review item rather than being silently invented.

### 6. Release blockers kept visible

The candidate still does not invent:

- publisher legal identity;
- privacy contact;
- support contact;
- final effective date;
- final children/target-audience wording.

The children/target-audience section remains visibly marked `Publication review required`.

## Responsive / accessibility controls

Static controls verified in source:

- one H1 per page;
- viewport metadata on both pages;
- local stylesheet only;
- zero JavaScript;
- skip link on both pages;
- visible `:focus-visible` treatment;
- reduced-motion rule;
- responsive breakpoints at 980px, 860px and 620px;
- landing grids collapse for tablet/mobile;
- mobile CTA buttons become full width;
- Privacy Policy summary collapses to one column;
- no broken same-page anchor references detected;
- canonical URLs are present;
- candidate remains `noindex,nofollow`.

## Static QA evidence

Landing:

- H1 count: 1
- H2 count: 5
- title: PASS
- viewport: PASS
- canonical: PASS
- scripts: 0
- local stylesheet: `./assets/site.css`
- skip link: PASS
- internal anchor integrity: PASS
- privacy link: PASS
- exact-byte proof example: PASS
- workflow-illustration disclosure: PASS

Privacy:

- H1 count: 1
- H2 count: 15
- title: PASS
- viewport: PASS
- canonical: PASS
- scripts: 0
- local stylesheet: `../assets/site.css`
- skip link: PASS
- internal anchor integrity: PASS
- privacy/support placeholders retained: PASS
- target-audience publication blocker retained: PASS
- Save path truth: PASS
- local-processing vs AdMob boundary: PASS

CSS:

- external font/resource dependency: none
- focus-visible rule: PASS
- reduced-motion rule: PASS
- reading measure: 72ch
- mobile single-column fallback: PASS

## Remaining blockers before publication

`HOLD`:

1. publisher/legal identity;
2. privacy email;
3. support email;
4. final effective date;
5. final Google Play target-audience / children declaration;
6. exact merged release-manifest reconciliation;
7. final Play Data Safety reconciliation;
8. final production AdMob binding/runtime reconciliation;
9. final human visual review at representative desktop/mobile viewport sizes;
10. explicit deployment/publication approval.

## Claim ceiling

The candidate may state:

- JPEG/JPG scope;
- target KB/MB workflow;
- actual-byte verification for a known target;
- local/on-device core compression;
- source photo not uploaded to Afradad Media server for compression;
- original source not overwritten in the normal workflow;
- explicit Save / Share;
- no account required for core compression;
- unknown-limit path produces a smaller copy without a compatibility guarantee.

The candidate must not state:

- guaranteed compatibility with every website;
- lossless compression;
- support for all image formats;
- absolute zero data collection;
- no third-party processing;
- entire app is always offline;
- production ads are already live.

## Current disposition

`READY_FOR_HUMAN_VISUAL_REVIEW`

No deploy, merge, Artifact Freeze or Publication authority is implied.
