# Photo Compressor — W2 Artifact-Bound Privacy Reconciliation

Date: 2026-10-04  
Product: Photo Compressor: KB Limit

## Verdict

`PASS_FOR_S7_RELEASE_MODE_TEST_ARTIFACT / FINAL_PRODUCTION_HOLD`

The Android W2 audit produced replayable debug and release-mode artifacts from the current S7 product source and reconciled the web Privacy Policy against the exact merged manifest and resolved runtime dependencies.

## Android source/evidence binding

Canonical product source:

`baf63bbc9c793b135796cc70de61013bccd26fca`

Audit workflow head:

`4cb86e5393d857e53437a62ad9868c0f0eaf8091`

The only code-tree difference between the product source head and the audit head is the W2 GitHub Actions workflow. Application source was not changed.

Final valid GitHub Actions run:

`37208707771`

Evidence artifact:

- ID: `11305559563`
- digest: `sha256:8aa255476a714621657ebb0fd6d9076df08891e25831c7ca83cb17f88db947a6`

## Release-mode artifact

Package:

`com.afradadmedia.reducephotosize`

Version:

`0.1.0` / versionCode 1

Unsigned release APK:

- bytes: `36,679,520`
- SHA-256: `147268aa57bbbd7224782104dcfa96018792a73f3dcaff65ceb61c218e6e2d16`

Merged manifest source:

`app/build/intermediates/merged_manifests/release/processReleaseManifest/AndroidManifest.xml`

## Exact resolved privacy/ads dependencies

Release runtime proves:

- Google Mobile Ads Next-Gen `1.5.0`
- Google UMP `4.0.0`
- legacy `play-services-ads`: absent
- legacy `play-services-ads-lite`: absent
- Firebase Analytics: absent
- custom analytics dependency: absent
- mediation dependency: absent

## Exact release merged-manifest permissions

Present:

- `android.permission.INTERNET`
- `android.permission.ACCESS_NETWORK_STATE`
- `android.permission.READ_BASIC_PHONE_STATE`
- `com.google.android.gms.permission.AD_ID`
- `android.permission.WAKE_LOCK`
- `android.permission.FOREGROUND_SERVICE`
- app-scoped `DYNAMIC_RECEIVER_NOT_EXPORTED_PERMISSION`

Not present:

- camera
- microphone
- precise/coarse location
- contacts
- `READ_MEDIA_IMAGES`
- broad external-storage read/write

## Google SDK disclosure reconciliation

Current official Google GMA Next-Gen disclosure states automatic collection/sharing of:

- IP address;
- user product interactions;
- diagnostic information;
- device/account identifiers;

for advertising, analytics, and fraud-prevention purposes. Google states this SDK data is encrypted in transit with TLS.

The Privacy Policy candidate has been updated to distinguish those Google SDK practices from the app's local JPEG processing.

## Production binding boundary

The audited release-mode manifest still contains Google's sample App ID:

`ca-app-pub-3940256099942544~3347511713`

It does not contain the real provider App ID:

`ca-app-pub-8084313520610270~1492953098`

Therefore this W2 result does not prove production ad serving and does not close final production privacy.

## Verification-control repair

An earlier audit run captured the debug manifest in the release evidence slot because manifest selection was too broad.

That run is rejected for release-manifest claims.

The control was repaired by binding manifest capture to explicit variant directories and asserting exact debug/release package names. Run `37208707771` is the valid evidence run.

## Web Privacy Policy changes

The candidate now:

- names Google Mobile Ads / UMP third-party processing separately from JPEG processing;
- describes Google's currently documented SDK data categories;
- distinguishes absence of Firebase/custom analytics from Google Ads' own analytics-purpose processing;
- records the audited permission boundary without claiming broad media/camera/location access;
- retains final-production reconciliation language.

## Remaining blockers

- production AdMob App ID binding;
- real Banner ad-unit ID binding;
- banner placement API mismatch resolution;
- exact final signed/Play candidate build;
- final merged-manifest/dependency replay after production binding;
- production-like UMP/ad runtime;
- final Play Ads declaration;
- final Play Data Safety form;
- final effective date;
- final rendered human visual review;
- explicit deployment/publication approval.

## Disposition

`WEB_PRIVACY_W2_RECONCILED_FOR_TEST_RELEASE_MODE_CANDIDATE`

No deploy, merge, Artifact Freeze, or publication is authorized.
