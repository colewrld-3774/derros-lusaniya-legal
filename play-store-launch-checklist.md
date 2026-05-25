# Derros Lusaniya Play Store Launch Checklist

Last updated: 2026-05-22

Use this as the release gate before uploading to Google Play. Do not submit the app until every Required item is done.

## Phase 1 - Rejection Blockers

- [ ] Privacy policy is final, hosted on HTTPS, and linked in Play Console and inside the app.
- [ ] Data safety form matches the app and privacy policy exactly.
- [ ] App access instructions are provided for Google review accounts if login is required.
- [ ] Release build uses a signed Android App Bundle, not a debug APK.
- [ ] Final production application ID/package name is chosen before first Play upload.
- [ ] Release SHA-1 and SHA-256 are added to Firebase for Google Sign-In.
- [ ] No service-account private keys or admin secrets are packaged in the app.
- [ ] Firestore rules block users from reading or editing data outside their role.
- [ ] Sensitive permissions are minimized and justified.
- [ ] App opens without crash in light mode, dark mode, and each supported language.
- [ ] No overflow stripes, red error screens, infinite spinners, placeholder pages, TODO labels, or broken buttons.

## Phase 2 - Policy And Legal

- [ ] Privacy policy includes: name, phone, email, address, location, order history, notification tokens, reviews, and support/deletion contact.
- [ ] Terms of service page is written and hosted.
- [ ] Support email is active and visible in Play Console.
- [ ] Developer contact details are complete in Play Console.
- [ ] Content rating questionnaire is completed as a food delivery app.
- [ ] Target audience is set correctly. Do not target children unless the whole app is built for that policy.
- [ ] Ads declaration is set to "No" unless ads are added.
- [ ] Government/COVID/news/financial product declarations are answered accurately.

## Phase 3 - Data Safety Mapping

Declare collection for:

- [ ] Approximate location and precise location: delivery address, map location, rider tracking.
- [ ] Name: account profile, rider/customer identification.
- [ ] Email address: account login and password reset.
- [ ] Phone number: order contact, rider/customer/admin calling.
- [ ] Address: delivery address.
- [ ] User IDs: Firebase Auth UID and notification routing.
- [ ] Purchase history: orders, order totals, order status, items ordered.
- [ ] App interactions: notifications, order actions, reviews, admin/rider actions.
- [ ] Device or other IDs: FCM token and Firebase installation/device identifiers.
- [ ] Crash logs/diagnostics if Firebase/Google services collect them.

Declare purposes:

- [ ] App functionality.
- [ ] Account management.
- [ ] Analytics/reporting if analytics dashboards or SDK diagnostics are used.
- [ ] Developer communications for order and delivery notifications.
- [ ] Fraud prevention, security, and compliance.

## Phase 4 - Permissions

Current Android permissions should be:

- [ ] Internet: required for Firebase, images, orders, auth, and notifications.
- [ ] Fine/coarse location: required for delivery location and rider tracking.
- [ ] Notifications: required for order and delivery updates.
- [ ] Vibrate: notification feedback.

Avoid before release unless truly needed:

- [ ] Background location.
- [ ] Direct phone call permission.
- [ ] SMS/call log permissions.
- [ ] Storage/media permissions.
- [ ] Camera permission.

## Phase 5 - Firebase And Security

- [ ] Rotate any Firebase service account key that was ever committed or packaged.
- [ ] Move privileged notification sending to Cloud Functions or a backend only.
- [ ] Verify `fcm_queue` writes cannot be abused by normal customers to spam arbitrary users.
- [ ] Verify admin and super admin role assignment can only be done by trusted super admins.
- [ ] Verify customers can only read/write their own profile, cart, reviews, and orders.
- [ ] Verify riders can only read available delivery orders and orders assigned to them.
- [ ] Verify admins can manage orders/menu/categories/offers/reviews only after role checks.
- [ ] Verify Firebase Storage rules if uploads are enabled.
- [ ] Check GitHub history for leaked secrets and revoke/rotate anything exposed.

## Phase 6 - App Quality QA

Test on a real phone in release mode:

- [ ] Open app from cold start.
- [ ] Signup with email.
- [ ] Email verification.
- [ ] Forgot password.
- [ ] Login/logout.
- [ ] Google Sign-In in release build.
- [ ] Customer places order.
- [ ] Customer receives push notification immediately.
- [ ] Rider sees available orders without refresh loops.
- [ ] Rider accepts, starts delivery, marks delivered.
- [ ] Customer confirms and reviews delivery.
- [ ] Admin views reviews with linked phone numbers.
- [ ] Admin cancels order with reason.
- [ ] Revenue updates for completed/delivered orders.
- [ ] Notifications remain visible after switching accounts.
- [ ] Language switch updates all visible UI.
- [ ] Theme switch works in portrait and landscape.
- [ ] Offline/slow internet states show retry or empty messages.
- [ ] No yellow/black overflow stripes on small phones.
- [ ] No stuck loading states.

## Phase 7 - Store Listing

- [ ] App title.
- [ ] Short description.
- [ ] Full description.
- [ ] Category selected.
- [ ] Tags/keywords researched.
- [ ] App icon 512 x 512 PNG.
- [ ] Feature graphic 1024 x 500 PNG.
- [ ] Phone screenshots: at least 2, recommended 6-8.
- [ ] Screenshots include customer menu/order tracking, rider deliveries, admin dashboard, dark mode, and language support.
- [ ] Privacy policy URL.
- [ ] Support URL if available.
- [ ] Support email.

## Phase 8 - Release Build

Commands:

```bash
flutter clean
flutter pub get
dart format lib
flutter analyze
flutter build appbundle --release
```

Release output:

```text
build/app/outputs/bundle/release/app-release.aab
```

Do not upload:

```text
build/app/outputs/flutter-apk/app-debug.apk
```

## Phase 9 - Signing Backup

Back up these outside GitHub:

- [ ] Upload keystore file.
- [ ] `key.properties`.
- [ ] Key alias.
- [ ] Store password.
- [ ] Key password.
- [ ] SHA-1 fingerprint.
- [ ] SHA-256 fingerprint.

## Current Code Audit Notes

- App display name is set to `Derros Lusaniya`.
- The release Gradle config now supports `android/key.properties` and a release keystore, but will fall back to debug signing until those local signing files are created.
- Current Android package is `com.example.derroslusaniyaapp` because Firebase is configured for that package. The Play Store app name can be `Derros Lusaniya`, but the Android package ID must be lowercase reverse-domain format, such as `com.derroslusaniya.app`. Choose the final production package before first Play Store upload; changing it later means publishing a separate app.
- A client-side Firebase service account config file was removed. Rotate the exposed Firebase service account key before production.
- `CALL_PHONE` and `ACCESS_BACKGROUND_LOCATION` were removed from the release manifest because the current app does not need them.

## Official References

- Google Play Data safety: https://support.google.com/googleplay/android-developer/answer/10787469
- Prepare app for review: https://support.google.com/googleplay/android-developer/answer/9859455
- Upload Android App Bundle: https://developer.android.com/studio/publish/upload-bundle
- App signing: https://developer.android.com/guide/publishing/app-signing
