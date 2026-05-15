---
title: "EV Features"
weight: 50
description: "Electricity bills and EV cost tracking"
---

If any of your vehicles is set to the **EV** fuel type (either as the primary or second tank), an **EV** tab appears in the app.

## Electricity Bills

Track your home charging costs by logging electricity bills.

1. Go to the **EV** tab.
2. Tap the **+** button.
3. Enter the bill details:
   - **Start Date** and **End Date** — the billing period.
   - **Amount** — the total bill amount.
4. Tap **Save**.

<!-- SCREENSHOT: Add electricity bill — the "Add Electricity Bill" form with start date, end date, and amount fields. -->
![Add electricity bill](/images/docs/1.1/ev-add-bill.png)

## In-Progress Periods

The EV tab shows the current billing period at the top if there is an electricity bill in progress. Tap it to see details for that period.

<!-- SCREENSHOT: EV tab — the EV tab showing the in-progress period card at the top (with date range), followed by navigation links, and the floating + button in the bottom right. -->
![EV tab](/images/docs/1.1/ev-tab.png)

## Sync Failure Banner

If the app fails to sync odometer data from a connected service multiple times in a row, a warning banner appears at the top of the screen. Reconnect the integration from **Settings > Integrations** to resolve the issue.

## EV Stats on the Data Tab

When a vehicle is EV-enabled, the [**Data**](../data/) tab shows an **EV** snapshot card with average kWh/100km, last kWh/100km, and the most recent cost per kWh — alongside a **Fuel** card if the vehicle also has a combustion tank (plug-in hybrid). See [Data → Vehicle Snapshot Card](../data/#vehicle-snapshot-card) for details.

## Snapshot History

For connected vehicles (Volvo, Toyota), each automatic fetch records an **energy snapshot** with the odometer and battery state of charge at that moment. Open the **EV** tab → period card → snapshot history list to see each row. Badges indicate how the fetch was triggered:

- **Scheduled** (grey) — a routine background or Shortcuts fetch that succeeded.
- **Manual** (accent) — a user-triggered fetch.
- **Failed** (red) — a fetch attempt that didn't produce a snapshot. The row's subtitle shows the reason — typically a transient API error, a missing/expired integration token, or a "Keychain locked" message when a background fetch fired before the device had been unlocked after a reboot. See [Connected Services → Reliability](../connected-services/#reliability).

<!-- SCREENSHOT: EV snapshot history — the EV period detail screen with the snapshot history list visible: rows showing odometer + battery state of charge values and badges in the trailing edge (grey "Scheduled", accent "Manual", red "Failed" with an error message). -->
![EV snapshot history](/images/docs/1.1/ev-snapshot-history.png)

## Requirements

- At least one vehicle must have its fuel type set to **EV** (either as primary fuel type or as a second tank).
