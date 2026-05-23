---
title: "Cost Tracking"
weight: 30
description: "Recording vehicle expenses by category, with odometer and location"
---

## Adding a Cost

1. Go to the **Costs** tab.
2. Tap the **+** button.
3. Fill in the details (the Vehicle section sits at the top so it stays visible while you scroll the rest of the form):
   - **Vehicle** (when you have multiple vehicles) — pick the car this cost belongs to.
   - **Odometer** — optional mileage reading at the time of the cost. If the vehicle is connected (Volvo / Toyota with the integration set up), this field auto-populates from the latest snapshot when you change vehicles.
   - **Location** — auto-captured GPS, with the same toggle / refresh / long-press behaviour as on the Fuel form. See [Fuel Tracking → Location Capture](../fuel-tracking/#location-capture).
   - **Category** — select a category (e.g. Insurance, Service, Tolls, Wash, Parking, Maintenance, Tickets).
   - **Amount** — the cost amount (Category + Amount share one section to save vertical space).
   - **Date** — when the expense occurred.
   - **Note** — optional description.
   - **Reminder** — optionally create a reminder for this expense (see [Reminders](../reminders/)).
   - **Photos** — attach photos of receipts or documents.
   - **Files** — attach document files (e.g. PDF invoices).
4. Tap **Save**.

<!-- SCREENSHOT: Add cost form — the "Add Cost" screen with the Vehicle section at the top (vehicle picker, odometer field with the connected-service download button, location row with a captured place name), then the Category picker showing icons (e.g. Insurance with shield icon selected), amount field filled, date picker, and "Create Reminder" toggle at bottom. -->
![Add cost](/images/docs/1.2/cost-tracking-add-cost.png)

### Why odometer and location?

When a cost is tagged with mileage, future Drivest features can correlate spend with kilometres driven (cost-per-km style analyses) the same way fill-ups and charging sessions already do. When a cost carries GPS, it appears on the unified [**Data → Map**](../data/#map) view as an orange wrench icon — so your mechanic shops, car washes, parking lots, and tolls land on the same map as your gas stations. Both fields are optional; leaving them empty is fine for costs where they're not relevant (e.g. an annual insurance payment).

### Disabling location for a single entry

Tap the leading 📍 icon on the Location row to flip it to a slashed icon — capture turns off, the row collapses to "Location · Off", and no GPS is persisted for this entry. Useful for purely administrative costs paid online from home.

## Categories

The app comes with built-in categories:

- Insurance
- Service
- Tolls
- Wash
- Parking
- Maintenance
- Tickets

<!-- SCREENSHOT: Cost list — the Costs tab showing a list of cost entries grouped or listed chronologically, each with category icon, name, amount, and date. -->
![Cost list](/images/docs/1.2/cost-tracking-list.png)

### Custom Categories

You can create your own categories and reorder or delete existing ones:

1. Go to **Settings > Categories**.
2. Tap **+** to add a new category.
3. Enter a name and choose an icon.
4. Tap **Add**.

To reorder categories, tap **Edit** and drag them into your preferred order. To delete a category, swipe left or use the Edit mode.

<!-- SCREENSHOT: Category list — the Categories settings screen showing the list of categories with icons. -->
![Category list](/images/docs/1.2/cost-tracking-categories-a.png)

<!-- SCREENSHOT: New category — the "New Category" sheet open with name field filled and the icon selection grid visible. -->
![New category](/images/docs/1.2/cost-tracking-categories-b.png)

## Multi-Currency Support

If you have multiple currencies configured, a currency selector appears next to the amount field. The cost will be recorded with the selected currency and its exchange rate.

## Editing and Deleting

- Tap any cost entry in the list to view its details. The detail view shows odometer and location only when those fields are present.
- Tap **Edit** to modify a cost. The same Vehicle section (with odometer at the top) is at the top of the Edit form for parity with Add.
- Swipe left on a cost entry to delete it.
