---
title: "Backup & Restore"
weight: 90
description: "Export and import your vehicle data"
---

Drivest lets you export and import your vehicle data using `.drivestbackup` files. This is useful for creating backups or transferring data between devices.

## Exporting Data

1. Go to **Settings > Manage Vehicles**.
2. Tap the vehicle you want to export.
3. In the vehicle detail screen, scroll to the **Data** section.
4. Tap **Export Data**.
5. Choose where to save or share the file using the iOS share sheet (e.g. save to Files, send via AirDrop, email).

The export creates a `.drivestbackup` file containing all data for that vehicle: fill-ups, costs, charging sessions, electricity bills, energy snapshots, reminders, photos, and attachments — with GPS coordinates and odometer values when present.

<!-- SCREENSHOT: Vehicle detail Data section — the bottom part of the vehicle detail screen showing the "Data" section with "Export Data" and "Import Data..." buttons. -->
![Export and import](/images/docs/1.2/backup-export-import.png)

## Importing Data

There are two ways to import:

### From the vehicle detail screen

1. Go to **Settings > Manage Vehicles**.
2. Tap the vehicle you want to import into.
3. Scroll to the **Data** section.
4. Tap **Import Data...** and select a `.drivestbackup` file.

### By opening a file

Tap any `.drivestbackup` file on your device (e.g. from the Files app or an email attachment). Drivest will open and show an import preview.

## Import Preview

Before importing, the app shows a preview of the data in the file and lets you choose an import strategy:

- **Merge** — adds the imported data alongside your existing records. Duplicate entries are skipped.
- **Replace** — replaces the vehicle's existing data with the imported data.

Review the preview carefully before confirming.

<!-- SCREENSHOT: Import confirmation — the import confirmation sheet showing a preview of the data to be imported (vehicle name, fill-up / cost / charging session / reminder counts) and the Merge/Replace strategy options. -->
![Import confirmation](/images/docs/1.2/backup-import-confirmation.png)

## What's Included in a Backup

- Vehicle information (name, make, model, VIN, settings, battery capacity for EVs)
- All **fill-up** records with photos and GPS coordinates (when captured)
- All **cost entries** with photos, file attachments, **odometer**, and **GPS coordinates** (new in 1.2)
- All **charging sessions** with photos, odometer, and GPS coordinates
- All **electricity bills**
- **Reminders**
- **Energy snapshots** (odometer + battery state of charge + fuel level fetched from connected services, plus the trigger badge — Scheduled / Manual / Failed)

### Backwards-compatible imports

The new optional fields added in 1.2 (cost odometer, cost location, charging-session fields, battery capacity) are read as `nil` from older backups produced by 1.1 — no manual migration is needed, and re-exporting an imported 1.1 backup from 1.2 will round-trip the data cleanly.

## What's Not Included

- App-wide settings (currency, categories, appearance, language preference)
- Connected service credentials (authentication tokens)
- The on-device cache of receipt photos beyond what's attached to a record

## Tips

- Export your data regularly, especially before updating iOS or switching devices.
- Store backups in iCloud Drive or another cloud service for safekeeping.
- You can export and import individual vehicles — there is no "export all" option, so back up each vehicle separately.
