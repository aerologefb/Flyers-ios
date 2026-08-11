# Flyers — Privacy Policy

**Effective date:** 12 May 2026
**Last updated:** 11 August 2026 (Version 4.3 — app version 3.3.0)

This Privacy Policy describes how the **Flyers** iOS application handles your information. The Flyers app is published by **Capt. Navneet Reddy** (the *Developer*). If you have questions, contact **NAV-INT-LLC@pm.me**.

This policy exists to be plain, short, and honest. The summary is: **Flyers is a personal companion app for airline crew. It runs on your device, talks to your airline's eCrew portal and Apple's iCloud, and collects no analytics. By default, the Developer cannot read your eCrew credentials or on-device roster cache. Push notifications are opt-in: after your first sign-in Flyers shows a one-time prompt explaining notifications and letting you turn them on or off, and you can change this later in Settings. If you explicitly opt into server-side eCrew monitoring, Flyers sends only the minimum credentials and device identifiers needed for that monitoring to the Flyers Roster Watcher so it can check for roster changes and send signal-only push notifications. Exact What's Changed details are still fetched and computed locally on your iPhone when you open the notification. Flyers uses maps only to show duty routes, airport context, and layover information — it does not track your location. If you opt into Flyers Social, roster events you publish are stored in Apple's CloudKit Public Database and are intended to be visible only to accepted friends in the app.**

---

## 1. Who runs Flyers

- **Developer / Data Controller:** Capt. Navneet Reddy (NAV-INT LLC)
- **Contact:** NAV-INT-LLC@pm.me
- **Jurisdiction:** The Developer's home jurisdiction. EU users may exercise GDPR rights by writing to the contact email.

Most Flyers features run only on your device. The optional server-side eCrew monitoring feature uses a Flyers-operated Roster Watcher backend only after you explicitly enable it in Settings. Your airline's eCrew portal remains operated by your airline, not the Developer, and your iCloud account remains operated by Apple.

## 2. What Flyers stores and where

### 2.1 On your device (Keychain + SwiftData)

| Data | Where | Why |
|---|---|---|
| Your eCrew portal credentials (crew ID, password) | iOS Keychain, with `kSecAttrAccessibleWhenUnlockedThisDeviceOnly` | So the app can sign back in to your airline's portal automatically. |
| Your roster, logbook, flight details, schedule cache, and local What's Changed records | SwiftData (local on-device only) | So the app works offline, renders instantly, and lets you review detected roster changes. |
| App preferences (selected time zone, biometric unlock setting, notification choices, one-time notification prompt state, server-monitoring consent state, etc.) | UserDefaults / SwiftData (on-device) | App configuration. |

By default, this data stays on your device and is not sent to the Developer, to analytics, or to advertising services.

### 2.2 Optional server-side eCrew monitoring

Server-side eCrew monitoring is **off by default**. If you choose to enable it in Settings, Flyers shows a separate consent screen and requires explicit acknowledgements before the final Enable action. Only then does Flyers send the data below to the Flyers Roster Watcher backend over HTTPS so the backend can periodically check eCrew for roster changes and send push notifications even when iOS does not wake the app.

| Data | Where | Why |
|---|---|---|
| eCrew crew ID and password | Encrypted credential vault on the Roster Watcher backend | To sign into your airline's eCrew portal for your account and detect roster changes. |
| APNs device token and OneSignal subscription ID | Roster Watcher enrollment record and OneSignal | To send a roster-change push notification to this device. |
| Tenant/airline identifier, consent version, monitoring status, and username suffix | Roster Watcher enrollment record | To verify the supported eCrew tenant, record consent, show status, and support deletion. |

The Roster Watcher stores credentials encrypted at rest and does not store roster HTML, session cookies, or raw roster contents. It stores only a safe roster fingerprint/change state needed to decide whether a notification should be sent.

Push payloads are **signal-only**: they tell Flyers that a change was detected, but they do not include duty details, report times, hotel data, raw roster content, credentials, or cookies. When you open a roster-change push, Flyers refreshes eCrew on your iPhone, computes the exact What's Changed diff locally, and stores that review history on the device.

You can disable monitoring from Settings at any time; Flyers asks the backend to hard-delete the device enrollment and clears local monitoring state.

### 2.3 In your airline's eCrew portal

The Flyers app talks to the AIMS eCrew web portal operated by your airline (your airline's own eCrew domain). When you sign in, the app authenticates against that portal and fetches your own roster, dashboard, and flight details. This is the same data your airline would let you see by signing into the portal in a web browser. The Developer does not operate the eCrew portal and cannot see what your airline stores or how long.

### 2.4 In your iCloud account (only if you use Flyers Social)

If you choose to enable **Flyers Social** — the optional feature that lets you share your roster with other Flyers users — the following data is stored in **your iCloud account** via Apple's CloudKit:

| Data | Where in CloudKit | Visibility |
|---|---|---|
| Your public `@handle`, display name, and internal anchor `(airlineId, staffId)` | Public Database (`Handle` record) | The handle and display name are visible to other Flyers users. The `(airlineId, staffId)` pair is used for impersonation protection and is not displayed in normal app UI. |
| Your friend requests, accepted edges, and any users you block | Public Database (`FriendRequest`, `FriendEdge`, `Block`) | Used by the app to show requests, friendships and blocks. |
| The roster events you publish to friends | Public Database (`SharedRoster`) | Intended to be shown only to accepted friends listed in the record's `viewableBy` field. The app checks that list before rendering the roster. |

These records sit in Apple's CloudKit container (`iCloud.com.navintllc.flyers.ios`). Apple operates this infrastructure. Because Flyers Social uses CloudKit Public Database records for roster sharing, roster payloads are not a substitute for regulatory roster systems and should be considered shared data once you opt into publishing.

You can stop using Flyers Social at any time. **Settings → Flyers Social → Delete my Flyers Social data** deletes your published `SharedRoster` record and clears the local handle state on this device.

### 2.5 Push notifications and maps

Flyers uses iOS local notifications and push notifications only for app functionality: report reminders, crew-mail alerts, roster-change alerts, and optional server-monitoring roster-change signals. Notifications are opt-in. After a crew member signs in for the first time on a device, Flyers shows a one-time prompt explaining notifications with an on/off choice; the choice can be changed later in Settings.

If notifications are enabled, Apple Push Notification service and OneSignal process the technical device/subscription identifiers needed to deliver alerts to that device. Notification content is limited to operational app alerts. Server-monitoring pushes are signal-only and do not contain roster contents, credentials, duty details, hotel data, or raw eCrew data.

Flyers includes a location purpose string because the app links map/location-capable Apple frameworks and shows duty routes, airport context, and layover information on maps. Flyers does **not** track your live location, does **not** store location history, and does **not** send device location to the Developer, the Roster Watcher, Cloudflare, OneSignal, analytics, or advertisers.

## 3. What Flyers does *not* collect

- No analytics, no telemetry, no usage tracking.
- No advertising or analytics SDKs that phone home. OneSignal is used only to deliver push notifications when you enable notifications/server monitoring.
- No advertising identifiers. No advertising of any kind.
- No live location tracking and no location history.
- No contacts access.
- No microphone, no camera, no health data.
- Credentials never leave your device unless you explicitly enable server-side eCrew monitoring in Settings.
- Your raw roster HTML, session cookies, and full roster contents are not stored on a Developer-operated server.

## 4. Subscriptions and payments

Flyers offers an optional **Flyers Pro** subscription — an **auto-renewable subscription** billed **monthly (`$2.99`) or yearly (`$19.99`)**, with a **7-day free trial that unlocks the full app**. The subscription renews automatically at the end of each period until you cancel.

All purchases are processed by **Apple** via StoreKit and the App Store. Flyers receives only your **entitlement status** from StoreKit on your device — that is, whether Pro is currently active. Flyers does **not** collect, store, or transmit your payment details, card numbers, or Apple ID, and no purchase data leaves your device beyond Apple's own processing. The Developer receives only Apple's standard, aggregated payout and never sees your card number, full name, or address.

Manage or cancel your subscription in **Settings → Apple ID → Subscriptions** on your iPhone.

## 5. Your rights

You can delete most Flyers data yourself at any time:

- **Local data:** sign out (Hub → Sign out), uninstall Flyers, or wipe the device.
- **Notifications:** change notification choices in Hub → Settings → Notifications, or in iOS Settings → Notifications → Flyers.
- **Server-side eCrew monitoring:** Hub → Settings → Server eCrew monitoring → **Disable server monitoring**. This asks the Roster Watcher backend to delete your device enrollment and encrypted credential envelope.
- **Flyers Social data (CloudKit):** Settings → Flyers Social → **Delete my Flyers Social data**.
- **Subscription:** Settings → Apple ID → Subscriptions → Flyers Pro → Cancel.

If you are an EU or UK resident, you have additional rights under GDPR / UK GDPR — including access, rectification, erasure, restriction, portability, and objection. Write to the contact email below. Depending on the feature, these rights may be exercised directly via your device, Apple/iCloud, your airline/eCrew tenant, or the Roster Watcher delete control.

## 6. Data retention

- **On-device data** lives until you sign out, delete the app, or wipe the device.
- **Notification preferences and technical push identifiers** live until you disable notifications/server monitoring, sign out where applicable, delete the app, or revoke notification permission in iOS Settings.
- **Server-side eCrew monitoring data** lives until you disable monitoring, the enrollment is deleted during maintenance, or the backend is decommissioned.
- **CloudKit data** lives until you choose "Delete my Flyers Social data" or Apple garbage-collects unowned records.
- **Apple's subscription records** are kept by Apple under Apple's own retention policies.

## 7. Children

Flyers is rated **4+** but its intended audience is professional airline crew. The Developer does not knowingly collect data from anyone under 13.

## 8. International transfers

Apple operates CloudKit globally and may store your data in any of its data centres depending on your iCloud region. Cloudflare and OneSignal operate globally and may process server-monitoring/push-delivery data according to their infrastructure regions. By using Flyers Social or server-side eCrew monitoring, you consent to the corresponding infrastructure handling needed for those optional features.

## 9. Security

- By default, credentials sit in the iOS Keychain with the `WhenUnlockedThisDeviceOnly` accessibility class — they are encrypted at rest by the device's Secure Enclave.
- If you enable server-side eCrew monitoring, the Roster Watcher stores an encrypted credential envelope at rest and decrypts credentials only to perform the monitoring check.
- All network traffic to eCrew portals and the Roster Watcher goes over HTTPS.
- CloudKit data is protected by Apple's CloudKit security controls.
- Push notifications are signal-only and do not contain roster contents or credentials.

## 10. Changes to this policy

If material changes are needed, the policy will be updated here and the **Last updated** date at the top will change. Continued use of the app after a change constitutes acceptance.

## 11. Disclaimer & limitation of liability

Flyers is an **independent, unofficial** companion app. It is **not affiliated with, endorsed by, or supported by any airline, AIMS International, OneSignal, Cloudflare, or Apple**. "eCrew", "AIMS", and any airline names or marks are the property of their respective owners and are used only to describe what the app connects to.

Roster data and notifications are **best-effort and may be delayed, incomplete, or unavailable**. The official eCrew portal and your airline's official communications are the **authoritative source** for your duties, report times, and any roster change — do not rely on Flyers alone for duty awareness. Flyers is provided **"as is", without warranty of any kind**. To the maximum extent permitted by law, the Developer accepts **no liability** for any missed duty, error, omission, or loss arising from use of the app.

## 12. Contact

**Capt. Navneet Reddy**
**NAV-INT-LLC@pm.me**

For privacy questions, data-access requests, or anything else, write to the email above.
