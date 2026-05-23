---
title: "FAQ"
weight: 110
description: "Frequently asked questions and troubleshooting"
---

## General

### Is Drivest free?

Yes. Drivest is free and open source under the MIT license.

### Does Drivest require an internet connection?

No. The app works fully offline. An internet connection is only needed for:

- Fetching exchange rates from NBP.
- Syncing odometer / battery / fuel data from a connected vehicle service.
- Reverse-geocoding captured GPS coordinates into a friendly place name (e.g. "Warsaw, PL"). If offline, the row shows a "Captured" badge instead — the underlying coordinate is still saved.

### Where is my data stored?

All data is stored locally on your device using Apple's SwiftData framework. Nothing is sent to any external server. See the [Privacy Policy](/privacy/) for details.

### Can I use Drivest on iPad?

Drivest is designed for iPhone and requires iOS 17.0 or later.

## Tabs

### Why is the Fuel tab missing?

If every vehicle on file is pure-EV (no combustion tank), the Fuel tab is hidden — symmetric with how the EV tab is hidden for petrol-only vehicles. Add a vehicle with a fuel type other than EV (or add a second tank with a fuel type) and the Fuel tab appears.

### Why is the EV tab missing?

The EV tab only appears when at least one vehicle has its fuel type set to EV (either as the primary fuel type or as a second tank).

## Fuel Tracking

### Why is fuel efficiency not showing for some fill-ups?

Fuel efficiency can only be calculated between two consecutive **full tank** fill-ups. Make sure to toggle **Full Tank** on when you fill up completely. Partial fill-ups will not show an efficiency badge.

### Can I track two fuel types for one vehicle?

Yes. When adding a vehicle, you can configure a **second tank** with a different fuel type. This is useful for vehicles that run on LPG + petrol, or plug-in hybrids (petrol + EV).

### How does receipt scanning work?

The app uses on-device OCR (optical character recognition) to read fuel receipts through your camera. It extracts the price per unit, volume, and total cost. All processing happens locally — no images are sent anywhere.

## Costs

### Can I create my own cost categories?

Yes. Go to **Settings > Categories** and tap **+** to add a custom category with a name and icon of your choice.

### Can I attach files to cost entries?

Yes. When adding a cost, you can attach both photos and document files (e.g. PDF invoices).

### Why does the Cost form now have a Vehicle section at the top?

In 1.2, cost entries can carry an optional **odometer** and **GPS location** — same shape as fill-ups and charging sessions. The Vehicle section at the top groups the vehicle picker, odometer, and location row so they're easy to find and so a cost can light up on the Data → Map view as an orange wrench pin.

## Location

### How do I skip location capture for a single entry?

Tap the leading 📍 icon on the **Location** row (in Add Fuel, Add Charging Session, or Add Cost). The icon flips to a slashed variant and the row collapses to "Location · Off" — no GPS is persisted for this entry. Tap the icon again to re-enable. The toggle is per-entry; it doesn't change a global setting.

### How do I change the captured spot to somewhere else?

**Long-press the Location row** to open a map picker — drop a pin anywhere and tap **Use this location**. Your override wins over the live GPS fix. Tap the trailing 📍 (pin) icon to throw the override away and re-acquire from GPS.

### Why doesn't the Location row show coordinates anymore?

Raw lat/lon numbers were too wide for one line on iPhone mini and in Polish (where "Lokalizacja" is longer than "Location"). In 1.2 the row shows a reverse-geocoded place name like `Warsaw, PL` instead. The full-precision coordinate is still what's stored on the entry; this is just the display.

## Welcome Hints

### How do I bring back the welcome hints?

**Settings → Help → Show welcome hints again** → tap **Restart now** (or close the app yourself). On the next launch every coachmark is fresh again.

> Why a restart? TipKit's reset has to run *before* the framework is configured, and configuration happens during app launch. A flag in UserDefaults handles the handoff.

### Why don't the hints appear without restarting?

`Tips.resetDatastore()` is only honoured when called before `Tips.configure()`. There's no in-session API that re-eligibles tips reliably across all anchor surfaces. Restarting is fast and matches the same pattern Settings uses for language changes.

## Map

### Why don't I see all my costs / sessions on the Map?

Only entries with a GPS coordinate show up. If you (or older 1.1-era entries) captured no location, those rows are silently excluded. To bring an existing entry onto the map: open it, tap **Edit**, long-press the Location row, and pick a spot.

### How do I hide one of the pin types?

Tap the `≡` filter button in the Map toolbar (top-right) and untick the type you want to hide. The filter resets to all-visible each time you open the Map.

## Reminders

### How do distance-based reminders know when to trigger?

Distance-based reminders check the latest odometer reading each time you log a fill-up, charging session, or cost (with odometer), or when data is synced from a connected service. When the odometer approaches the target (within the lead distance), the reminder becomes "Due Soon".

### What happens when I mark a reminder as done?

The reminder advances by its recurrence interval. For date-based reminders, the due date moves forward by the specified number of days (default: 365). For distance-based reminders, the target odometer increases by the specified distance.

## EV / Electricity Bills

### Why didn't the Odometer field prefill when I picked a date?

Prefill only happens when a connected-service snapshot exists for the **exact calendar day** you selected. If the nearest snapshot is from a different day, the field stays empty so you can enter the reading yourself.

### Are Start and End odometers required?

No. They're optional. If you fill both in, the bill uses them directly to compute distance and **kWh / 100 km**. If you leave either empty, the bill falls back to automatic snapshot reconciliation against the previous bill.

### Why is the EV ➕ button doing two things?

A short tap adds a **charging session** (the more frequent action). A **long-press** adds an **electricity bill** (much less frequent — usually monthly). One button keeps the EV tab uncluttered; the first-launch hint floats over the button to explain both gestures.

## Connected Services

### How do I connect a Volvo without using the terminal?

Open **Settings → Integrations → Volvo**, paste your Client ID + Client Secret + VCC API Key (one-time setup from the Volvo developer portal), then tap **Sign in with Volvo**. The app opens Volvo ID's login page inside a sheet, you sign in normally, and the refresh token is captured + saved automatically — no Python script, no copying URLs from a terminal. See [Connected Services → Setup — Volvo](../connected-services/#setup--volvo).

### I previously generated a refresh token with the Python script — does it still work?

Yes. Existing tokens remain valid until they expire or are revoked. The Python helper at `scripts/get_volvo_token.py` is unchanged and still useful for CI or terminal-only workflows. The in-app sign-in is the recommended path for end users; the script is now a power-user fallback documented under **Account → Advanced** in Volvo settings.

### Why can't I see the odometer fetch button?

The fetch button only appears when:

1. Your vehicle's **Make** matches a supported manufacturer.
2. A **VIN** is entered in the vehicle settings.
3. The integration is connected in **Settings > Integrations**.

### Can I use Drivest without connecting to a vehicle service?

Absolutely. Connected services are entirely optional. You can enter all data manually.

### Can I schedule different fetch cadences for different cars?

Yes — that's the point of the **Fetch Data** Shortcut's Vehicle parameter. Build one Automation for your Volvo at 23:55 daily, another for your Toyota at 09:00 every Sunday, etc. Pick the vehicle in the Shortcut's parameter slot. Leave it blank to fall back to the old "fetch every connected vehicle in one run" behavior. See [Connected Services → Apple Shortcuts Integration](../connected-services/#apple-shortcuts-integration).

### My Shortcut named "Fetch Odometer" stopped working after updating — what happened?

The action was renamed to **Fetch Data** because the snapshot now includes battery state of charge and fuel level alongside the odometer. iOS treats the renamed action as a new identity, so your old Shortcut appears broken. Delete the missing step, add **Fetch Data** in its place, pick your vehicle (or leave blank), save. One-time fix.

### What does a red "Failed" badge in Readings mean?

It means a fetch attempt (from a Shortcut or background refresh) recorded a snapshot row but no new reading was retrieved. The row's subtitle carries the underlying reason — most often a rate limit or transient network/server error from the manufacturer's API. The app retries automatically before marking a snapshot as failed, and the row preserves the previous known odometer so the entry isn't blank. The next successful fetch records a fresh reading.

If you see *"Keychain locked — device must be unlocked at least once after boot"*, a scheduled fetch ran while the device was still locked from a reboot. Unlock the phone once and the next fetch will succeed; no action needed in the app. See [Connected Services → Reliability](../connected-services/#reliability) for details.

### How do I trigger a manual fetch?

Two ways:

1. **Long-press the Latest Reading card** on the Data tab.
2. **Tap the toolbar button** on **Data → Readings**.

Either records a new snapshot tagged with the **Manual** (accent-colored) badge.

## Language

### I picked a different language but the app is still in the old one — why?

iOS only applies a language change on app launch. After you pick a new language, Drivest writes the preference and shows an inline "Restart now" button under the picker. Tap it (or close the app and reopen it) and the new language takes effect.

The inline reminder persists across closing and re-opening Settings so you don't forget to restart.

## Backup

### How do I transfer data to a new phone?

1. Export each vehicle's data from **Settings > Manage Vehicles > [Vehicle] > Export Data**.
2. Save the `.drivestbackup` files to iCloud Drive or send them to yourself.
3. On your new phone, open each file and import it into Drivest.

### Can I import data from other fuel tracking apps?

Drivest only supports its own `.drivestbackup` format. You would need to convert data from other apps manually.

### Will a 1.1 backup import into 1.2?

Yes. The new optional fields added in 1.2 (cost odometer + location, EV battery capacity, charging-session fields) read as `nil` from older backups. No manual migration is needed.

## Troubleshooting

### The app shows "Unable to sync" banner

This means the app has failed to fetch data from a connected service multiple times. Go to **Settings > Integrations** and reconnect the affected service.

### Exchange rates are not updating

Tap **Refresh Rates Now** in **Settings > Currency**. If the error persists, check your internet connection. The NBP API may also be temporarily unavailable.

### I deleted a fill-up or cost by accident

Unfortunately, there is no undo for deletions. This is why regular backups are recommended — see [Backup & Restore](../backup-and-restore/).
