# Screenshot Placeholders — v1.1

Place PNG screenshots for **app version 1.1** in this directory (`static/images/docs/1.1/`). Each file is referenced from the docs pages as `/images/docs/1.1/<filename>.png`.

All screenshots should be iPhone screenshots (portrait, standard resolution).

## Versioned screenshots

Screenshots are organised by app version. When the app's documentation changes meaningfully (new screens, redesigned UI, renamed tabs), bump to a new folder rather than overwriting:

- `static/images/docs/1.0/` — frozen screenshots from the original release.
- `static/images/docs/1.1/` — this folder; current docs reference these.
- `static/images/docs/1.2/` — next version (to be created when the next release ships).

When you add a new version folder, copy this `SCREENSHOTS.md` and `SCREENSHOT_INSTRUCTIONS.md` into it as a starting point, then update the doc pages in `content/docs/` to point at the new `/images/docs/<version>/` prefix.

## Required Screenshots

| Filename | Page | What to capture |
|---|---|---|
| `getting-started-add-vehicle.png` | Getting Started | The "Add Vehicle" form filled with sample data — name, make, model, initial odometer. Fuel type and distance unit pickers should be visible. |
| `getting-started-main-screen.png` | Getting Started | The Fuel tab with the vehicle picker card at top (showing vehicle name and odometer), a list of fill-ups below, and the tab bar at bottom (Fuel, Costs, Data tabs). |
| `getting-started-vehicle-picker.png` | Getting Started | The vehicle picker dropdown expanded, showing two or more vehicles with a checkmark next to the selected one. |
| `fuel-tracking-add-fillup.png` | Fuel Tracking | The "Add Fill-Up" form with odometer, price per unit, volume, total cost fields filled with sample values. "Full Tank" toggle visible and turned on. |
| `fuel-tracking-location.png` | Fuel Tracking | The iOS system "While Using" location permission prompt over the fill-up form on first save, OR the fill-up detail page with a small map preview showing the captured fuel-stop location. |
| `fuel-tracking-receipt-scan.png` | Fuel Tracking | The camera view scanning a receipt, or the fill-up form after scanning with values auto-filled and the "Scan Receipt" button visible at top. |
| `fuel-tracking-efficiency.png` | Fuel Tracking | The Fuel tab list showing several fill-ups with date, volume, cost, and efficiency badges (e.g. "7.2 L/100km") on the right side. |
| `fuel-tracking-currency.png` | Fuel Tracking | The fill-up form with a currency badge (e.g. "EUR") visible next to the price field, showing a non-default currency selected. |
| `cost-tracking-add-cost.png` | Cost Tracking | The "Add Cost" form with a category picker showing icons (e.g. Insurance with shield icon selected), amount field filled, date picker, and "Create Reminder" toggle at bottom. |
| `cost-tracking-list.png` | Cost Tracking | The Costs tab showing a list of cost entries, each with category icon, name, amount, and date. |
| `cost-tracking-categories-a.png` | Cost Tracking | The "Categories" settings screen showing the list of categories with icons. |
| `cost-tracking-categories-b.png` | Cost Tracking | The "New Category" sheet open with name field filled and the icon selection grid visible. |
| `reminders-cost-form.png` | Reminders | Bottom section of "Add Cost" form with "Create Reminder" toggled on — type picker (Date/Distance), due date picker, "Remind days before" stepper visible. |
| `reminders-add.png` | Reminders | The "Add Reminder" screen with title, Date/Distance type selector, due date or target odometer fields, lead time config, and recurrence interval. |
| `reminders-list.png` | Reminders | Reminders list with different status badges: red "Overdue", orange "Due Soon", gray "Pending" — each with title, category icon, and due info. |
| `ev-add-bill.png` | EV Features | The "Add Electricity Bill" form with start date, end date, and amount fields. |
| `ev-tab.png` | EV Features | The EV tab showing the in-progress period card at top (with date range), navigation links below, and floating + button in bottom right. |
| `data-snapshot.png` | Data | The top of the Data tab: vehicle picker, the snapshot card with three rows (Average consumption, Last consumption, Last price) each with trend arrow + value, followed by the Stats / Charts / Map - Fill-ups list. |
| `data-snapshot-hybrid.png` | Data | The Data tab for a plug-in hybrid vehicle showing two snapshot cards stacked — one with a "Fuel" header, one with an "EV" header, each with its own three-metric layout. |
| `data-stats.png` | Data | The Stats detail page with three sections labeled "Last Month", "Last Year", and "All Time", each with Total Spent / Total Fuel / Fill-Ups / Avg Efficiency rows. |
| `data-charts.png` | Data | The Charts detail page: line chart at top, chart-type selector (Mileage / Efficiency / Fuel Price / Cost/km), period selector with All / YTD / Prev Y / This M / Prev M / Custom, summary section at the bottom. |
| `data-map.png` | Data | The Map - Fill-ups full-screen map with several round accent-coloured pins (each containing a fuel-pump glyph) scattered across a city or regional view, auto-zoomed to fit all pins. |
| `data-map-cluster.png` | Data | The Map - Fill-ups screen zoomed out enough that several fill-ups have merged into one or two cluster badges (each showing a count like "3" or "8"), with a few single pins also visible. |
| `data-map-detail.png` | Data | The Map - Fill-ups screen with the bottom detail sheet visible after tapping a single pin, showing the fill-up's date, fuel type, odometer, volume, price per litre, and total cost. |
| `ev-snapshot-history.png` | EV Features | The EV period detail screen with the snapshot history list visible: rows showing odometer + battery state of charge values and trailing badges (grey "Scheduled", accent "Manual", red "Failed" with an error message). |
| `currency-settings.png` | Currency | Currency settings screen — default currency picker at top (e.g. "PLN"), additional currencies section with rates (e.g. "EUR 4.3000"), last updated date, "Add Currency" and "Refresh Rates Now" buttons. |
| `connected-services-integrations.png` | Connected Services | Integrations settings showing supported manufacturers (with green checkmark for connected ones) and "Set auto fetch in Shortcuts" link with external link icon. |
| `connected-services-odometer-fetch.png` | Connected Services | Fill-up form odometer field with the circular download button visible next to the value, indicating connected service fetch is available. |
| `connected-services-snapshot-history.png` | Connected Services | The Snapshot History list for a vehicle showing rows with different badges: grey "Scheduled" with a fresh odometer, accent "Manual", and red "Failed" whose subtitle shows a "Keychain locked" or similar error message and where the previous odometer is carried over. |
| `backup-export-import.png` | Backup & Restore | Bottom of vehicle detail screen showing the "Data" section with "Export Data" and "Import Data..." buttons. |
| `backup-import-confirmation.png` | Backup & Restore | Import confirmation sheet showing data preview (vehicle name, fill-up/cost/reminder counts) and Merge/Replace strategy options. |
| `settings-main.png` | Settings | Full Settings screen — Manage Vehicles, Vehicle Order sort picker, Manage section (Currency, Categories, Integrations), Appearance theme picker (System/Light/Dark), Language, About. |
| `settings-appearance.png` | Settings | Close-up of Appearance section showing segmented control: System / Light / Dark, with "System" selected. |
