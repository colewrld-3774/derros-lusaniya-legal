# Play Store Data Safety Draft - Derros Lusaniya

Use this as the Play Console Data safety form source of truth. Keep it aligned with `privacy-policy.html` before submission.

## Data Collected

### Location

- Approximate location: Yes
- Precise location: Yes
- Purpose: App functionality, delivery fulfillment, rider tracking, fraud prevention/security
- Shared: With service providers needed to run the app, such as Firebase/Google services
- Required or optional: Required for delivery features; users can deny location and use manual address where available

### Personal Information

- Name: Yes
- Email address: Yes
- Phone number: Yes
- Address: Yes
- Purpose: Account management, order delivery, rider/customer/admin contact, support, fraud prevention/security
- Shared: With service providers needed to run the app
- Required or optional: Required for account and delivery features

### Financial Information

- User payment info: No card/bank details are collected by the current app
- Purchase history: Yes, order items, totals, discounts, delivery status, and order history
- Purpose: App functionality, order fulfillment, analytics/reporting, accounting/support

### App Activity

- App interactions: Yes, order actions, rider actions, admin actions, notification interactions, reviews
- In-app search history: Search text may be processed locally in app screens; do not declare as collected unless stored remotely
- Purpose: App functionality, analytics/reporting, fraud prevention/security

### App Info and Performance

- Crash logs/diagnostics: Yes if Firebase/Google diagnostics are enabled in the release
- Purpose: Analytics, app performance, crash prevention, service improvement

### Device or Other IDs

- Device or other IDs: Yes, Firebase Cloud Messaging token and Firebase installation/device identifiers
- Purpose: Push notifications, app functionality, fraud prevention/security

## Security Practices

- Data is encrypted in transit: Yes
- Users can request data deletion: Yes, through the support contact
- Data is not sold: Yes
- Data is used for app functionality and operational communication, not unrelated notification spam

## Notes Before Submission

- Privacy policy, support email, business address, and hosted URL are filled in. Re-check that Play Console uses the same public URLs before submitting.
- Confirm whether Firebase Crashlytics, Analytics, or Performance Monitoring are enabled in the final release. If yes, keep diagnostics/app activity declarations.
- If a payment provider is added later, update this form and the privacy policy before release.
- If background location is added later, update the Android manifest, prominent disclosure, Play Console permissions declaration, and privacy policy.
