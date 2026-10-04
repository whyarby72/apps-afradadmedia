# Photo Compressor — Exact Deployment Candidate v1

Date: 2026-10-04  
Project: Apps AfradadMedia  
Product: Photo Compressor: KB Limit

## Candidate

Branch:

`deploy-candidate/photo-compressor-web-v1`

Base:

`deploy/production`

Candidate head:

`6f247e0c04fbbf844c4b4e55524183b82cdeb163`

## Exact public delta

Compared with `deploy/production`, the candidate is:

`ahead 3 / behind 0`

Exactly three files are added:

1. `photo-compressor-kb-limit/index.html`
2. `photo-compressor-kb-limit/privacy/index.html`
3. `photo-compressor-kb-limit/assets/site.css`

No existing production-root file is modified.

Existing root payload remains:

- `.htaccess`
- `index.html`
- `robots.txt`

No internal review/governance file is present in the deployment candidate.

## Source-to-deployment blob binding

Landing source:
`public/photo-compressor-kb-limit/index.html`

Landing deployment blob:
`1ee42d462ebaf7a2fb24e8db943d2801f3c6d2ae`

Privacy source:
`public/photo-compressor-kb-limit/privacy/index.html`

Privacy deployment blob:
`cf10a07a5a2e77df5039a8fb408210786bfe287a`

CSS source:
`public/photo-compressor-kb-limit/assets/site.css`

CSS deployment blob:
`801c1065a308b846197bf69ecd73446bb436c150`

The deployment candidate blobs are byte-identical to the reviewed source blobs.

## Target URLs after a separately approved deploy

Landing:

`https://apps.afradadmedia.com/photo-compressor-kb-limit/`

Privacy:

`https://apps.afradadmedia.com/photo-compressor-kb-limit/privacy/`

CSS:

`https://apps.afradadmedia.com/photo-compressor-kb-limit/assets/site.css`

## Static candidate checks

Landing:
- exactly one H1;
- local CSS path resolves to `./assets/site.css`;
- Privacy link resolves to `./privacy/`;
- JavaScript count: 0;
- `noindex,nofollow`: present.

Privacy:
- exactly one H1;
- local CSS path resolves to `../assets/site.css`;
- publisher/contact present;
- 18+ target-audience wording present;
- JavaScript count: 0;
- `noindex,nofollow`: present.

## Boundary

`READY_FOR_DEPLOYMENT_APPROVAL / NOT DEPLOYED`

This record does not authorize:
- merge to `deploy/production`;
- DomaiNesia deployment;
- removal of `noindex,nofollow`;
- publication;
- Artifact Freeze.

Deployment requires a separate explicit approval.
