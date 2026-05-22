---
title: "Documentation"
description: "Drivest user documentation — learn how to track your vehicle costs"
---

Drivest is a vehicle cost and fuel tracking app for iOS. All your data stays on your device — no accounts, no servers, no tracking.

## Guides

- [Getting Started](getting-started/) — First launch, adding your first vehicle, welcome hints
- [Fuel Tracking](fuel-tracking/) — Logging fill-ups, receipt scanning, fuel efficiency
- [Cost Tracking](cost-tracking/) — Recording expenses by category, with odometer and location
- [Reminders](reminders/) — Date-based and distance-based reminders
- [EV Features](ev-features/) — Charging sessions, electricity bills, EV tracking
- [Data](data/) — Latest Reading card, Stats, Charts, Map, Efficiency, Readings
- [Currency](currency/) — Default currency, additional currencies, exchange rates
- [Connected Services](connected-services/) — Vehicle manufacturer integrations, Shortcuts
- [Backup & Restore](backup-and-restore/) — Export and import your data
- [Settings](settings/) — Appearance, language, categories, vehicle order, welcome hints
- [FAQ](faq/) — Frequently asked questions and troubleshooting

## What's New in 1.2

- **One Map for everything** — the Data → Map view now shows fill-ups, costs, and charging sessions on a single map, with a toolbar filter to toggle each type.
- **Cost entries carry odometer and location** — same auto-capture pattern as fill-ups and charging sessions, so wrench-shop visits and parking tickets land on the map too.
- **EV tab redesigned** — bills and charging sessions are now a single flat history list. One ➕ button: short tap adds a charging session, long-press adds an electricity bill.
- **Edit Charging Session** — the charging-session detail screen gets an Edit toolbar button (mirroring fill-ups).
- **Latest Reading card moved to Data** — the live odometer / battery / fuel snapshot card now lives at the top of the Data tab for connected EV vehicles. Long-press to trigger a manual fetch.
- **New Readings list** — `Data → Readings` is a flat history of every snapshot from your connected services with a Scheduled / Manual / Failed badge.
- **Per-entry location toggle** — every Add form has a small icon on the Location row that lets you skip GPS capture for that entry.
- **Place names instead of coordinates** — the captured-location row now shows `Warsaw, PL` rather than raw coordinates.
- **In-app Volvo sign-in** — tap Sign in with Volvo in the integration settings and complete the Volvo ID OAuth flow inside an in-app browser. No more Python script required for end users.
- **Per-vehicle Shortcuts** — the Fetch Data action (renamed from "Fetch Odometer") takes an optional Vehicle parameter so you can build separate scheduled syncs per car.
- **Welcome hints** — first-launch contextual coachmarks point out non-obvious gestures. Replayable from Settings → Help.
- **Vehicle subtitle on detail screens** — Stats, Charts, Map, Efficiency, and Readings screens now show the active vehicle name under the title.
- **Fuel tab hides for pure-EV vehicles** — symmetric with how the EV tab hides for petrol-only vehicles.

Looking for older documentation? See [v1.1 docs](v1.1/).

## Requirements

- iOS 17.0 or later
- iPhone

## Support

Drivest is free and open source. If you have questions or find a bug, visit the [GitHub repository](https://github.com/andrzejsiemion/drivest-ios).
