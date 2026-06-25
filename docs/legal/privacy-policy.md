# Flyers — Privacy Policy

**Effective date:** 12 May 2026
**Last updated:** 26 June 2026 (Version 3.0)

This Privacy Policy describes how the **Flyers** iOS application handles your information. The Flyers app is published by **Capt. Navneet Reddy** (the *Developer*). If you have any questions about this policy, contact **NAV-INT-LLC@pm.me**.

This policy exists to be plain, short, and honest. The summary is: **Flyers is a personal companion app for airline crew. It runs on your device, talks only to your airline's eCrew portal and Apple's iCloud, and collects no analytics. The Developer cannot read your eCrew credentials or your on-device roster cache. If you opt into Flyers Social, the roster events you publish are stored in Apple's CloudKit Public Database and are intended to be visible only to accepted friends in the app.**

---

## 1. Who runs Flyers

- **Developer / Data Controller:** Capt. Navneet Reddy (NAV-INT LLC)
- **Contact:** NAV-INT-LLC@pm.me
- **Jurisdiction of incorporation:** The Developer's home jurisdiction. EU users may exercise GDPR rights by writing to the contact email.

There is no Flyers-operated server. Every piece of data the app uses is either on your device, in your airline's eCrew portal (which is operated by your airline, not the Developer), or in your own iCloud account (operated by Apple, not the Developer).

## 2. What Flyers stores and where

### 2.1 On your device (Keychain + SwiftData)

| Data | Where | Why |
|---|---|---|
| Your eCrew portal credentials (crew ID, password) | iOS Keychain, with `kSecAttrAccessibleWhenUnlockedThisDeviceOnly` | So the app can sign back in to your airline's portal automatically. |
| Your roster, logbook, flight details, schedule cache | SwiftData (local on-device only) | So the app works offline and renders instantly. |
| App preferences (selected time zone, biometric unlock setting, etc.) | UserDefaults (on-device only) | App configuration. |

This data never leaves your device. It is not sent to the Developer, to any third-party analytics service, or to any other party.

### 2.2 In your airline's eCrew portal

The Flyers app talks to the AIMS eCrew web portal operated by your airline (e.g. `ecrew.etihad.ae` for Etihad pilots). When you sign in, the app authenticates against that portal and fetches your own roster, dashboard, and flight details. This is the same data your airline would let you see by signing into the portal in a web browser. The Developer does not operate the eCrew portal and cannot see what your airline stores or how long.

### 2.3 In your iCloud account (only if you use Flyers Social)

If you choose to enable **Flyers Social** — the optional feature that lets you share your roster with other Flyers users — the following data is stored in **your iCloud account** via Apple's CloudKit:

| Data | Where in CloudKit | Visibility |
|---|---|---|
| Your public `@handle`, display name, and internal anchor `(airlineId, staffId)` | Public Database (`Handle` record) | The handle and display name are visible to other Flyers users. The `(airlineId, staffId)` pair is used for impersonation protection and is not displayed in normal app UI. |
| Your friend requests, accepted edges, and any users you block | Public Database (`FriendRequest`, `FriendEdge`, `Block`) | Used by the app to show requests, friendships and blocks. |
| The roster events you publish to friends | Public Database (`SharedRoster`) | Intended to be shown only to accepted friends listed in the record's `viewableBy` field. The app checks that list before rendering the roster. |

These records sit in Apple's CloudKit container (`iCloud.com.navintllc.flyers.ios`). Apple operates this infrastructure. Flyers does not run its own server. Because Flyers Social uses CloudKit Public Database records for roster sharing, roster payloads are not a substitute for regulatory roster systems and should be considered shared data once you opt into publishing.

You can stop using Flyers Social at any time. **Settings → Flyers Social → Delete my Flyers Social data** deletes your published `SharedRoster` record and clears the local handle state on this device.

## 3. What Flyers does *not* collect

- ❌ No analytics, no telemetry, no usage tracking.
- ❌ No third-party SDKs that phone home. (CloudKit and StoreKit are Apple-operated, not third-party.)
- ❌ No advertising identifiers. No advertising of any kind.
- ❌ No location tracking.
- ❌ No contacts access.
- ❌ No microphone, no camera, no health data.
- ❌ Credentials never leave your device. The Developer cannot see your eCrew password.
- ❌ Your roster is never sent to a Developer-operated server, because no such server exists.

## 4. Subscriptions and payments

Flyers offers an optional **Flyers Pro** subscription — an **auto-renewable subscription** billed **monthly (`$2.99`) or yearly (`$19.99`)**, with a **7-day free trial that now unlocks the full app**. The subscription renews automatically at the end of each period until you cancel.

All purchases are processed by **Apple** via StoreKit and the App Store. Flyers receives only your **entitlement status** from StoreKit on your device — that is, whether Pro is currently active. Flyers does **not** collect, store, or transmit your payment details, card numbers, or Apple ID, and **no purchase data leaves your device beyond Apple's own processing**. The Developer receives only Apple's standard, aggregated payout and never sees your card number, full name, or address.

Manage or cancel your subscription in **Settings → Apple ID → Subscriptions** on your iPhone.

## 5. Your rights

Because Flyers stores your data on your own device and in your own iCloud account, **you can delete everything yourself at any time without the Developer's involvement**:

- **Local data:** uninstall Flyers, or sign out (Hub → Sign out) to clear cached schedule and credentials.
- **Flyers Social data (CloudKit):** Settings → Flyers Social → Delete my Flyers Social data.
- **Subscription:** Settings → Apple ID → Subscriptions → Flyers Pro → Cancel.

If you are an EU or UK resident, you have additional rights under GDPR / UK GDPR — including access, rectification, erasure, restriction, portability, and objection. Write to the contact email below. Because the Developer holds no server-side records of you, most of these rights can be exercised by you directly via Apple (your eCrew tenant; iCloud account).

## 6. Data retention

- **On-device data** lives until you sign out, delete the app, or wipe the device.
- **CloudKit data** lives until you choose "Delete my Flyers Social data" or you delete the Flyers app and CloudKit garbage-collects unowned records.
- **Apple's subscription records** are kept by Apple under Apple's own retention policies.

## 7. Children

Flyers is rated **4+** but its intended audience is professional airline crew. The Developer does not knowingly collect data from anyone under 13.

## 8. International transfers

Apple operates CloudKit globally and may store your data in any of its data centres depending on your iCloud region. By using Flyers Social, you consent to Apple's data handling under their own privacy policy: <https://www.apple.com/legal/privacy/>.

## 9. Security

- Credentials sit in the iOS Keychain with the `WhenUnlockedThisDeviceOnly` accessibility class — they are encrypted at rest by the device's Secure Enclave and never leave the device.
- All network traffic to eCrew portals goes over HTTPS with TLS 1.2+ and forward secrecy.
- CloudKit data is encrypted end-to-end between your device and Apple's infrastructure, and at rest in Apple's data centres.
- The Developer has no remote-administration access to your device, your iCloud account, or your eCrew tenant.

## 10. Changes to this policy

If material changes are needed, the policy will be updated here and the **Last updated** date at the top will change. Continued use of the app after a change constitutes acceptance.

## 11. Contact

**Capt. Navneet Reddy**
**NAV-INT-LLC@pm.me**

For privacy questions, data-access requests, or anything else, write to the email above.
