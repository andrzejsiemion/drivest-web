---
title: "Data"
weight: 60
description: "Latest Reading card, Stats, Charts, Map, Efficiency, and Readings"
---

The **Data** tab is the hub for everything analytical about the selected vehicle. It shows the **Latest Reading** card (for connected EV vehicles) at the top, followed by a list of pushable destinations: **Stats**, **Charts**, **Map**, **Efficiency**, and **Readings**.

Every detail screen below shows the vehicle's name as a subtitle under its title so you always know which car you're looking at.

## Latest Reading Card

When the selected vehicle has a connected service integration that returns energy data (Volvo, Toyota EVs), a snapshot card sits between the vehicle picker and the menu list. It shows up to three at-a-glance metrics:

- **Odometer** (km / mi) — current mileage from the latest snapshot.
- **Battery** (%) plus an estimated remaining range if the API returns one.
- **Fuel** (L / gal) plus an estimated remaining range — for plug-in hybrids whose API exposes fuel level.

A timestamp on the right tells you how long ago the snapshot was taken.

<!-- SCREENSHOT: Latest Reading card — the top of the Data tab for a connected EV vehicle, showing the vehicle picker followed by the Latest Reading card with the odometer / battery / fuel rows on the left and the relative timestamp on the right, followed by the Stats / Charts / Map / Efficiency / Readings list below. -->
![Latest Reading card](/images/docs/1.2/data-latest-reading.png)

### Gestures

- **Tap the card** → opens the snapshot detail (every field returned for that snapshot).
- **Long-press the card** → triggers a manual fetch from the vehicle API. While the fetch is in flight, an inline spinner replaces the timestamp.

A welcome hint on first use explains both gestures. It dismisses itself the first time you use either.

For non-EV or non-connected vehicles, this card is hidden and the menu list starts right after the vehicle picker.

## Stats

Tap **Stats** for a comparison of three time periods:

- **Last Month** — fill-ups in the last 30 days.
- **Last Year** — fill-ups in the last 365 days.
- **All Time** — every fill-up on file.

Each period shows:

- **Total Spent** — total amount spent on fuel.
- **Total Fuel** — total volume added.
- **Fill-Ups** — number of fill-up records.
- **Avg Efficiency** — average fuel efficiency, when computable.

If you have a default currency set, amounts are shown in that currency. Fill-ups recorded in other currencies are converted using the exchange rate at the time of the fill-up.

<!-- SCREENSHOT: Stats screen — the Stats detail page showing the vehicle name as a subtitle under the title, then three stacked sections labeled "Last Month", "Last Year", and "All Time", each with rows for Total Spent, Total Fuel, Fill-Ups, and Avg Efficiency. -->
![Stats](/images/docs/1.2/data-stats.png)

## Charts

Tap **Charts** for a visual trend chart. You can switch between:

- **Mileage** — cumulative odometer over time.
- **Efficiency** — fuel efficiency trend.
- **Fuel Price** — price per unit trend.
- **Cost/km** — running cost per kilometre.

Use the period selector below the chart to filter by time range — **All**, **YTD**, **Prev Y**, **This M**, **Prev M**, or **Custom**. A summary section underneath shows total spent, total fuel, fill-up count, and average efficiency for the selected period.

<!-- SCREENSHOT: Charts screen — the Charts detail page with the vehicle name subtitle, a line chart at top, the chart-type selector (Mileage / Efficiency / Fuel Price / Cost/km), the period selector (All / YTD / Prev Y / This M / Prev M / Custom), and the summary section underneath. -->
![Charts](/images/docs/1.2/data-charts.png)

## Map

Tap **Map** for a full-screen map showing every location-tagged record for the selected vehicle — fill-ups, costs, and charging sessions on a single map. The map auto-centres and zooms to fit every pin. If the selected vehicle has nothing geo-tagged, an empty-state message explains how to enable it (see [Fuel Tracking → Location Capture](../fuel-tracking/#location-capture)).

<!-- SCREENSHOT: Unified map — the Map full-screen view with a mix of pin colours: green fuel-pump pins (fill-ups), orange wrench pins (cost entries), and blue lightning-bolt pins (charging sessions) scattered across a city or regional view, auto-zoomed to fit all pins. The toolbar shows the filter (≡) button in the top-right. -->
![Unified map](/images/docs/1.2/data-map.png)

### Pin Types

| Pin | Entity | Tint |
|---|---|---|
| ⛽ fuel pump | Fill-up | Accent (green) |
| 🔧 wrench | Cost entry | Orange |
| ⚡ bolt | Charging session | Blue |

A pin's coordinate comes from the entity's stored GPS — entries without a location are silently excluded from the map.

### Clusters

When two or more pins (of any mix of types) overlap at the current zoom level, they collapse into a single round badge showing the **count**. Tap a cluster to zoom in; the pins will split into smaller clusters or individual pins as the camera moves. If pins share the exact same coordinate (e.g. several fill-ups at the same gas station), tapping the cluster instead opens a chooser list with mixed-type rows.

<!-- SCREENSHOT: Map clusters — the Map screen zoomed out enough that several pins have merged into cluster badges (each showing a count like "3" or "8"), with a few single pins of different types also visible. -->
![Map clusters](/images/docs/1.2/data-map-cluster.png)

### Filtering

A `≡` filter button sits in the toolbar (top-right). Tap it to reveal three toggles — **Fill-ups**, **Costs**, **Charging sessions**. Turn any off to hide that pin type from the map. The filter resets to "all visible" each time you re-open the Map (it isn't persisted).

When all three filters are off, an inline empty state says "Nothing to show — turn a filter back on."

<!-- SCREENSHOT: Map filter — the filter sheet open from the toolbar showing three toggles (Fill-ups, Costs, Charging sessions). At least one toggle should be off so the difference is visible against the map underneath. -->
![Map filter](/images/docs/1.2/data-map-filter.png)

### Tapping a Single Pin

Tapping a pin slides up a per-type detail sheet:

- **Fill-up** → date, fuel type, odometer, volume, price/L, total cost, plus a **View Details** button that pushes the full editable Fill-Up detail.
- **Cost** → date, category icon, amount, plus **View Details** to push the Cost detail.
- **Charging session** → date, location name (if set), kWh, total cost, plus **View Details** to push the Session detail.

<!-- SCREENSHOT: Map detail sheet — the Map screen with a per-type detail sheet slid up from the bottom after tapping a single pin. Showing a charging-session sheet (date, location name, kWh, total cost, View Details button) is preferred because it's new in 1.2 — a cost or fill-up variant is also acceptable. -->
![Map detail sheet](/images/docs/1.2/data-map-detail.png)

## Efficiency

Tap **Efficiency** for a period-aware breakdown of fuel and EV consumption alongside one another. A **Granularity** toggle switches the chart between:

- **Per fill-up / per bill** (default) — one chart point per record.
- **Daily** — one point per day, derived from the snapshot stream (requires a connected service). For EVs without `Battery Capacity (kWh)` set, the Y-axis is `km / %`; with capacity set, the chart switches to `kWh / 100 km`.

A summary card at the top of the screen shows period totals and average consumption. The period picker matches the one on Charts.

<!-- SCREENSHOT: Efficiency screen — the Efficiency detail screen with the vehicle name subtitle, a summary card at the top with period totals, a chart in the middle (showing fuel + EV trends), and the Per fill-up / Daily granularity toggle plus the period picker below the chart. -->
![Efficiency](/images/docs/1.2/data-efficiency.png)

## Readings

Tap **Readings** for a flat chronological list of every energy snapshot fetched from your connected services. Each row shows the timestamp, odometer, battery (and fuel where applicable), and a **trigger badge**:

- **Scheduled** (grey) — a routine background or Shortcuts fetch that succeeded.
- **Manual** (accent) — a user-triggered fetch (from the Latest Reading card long-press or the toolbar button on this screen).
- **Failed** (red) — a fetch attempt that didn't produce a snapshot. The row's subtitle shows the reason.

A **toolbar button** at the top-right of the list triggers a manual fetch on demand. Useful for testing that the integration is alive or for prompting an immediate snapshot before recording a fill-up.

<!-- SCREENSHOT: Readings list — the Readings screen with the vehicle name subtitle, the manual-fetch toolbar button in the top-right, and a list of snapshot rows showing odometer + battery values with a mix of badges (grey "Scheduled", accent "Manual", red "Failed" with an error message). -->
![Readings](/images/docs/1.2/data-readings.png)

## Switching Vehicles

Use the vehicle picker at the top of the Data tab to view data for a specific vehicle. Each vehicle has its own independent Latest Reading card, stats, charts, map, efficiency, and readings list.
