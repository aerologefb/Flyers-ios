# Flyers — Support

**Contact:** [NAV-INT-LLC@pm.me](mailto:NAV-INT-LLC@pm.me)
**Developer:** Capt. Navneet Reddy

The fastest way to get help is to email **NAV-INT-LLC@pm.me** with:

1. The version + build number, shown at the top of the **About** screen (Hub tab → About).
2. Your device model and iOS version (Settings → General → About).
3. A description of what you tried, what you expected, and what you saw instead.
4. Screenshots if useful.

Most replies arrive within **2–3 business days**.

---

## FAQ

### I forgot my password / I'm locked out of eCrew

Flyers does not control your airline's eCrew portal. Use the **Forgot password** link on the login screen — Flyers will hand off to your airline's password reset flow. If that fails, contact your airline's crew control or eCrew helpdesk.

### My roster looks wrong

Flyers shows whatever your airline's eCrew portal returns. If a flight, layover, or time is wrong in Flyers, **first check the eCrew web portal in a browser**. If the data is wrong there, it's an issue for your airline's roster team. If it's correct on the web but wrong in Flyers, email support with a screenshot of both.

### My duty times look an hour off

Flyers fetches all times in UTC and converts to your selected display zone. **Hub → Settings → Time zone** lets you pick between local, base, and UTC. Make sure your iPhone's system time zone (Settings → General → Date & Time) is set to Automatic — the app uses this as the "local" reference.

### Face ID isn't working

Hub → Settings → Security → toggle off and on. If still failing, sign out (Hub → Sign out) and sign in once with your password — Flyers re-binds your credentials in the iOS Keychain.

### My background sync isn't running

iOS schedules background refresh at its own discretion based on app usage and battery state. There is no manual override Apple permits. Open Flyers manually and pull-to-refresh on the Roster or Dashboard to force a fresh fetch.

### Flyers Social — my friend can't find my handle

- Confirm you're both signed into iCloud on your devices.
- Confirm both of you have **claimed a handle** in the Friends tab.
- Search is case-insensitive but spelling-exact — `nav_reddy` will not find `navreddy`.
- If you previously toggled **Settings → Flyers Social → Hide me from search**, friends can't search for you.

### Flyers Social — my friend's roster isn't updating

Your friend's roster is republished when **their** device performs a background sync (roughly every few hours, controlled by iOS). The "Pull to refresh" gesture on your view of their roster only refreshes the receive side; it doesn't force them to republish.

### What is Flyers Pro, and what happens after the free trial?

Flyers Pro unlocks the whole app — roster, flights, stats, expiry, crew mail, fit-for-duty, pay estimate, logbook, and cross-airline roster sharing. New users get a **7-day free trial**, and the Dashboard shows a countdown of the days remaining. When the trial ends your subscription renews automatically unless you cancel; if it lapses, the Flyers Pro screen reappears and asks you to subscribe again.

### I subscribed to Flyers Pro but the Flyers Pro screen keeps appearing

- On the Flyers Pro screen, tap **Restore Purchases**.
- If it still appears, confirm in Settings → Apple ID → Subscriptions that the Flyers Pro subscription is **Active** (not Expired). If it shows Active and Flyers still doesn't see it, force-quit Flyers from the app switcher and reopen.

### How do I cancel Flyers Pro?

Settings → Apple ID → Subscriptions → Flyers Pro → Cancel Subscription. Apple handles all subscription billing — the Developer cannot cancel for you.

### I want to delete all my Flyers data

- **Local on-device data:** sign out (Hub → Sign out), then uninstall the app.
- **CloudKit / Flyers Social data:** Hub → Settings → Flyers Social → **Delete my Flyers Social data**. This revokes shares with friends and deletes the records owned by your handle.
- **Subscription:** Settings → Apple ID → Subscriptions → cancel.

### How do I report a bug?

Email **NAV-INT-LLC@pm.me** with the info at the top of this page. Please include exact steps to reproduce — even a one-line "tap X, then Y" is enormously useful.

### How do I request a feature?

Same email. Be specific about the use case.

---

## Disclaimer

Flyers is a third-party companion app. It is not affiliated with, endorsed by, or supported by your airline, AIMS International, or Apple. Use the app as a convenience layer over your airline's official tools, not as a replacement for them.
