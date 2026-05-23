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
- Syncing odometer data from a connected vehicle service.

### Where is my data stored?

All data is stored locally on your device using Apple's SwiftData framework. Nothing is sent to any external server. See the [Privacy Policy](/privacy/) for details.

### Can I use Drivest on iPad?

Drivest is designed for iPhone and requires iOS 17.0 or later.

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

## Reminders

### How do distance-based reminders know when to trigger?

Distance-based reminders check the latest odometer reading each time you log a fill-up or when data is synced from a connected service. When the odometer approaches the target (within the lead distance), the reminder becomes "Due Soon".

### What happens when I mark a reminder as done?

The reminder advances by its recurrence interval. For date-based reminders, the due date moves forward by the specified number of days (default: 365). For distance-based reminders, the target odometer increases by the specified distance.

## EV / Electricity Bills

### Why didn't the Odometer field prefill when I picked a date?

Prefill only happens when a connected-service snapshot exists for the **exact calendar day** you selected. If the nearest snapshot is from a different day, the field stays empty so you can enter the reading yourself. See [EV Features → Odometer prefill](../ev-features/#odometer-prefill).

### Are Start and End odometers required?

No. They're optional. If you fill both in, the app uses them directly to compute distance and **kWh / 100 km**. If you leave either empty, the bill falls back to automatic snapshot reconciliation against the previous bill.

## Connected Services

### Why can't I see the odometer fetch button?

The fetch button only appears when:
1. Your vehicle's **Make** matches a supported manufacturer.
2. A **VIN** is entered in the vehicle settings.
3. The integration is connected in **Settings > Integrations**.

### Can I use Drivest without connecting to a vehicle service?

Absolutely. Connected services are entirely optional. You can enter all data manually.

### What does a red "Failed" badge in Snapshot History mean?

It means a fetch attempt (from a Shortcut or background refresh) recorded a snapshot row but no new odometer reading was retrieved. The row's subtitle carries the underlying reason — most often a rate limit or transient network/server error from the manufacturer's API. The app retries automatically before marking a snapshot as failed, and the row preserves the previous known odometer so the entry isn't blank. The next successful fetch records a fresh reading.

If you see *"Keychain locked — device must be unlocked at least once after boot"*, a scheduled fetch ran while the device was still locked from a reboot. Unlock the phone once and the next fetch will succeed; no action needed in the app. See [Connected Services → Reliability](../connected-services/#reliability) for details.

## Backup

### How do I transfer data to a new phone?

1. Export each vehicle's data from **Settings > Manage Vehicles > [Vehicle] > Export Data**.
2. Save the `.drivestbackup` files to iCloud Drive or send them to yourself.
3. On your new phone, open each file and import it into Drivest.

### Can I import data from other fuel tracking apps?

Drivest only supports its own `.drivestbackup` format. You would need to convert data from other apps manually.

## Troubleshooting

### The app shows "Unable to sync" banner

This means the app has failed to fetch data from a connected service multiple times. Go to **Settings > Integrations** and reconnect the affected service.

### Exchange rates are not updating

Tap **Refresh Rates Now** in **Settings > Currency**. If the error persists, check your internet connection. The NBP API may also be temporarily unavailable.

### I deleted a fill-up or cost by accident

Unfortunately, there is no undo for deletions. This is why regular backups are recommended — see [Backup & Restore](../backup-and-restore/).
