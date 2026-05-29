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
- [Data](data/) — Latest Reading card, Latest Location card, Stats, Charts, Map, Readings
- [Currency](currency/) — Default currency, additional currencies, exchange rates
- [Connected Services](connected-services/) — Vehicle manufacturer integrations, Shortcuts
- [Backup & Restore](backup-and-restore/) — Export and import your data
- [Settings](settings/) — Appearance, language, categories, vehicle order, welcome hints
- [FAQ](faq/) — Frequently asked questions and troubleshooting

## What's New in 1.3

### Charts overhaul

- **Swipe through history on every chart** — Spending, Odometer, Consumption, Cost/km, and Efficiency all support horizontal scrolling. The visible-window width follows the period pill: Daily = 7 days, Weekly = 28 days, Monthly = 6 months, Yearly = 6 years.
- **Period header above each chart** — a centered date range tracks the visible window as you swipe (`May 18 – 24, 2026` on Daily; `Jul 2024 – Feb 2026` for fit-to-screen).
- **Smart granularity switching** — flipping between Daily / Weekly / Monthly / Yearly preserves your view position instead of jumping to the latest data. If the new (narrower) window would contain no data, the chart auto-shifts to the closest data point so you always see something.
- **Sparse-data charts auto-fit to screen** — a Yearly view on a vehicle with only 6 months of data no longer crushes the line into the leftmost ~15 % of the chart. The chart switches to fit-to-screen automatically and gains horizontal scroll the moment the data grows past the window's threshold.
- **Daily X-axis simplified** — day numbers only (`18 19 20 …`), no repeated month name. The period header above the chart already names the month.
- **Yearly window bumped from 4 → 6 years** — gives the same 6 X-axis ticks as the Monthly view.
- **Quarterly stride for 1–3 year spans** — the previous "month stride everywhere up to 2 years" rule produced 20+ overlapping labels on a Yearly Consumption view with 20 months of data. The X-axis now auto-picks a coarser stride when the visible window is wide.
- **Tighter Y axis on Odometer** — the visible window's Y range now scales to what you're actually looking at, with linearly-interpolated values at the window edges so a gap between fillups still shows a sensibly-bounded line instead of a flat smear against the 20 k–55 k km global range.
- **Stable Y axis on Consumption / Efficiency / Cost/km** — these fluctuating series keep a global Y axis so values are comparable across windows; the sliding Y on Odometer would have been too jumpy here.

### Other improvements

- **Odometer "Total" = current dial reading** — the Total cell on the Odometer chart now reflects the highest odometer reading in view (matches what the car's dashboard shows), not just the distance Drivest registered in the window. Avg-per-period still measures driven km.
- **PHEV legend keeps both Fuel and EV entries visible** — if one series has no data yet, its pill is rendered in a grayed/disabled state instead of vanishing, so the chart doesn't read as a misconfiguration.
- **Cards now visible in Dark Mode** — the Stats and Charts summary cards switched from a flat background to a grouped one. In Dark Mode the card boundaries finally show up against the page background (in Light Mode they stay white, as before).
- **Data tab compacted on iPhone 13 mini** — the Latest Location card's map shrank from 160 → 110 pt so the **Stats / Charts / Map / Readings** rows fit on a 5.4″ screen without scrolling.

### Performance & reliability (from late 1.2.x)

- **Receipt OCR off the main thread** — Vision text recognition now runs on a background queue, so the scanner sheet no longer freezes the UI while parsing large receipts.
- **NBP exchange rate backoff** — failed NBP fetches no longer hammer the API on every foreground transition; the service now waits 1 hour after a failure before retrying.
- **Save errors no longer swallowed silently** — bill add/edit/delete operations now route through a unified save path that logs failures via the system logger instead of dropping them.

Looking for older documentation? See [v1.2 docs](v1.2/) and [v1.1 docs](v1.1/).

## Requirements

- iOS 17.0 or later
- iPhone

## Support

Drivest is free and open source. If you have questions or find a bug, visit the [GitHub repository](https://github.com/andrzejsiemion/drivest-ios).
