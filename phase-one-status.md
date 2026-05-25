# Phase 1 Status - Play Store Rejection Blockers

Last updated: 2026-05-23

## Done In Code

- [x] Public GitHub Pages files generated under `docs/`.
- [x] Privacy policy page generated: `docs/privacy-policy.html`.
- [x] Terms page generated: `docs/terms-of-service.html`.
- [x] Support page generated: `docs/support.html`.
- [x] In-app Legal screen added from Profile.
- [x] Direct phone-call permission removed from the Android release manifest.
- [x] Background-location permission removed from the Android release manifest.
- [x] Firebase service-account client config removed from app source.
- [x] Release App Bundle build path verified previously.

## Needs Your Input Now

- [x] Final support email: [derroslusaniya.info@gmail.com](mailto:derroslusaniya.info@gmail.com).
- [x] Business/legal address: Plot 15, Mugungulu Hill, Mubende, Uganda, P.O. Box 10234.
- [x] Final GitHub Pages privacy URL: [https://colewrld-3774.github.io/derros-lusaniya-legal/privacy-policy.html](https://colewrld-3774.github.io/derros-lusaniya-legal/privacy-policy.html).
- [x] Final production package name decision: keep `com.example.derroslusaniyaapp`.
- [x] Customer/rider/admin/super admin reviewer account emails documented for Google Play App access.
- [ ] Firebase Console access to add release SHA-1/SHA-256.
- [ ] Confirmation that the exposed Firebase service-account key has been rotated/revoked.

## Must Be Done Before Play Upload

- [x] Replace placeholders in HTML/Markdown legal files.
- [ ] Add final privacy/support URLs to Play Console.
- [ ] Complete Data safety form using `play-store-data-safety-draft.md`.
- [ ] Add Play App access instructions using `play-store-app-access-instructions.md`.
- [x] Create release upload keystore and `android/key.properties`.
- [x] Build final signed AAB.
- [ ] Test signed release on real Android device.
- [ ] Deploy and test Firestore/Storage rules.
