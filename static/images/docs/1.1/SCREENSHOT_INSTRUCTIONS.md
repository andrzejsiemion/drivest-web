# How to Capture Documentation Screenshots — v1.1

Step-by-step instructions for reproducing each screenshot for **app version 1.1** using the iOS Simulator.

## Folder convention

Save the resulting PNGs in `static/images/docs/1.1/` using the exact filenames listed in `SCREENSHOTS.md`. The docs pages reference them as `/images/docs/1.1/<filename>.png`.

When a future app release ships meaningful UI changes, create the next version folder (e.g. `static/images/docs/1.2/`), copy this file in as a starting point, re-capture only the screenshots that changed, and update `content/docs/*.md` to point at the new prefix.

## General Setup

### Simulator

1. Open Xcode and build Drivest for an **iPhone 16 Pro** simulator.
2. Set the simulator to **English** language:
   - In Xcode: Product > Scheme > Edit Scheme > Run > Options > App Language > English.
3. For each screenshot, capture both light and dark variants if needed.
4. Take screenshots with **Cmd + S** in the Simulator (saves to Desktop).
5. Screenshots should be taken at **1x scale** for consistency — in the Simulator menu: Window > Physical Size.

### App State

Before capturing, delete and reinstall the app to start clean, then build up the
data as described below. Alternatively, use the `xcrun simctl` commands in the
"Quick State Setup" section to inject data without going through the UI.

### Quick State Setup (optional)

You can write UserDefaults directly to the simulator to create specific states:

```bash
# Find the booted simulator ID
DEVICE=$(xcrun simctl list devices booted -j | python3 -c "import sys,json; print(json.loads(sys.stdin.read())['devices'].values().__iter__().__next__()[0]['udid'])")

# Write a UserDefaults key to the app container
xcrun simctl spawn $DEVICE defaults write pro.siemion.drivest <KEY> <VALUE>
```

---

## Screenshot-by-Screenshot Instructions

### getting-started-add-vehicle.png

**What to show:** The "Add Vehicle" form with sample data.

1. Launch the app fresh (no vehicles).
2. The app shows the empty state — tap **+** to add a vehicle.
3. Fill in:
   - Name: `My Car`
   - Make: `Volvo`
   - Model: `XC60`
   - Initial Odometer: `45230`
4. Set Distance Unit to **Kilometers**, Fuel Type to **Diesel**, Fuel Unit to **Liters**.
5. Screenshot the form before tapping Save — scroll so the fuel type and distance unit pickers are visible.

---

### getting-started-main-screen.png

**What to show:** The Fuel tab with a vehicle card and a list of fill-ups.

1. Create a vehicle (e.g. "My Car", Volvo XC60).
2. Add 3–4 fill-ups with varied data:
   - Dates spread over the last 2 months.
   - Different volumes (35–50 L) and prices.
   - Toggle "Full Tank" on for most so efficiency badges appear.
3. Go to the **Fuel** tab.
4. Screenshot with the vehicle picker card at top and the fill-up list below. The tab bar at bottom should show Fuel, Costs, Data.

---

### getting-started-vehicle-picker.png

**What to show:** The vehicle picker dropdown expanded with multiple vehicles.

1. Create at least 2 vehicles (e.g. "My Car" and "Family Van").
2. On the Fuel tab, tap the vehicle picker card at the top.
3. The dropdown opens showing both vehicles with a checkmark on the selected one.
4. Screenshot while the dropdown is visible.

---

### fuel-tracking-add-fillup.png

**What to show:** The "Add Fill-Up" form with sample data filled in.

1. From the Fuel tab, tap **+**.
2. Fill in:
   - Odometer: `46120`
   - Price per Unit: `6.49`
   - Volume: `42.35`
   - Total Cost should auto-calculate to `274.85`.
   - Toggle **Full Tank** on.
3. Screenshot the form.

---

### fuel-tracking-location.png

**What to show:** Either the iOS "While Using" location permission prompt on top of the fill-up form, or a saved fill-up's detail page with a map preview showing the captured fuel-stop location.

**Option A — Permission prompt (recommended):**

1. Reset the simulator's location permissions:
   ```bash
   xcrun simctl privacy booted reset location pro.siemion.drivest
   ```
2. Launch the app on a vehicle with no prior fill-ups so the first save triggers the prompt.
3. From the Fuel tab, tap **+**, fill in basic values, tap **Save**.
4. The iOS system prompt asks for "While Using" location — screenshot at that moment.

**Option B — Detail page with map preview:**

1. Grant "While Using" location permission for Drivest.
2. Set a custom simulator location: in the Simulator menu, **Features > Location > Custom Location...** (use a recognisable place, e.g. a city centre).
3. Add a fill-up. After saving, open the fill-up detail page.
4. Screenshot showing the small map preview with a pin at the captured location.

**Option C — Add-screen Location row (covers the new manual-adjust UX):**

1. Grant "While Using" location permission and set a custom simulator location as in Option B.
2. From the Fuel tab, tap **+**. Scroll the form until the **Location** row is in view; it shows the current GPS fix with a pin icon on the trailing edge.
3. To capture the long-press affordance: long-press the row — a map sheet opens with a draggable pin. Screenshot the map sheet (this version is the most informative).
4. Alternatively, screenshot the Location row itself with the pin icon visible, since `Adjust on the Add screen` is now documented.

---

### fuel-tracking-receipt-scan.png

**What to show:** The fill-up form with the "Scan Receipt" button visible.

1. From the Fuel tab, tap **+**.
2. Screenshot showing the form with the **Scan Receipt** button at the top of the Fuel section.

> Note: The camera is not available in the Simulator. Show the button itself as the focal point. If you want to show auto-filled values, manually enter sample values and keep the Scan Receipt button visible in the screenshot.

---

### fuel-tracking-efficiency.png

**What to show:** Fill-up list with efficiency badges.

1. Create a vehicle and add at least 3 fill-ups:
   - All with **Full Tank** toggled on.
   - Increasing odometer readings (e.g. 45000, 45600, 46200, 46850).
   - Volumes around 35–45 L.
2. Go to the Fuel tab — efficiency badges (e.g. "7.2 L/100km") should appear next to each fill-up (except the first one).
3. Screenshot the list.

---

### fuel-tracking-currency.png

**What to show:** The fill-up form with a non-default currency selected.

1. Go to **Settings > Currency**.
2. Set default currency to **PLN**.
3. Add **EUR** as an additional currency.
4. Go to Fuel tab, tap **+** to add a fill-up.
5. Tap the currency badge next to "Price per Unit" and select **EUR**.
6. Enter a price (e.g. `1.85`) — the converted amount in PLN should appear below Total Cost.
7. Screenshot showing the EUR badge and the conversion line.

---

### cost-tracking-add-cost.png

**What to show:** The "Add Cost" form with a category selected and reminder toggle visible.

1. Go to the **Costs** tab, tap **+**.
2. Select category **Insurance** (shield icon).
3. Enter amount: `2400`
4. Scroll down so the **Create Reminder** toggle is visible (leave it off).
5. Screenshot the form.

---

### cost-tracking-list.png

**What to show:** The Costs tab with several cost entries.

1. Add 3–5 cost entries with different categories:
   - Insurance: 2400, dated 3 months ago.
   - Service: 850, dated 1 month ago.
   - Wash: 35, dated last week.
   - Parking: 12, dated yesterday.
2. Go to the Costs tab.
3. Screenshot the list showing category icons, names, amounts, and dates.

---

### cost-tracking-categories-a.png

**What to show:** The Categories management list.

1. Go to **Settings > Categories**.
2. Screenshot the list of categories with their icons.

---

### cost-tracking-categories-b.png

**What to show:** The "New Category" sheet with name and icon grid.

1. From **Settings > Categories**, tap **+**.
2. Type a name (e.g. `Accessories`).
3. Select an icon from the grid (e.g. the star icon).
4. Screenshot the sheet with the name and icon grid visible.

---

### reminders-cost-form.png

**What to show:** The "Create Reminder" section of the Add Cost form expanded.

1. Go to the **Costs** tab, tap **+**.
2. Select a category (e.g. Insurance), enter an amount.
3. Toggle **Create Reminder** on.
4. Set type to **Date**.
5. Set a Due Date (e.g. 1 year from now).
6. Set "Remind days before" to **14**.
7. Screenshot showing the expanded reminder section with date picker and days stepper.

---

### reminders-add.png

**What to show:** The standalone "Add Reminder" form.

1. Go to **Settings > Manage Vehicles** > tap your vehicle.
2. Find the Reminders section, tap **+** (or navigate to Reminders list and tap +).
3. Fill in:
   - Title: `Oil Change`
   - Type: **Distance**
   - Target odometer: `50000`
   - Lead distance: `500`
   - Reset interval: `15000`
4. Screenshot the form.

---

### reminders-list.png

**What to show:** Reminders with different status badges (Overdue, Due Soon, Pending).

1. Create a vehicle with initial odometer `45000`.
2. Add a fill-up at odometer `48500` so the app knows the current odometer.
3. Create 3 reminders:
   - **Overdue (red):** date-based reminder with a due date in the past (e.g. yesterday) — or distance-based with target `48000` (below current odometer).
   - **Due Soon (orange):** date-based with due date 5 days from now, lead days = 14 — or distance-based with target `49000`, lead distance `1000`.
   - **Pending (gray):** date-based with due date 6 months from now, lead days = 14.
4. Navigate to the Reminders list for that vehicle.
5. Screenshot showing all three reminders with their colored status badges.

---

### ev-add-bill.png

**What to show:** The "Add Electricity Bill" form.

1. Create a vehicle with fuel type **EV**.
2. Go to the **EV** tab, tap **+**.
3. Fill in:
   - Start Date: 1st of current month.
   - End Date: last day of current month.
   - Amount: `320`
4. Screenshot the form.

---

### ev-tab.png

**What to show:** The EV tab with an in-progress billing period.

1. Create an EV vehicle.
2. Add an electricity bill with an end date in the future (so it is "in progress").
3. Go to the **EV** tab.
4. Screenshot showing the in-progress period card at top and the Snapshots link below.

---

### data-snapshot.png

**What to show:** The top of the Data tab with the vehicle snapshot card.

1. Use a vehicle with at least 2 fill-ups (so the trend arrows can compare against a previous value).
2. Go to the **Data** tab.
3. Screenshot showing, in order: the vehicle picker at the top, the snapshot card with three rows (**Average consumption**, **Last consumption**, **Last price** — each with a trend arrow icon on the left and the value on the right), and the **Stats / Charts / Map - Fill-ups** list below.

---

### data-snapshot-hybrid.png

**What to show:** Two snapshot cards stacked (Fuel + EV) for a plug-in hybrid.

1. Create a vehicle with primary fuel type **Diesel** (or PB95) and configure a **second tank** with fuel type **EV**.
2. Add a couple of fill-ups to the fuel tank and one or two electricity bills for the EV component.
3. Go to the **Data** tab.
4. Screenshot showing two snapshot cards stacked vertically: one under a **Fuel** header (with fuel metrics) and one under an **EV** header (with kWh/100km and per-kWh price).

---

### data-stats.png

**What to show:** The Stats detail page with the three period sections.

1. Use a vehicle with 5+ fill-ups spread across the last several months and at least one fill-up older than 30 days.
2. Go to the **Data** tab, tap **Stats**.
3. Screenshot showing the three sections — **Last Month**, **Last Year**, **All Time** — each with rows for Total Spent, Total Fuel, Fill-Ups, and Avg Efficiency.

---

### data-charts.png

**What to show:** The Charts detail page with a chart, the chart-type selector, the period selector, and the summary.

1. Same vehicle as above (5+ fill-ups across several months).
2. Go to the **Data** tab, tap **Charts**.
3. Make sure the chart-type selector shows the four options (**Mileage / Efficiency / Fuel Price / Cost/km**); the default selection is fine.
4. Make sure the period selector shows all six options (**All / YTD / Prev Y / This M / Prev M / Custom**) and pick one that contains data (e.g. **All** or **YTD**).
5. Screenshot showing the line chart at top, the chart-type selector and the period selector below it, and the summary section (Total Spent / Total Fuel / Fill-Ups / Avg Efficiency) at the bottom.

---

### data-map.png

**What to show:** The Map - Fill-ups full-screen map with several pins.

1. Grant **"While Using"** location permission for Drivest (see [fuel-tracking-location.png](#fuel-tracking-locationpng)).
2. Add at least 4–5 fill-ups, each from a different simulator location:
   - In the Simulator: **Features > Location > Custom Location...** — set a coordinate (e.g. Warsaw `52.2297, 21.0122`), save the fill-up, then change the simulator location and add the next one.
   - Use a small spread of nearby cities so all pins fit a regional zoom.
3. Go to the **Data** tab, tap **Map - Fill-ups**.
4. Screenshot the full-screen map with the round accent-coloured pins visible.

> Tip: If you don't have time to vary the simulator location between fill-ups, you can also set each fill-up's location manually from its detail page after saving — the same map view will populate.

---

### data-map-cluster.png

**What to show:** The Map - Fill-ups screen with at least one cluster badge visible (a count circle that represents several overlapping pins).

1. Same setup as `data-map.png` — make sure there are fill-ups at several different coordinates, including two or three that sit close to each other (e.g. three fill-ups within the same neighbourhood and two more in nearby cities).
2. Open **Data > Map - Fill-ups**.
3. Pinch out (zoom out) until the close-together fill-ups merge into a cluster badge showing the count (e.g. "3"). Keep enough single pins visible so the difference between a pin and a cluster badge is obvious.
4. Screenshot.

> Tip: If clustering doesn't kick in, zoom out further or move two fill-up coordinates closer together.

---

### data-map-detail.png

**What to show:** The Map - Fill-ups screen with the read-only detail sheet expanded after tapping a single pin.

1. Same setup as `data-map.png`. Use a fill-up that has all the interesting fields set: date, fuel type, odometer, volume, price per litre, total cost.
2. Open **Data > Map - Fill-ups**.
3. Tap a single pin (not a cluster). The detail sheet slides up from the bottom.
4. Screenshot with the sheet expanded and the map still partially visible above it.

---

### ev-snapshot-history.png

**What to show:** The EV period detail screen with the snapshot history list, including the three badge styles (Scheduled / Manual / Failed).

1. Create or use an EV vehicle (Make: Volvo or Toyota, valid VIN, refresh token stored in Keychain — see `connected-services-odometer-fetch.png` for the dummy-token setup).
2. Add at least one electricity bill so there's a period to drill into.
3. Trigger a mix of snapshots so the history has all three badge styles:
   - **Manual** — open a fill-up and tap the odometer fetch button.
   - **Scheduled** — run the Drivest **Fetch Odometer** Shortcuts action.
   - **Failed** — either let one of the calls above fail naturally (with a dummy token it will), or briefly disconnect the Mac's internet before triggering a fetch. For the most informative subtitle, stage the "Keychain locked — device must be unlocked at least once after boot" variant: reboot the device, leave it locked, fire a scheduled Shortcuts fetch, then unlock and screenshot.
4. Open the **EV** tab, tap the in-progress period card, scroll to the **Snapshot History** list.
5. Screenshot the list showing rows with their odometer + state-of-charge values and a visible mix of badges. The failed row's subtitle should be readable.

---

### currency-settings.png

**What to show:** The Currency settings with default and additional currencies.

1. Go to **Settings > Currency**.
2. Set default currency to **PLN**.
3. Add **EUR** and **USD** as additional currencies.
4. Tap **Refresh Rates Now** to load NBP rates (requires internet on the Mac running the Simulator).
5. Screenshot the screen showing: default currency at top, additional currencies with rates and last-updated dates, Add Currency and Refresh buttons.

---

### connected-services-integrations.png

**What to show:** The Integrations settings screen.

1. Go to **Settings > Integrations**.
2. Screenshot the screen showing supported manufacturer names and the "Set auto fetch in Shortcuts" link.

> Note: To show a green checkmark (connected state) for a manufacturer, you would need valid credentials. For documentation purposes, screenshot without a connected state is fine — or fake it by storing a dummy token in the Keychain through a debug build.

---

### connected-services-odometer-fetch.png

**What to show:** The odometer field with the fetch button visible.

1. Create a vehicle with Make: `Volvo`, and a VIN (e.g. `YV1XZ72VCL1234567`).
2. Store a dummy Volvo refresh token in the Keychain. This can be done via a debug build or by temporarily adding a line in `DrivestApp.swift` `onAppear`:
   ```swift
   KeychainService.save("dummy", for: KeychainService.volvoRefreshToken)
   ```
3. Go to the **Fuel** tab, tap **+** to add a fill-up.
4. The circular download button (arrow.down.circle) should appear next to the odometer field.
5. Screenshot the odometer row with the fetch button visible.
6. **Remove the debug line after capturing.**

---

### connected-services-snapshot-history.png

**What to show:** The Snapshot History list with a mix of Scheduled / Manual / Failed badges.

1. Use the same vehicle as for `connected-services-odometer-fetch.png` (Make: Volvo, VIN set, dummy token stored — see that section).
2. Trigger a few snapshots so the history has at least three rows:
   - One **Manual** snapshot — open a fill-up and tap the odometer fetch button. (With the dummy token, the call will fail and the row will be inserted as **Failed**; that's fine — the badge style is still what we want to show.)
   - One **Scheduled** snapshot — run the Drivest **Fetch Odometer** Shortcuts action via the Shortcuts app (the Shortcut needs to be created once; see the [Apple Shortcuts Integration](../../content/docs/connected-services.md#apple-shortcuts-integration) section in the docs). The resulting row gets a grey **Scheduled** badge.
   - One **Failed** row will already be present from the manual attempt above; otherwise force one by temporarily disabling the Mac's internet before tapping the fetch button.
3. Open the vehicle detail screen and tap **Snapshots** (or the equivalent navigation row to **Snapshot History**).
4. Screenshot the list showing the rows with their badges and (for the failed row) the subtitle error message and the preserved previous odometer.

> Tip: The most illustrative failure subtitle is the *"Keychain locked — device must be unlocked at least once after boot"* variant. To stage it on a real device: lock the device, reboot it, leave it locked, and trigger a scheduled fetch (e.g. via a time-based Shortcuts automation). The next time you unlock and open the app, that failure row is visible at the top of the Snapshot History.

> Tip: If creating a real Scheduled row is awkward, you can also insert a snapshot directly into the SwiftData store via a debug build. For documentation purposes the key thing is that each badge style (grey "Scheduled", accent "Manual", red "Failed") appears in the screenshot.

---

### backup-export-import.png

**What to show:** The Data section of the vehicle detail screen.

1. Go to **Settings > Manage Vehicles** > tap your vehicle.
2. Scroll to the **Data** section at the bottom.
3. Screenshot showing the "Export Data" and "Import Data..." buttons.

---

### backup-import-confirmation.png

**What to show:** The import confirmation sheet.

1. First, export a vehicle's data (follow the export steps and save the `.drivestbackup` file).
2. Import the same file back: in the vehicle detail screen, tap **Import Data...** and select the exported file.
3. The import confirmation sheet appears, showing the vehicle name, fill-up and cost counts, and Merge/Replace/Create New options.
4. Screenshot the sheet.

> Tip: To make the file accessible in the Simulator, drag the `.drivestbackup` file onto the Simulator window — it will appear in the Files app. Then import from there.

---

### settings-main.png

**What to show:** The full Settings screen.

1. Tap the **gear icon** on any tab.
2. Screenshot the Settings screen showing all sections: Manage Vehicles, Vehicle Order, Manage (Currency, Categories, Integrations), Appearance, Language, About.

---

### settings-appearance.png

**What to show:** Close-up of the Appearance section.

1. Open Settings.
2. Scroll to the **Appearance** section.
3. Make sure **System** is selected in the segmented control.
4. Screenshot focusing on the System / Light / Dark segmented control.

---

## Special States

### Sync Failure Banner (EVSyncFailureBanner)

**What to show:** The orange warning banner at the top of the screen saying "Unable to sync".

The banner appears when `snapshotFailures_<vehicleUUID>` in UserDefaults is >= 3.

1. Create an EV vehicle with a Make (e.g. `Volvo`) and a VIN.
2. Find the vehicle's UUID. You can do this by adding a temporary `print(vehicle.id)` in the app, or by inspecting the SwiftData store.
3. Set the failure count via the terminal:
   ```bash
   xcrun simctl spawn booted defaults write pro.siemion.drivest "snapshotFailures_<VEHICLE-UUID>" -int 5
   ```
4. Return to the app (or bring it to foreground) — the orange banner should appear at the top: "Unable to sync [Make] — reconnect in Integrations".
5. Screenshot showing the banner overlaying the tab content.
6. To reset after capturing:
   ```bash
   xcrun simctl spawn booted defaults write pro.siemion.drivest "snapshotFailures_<VEHICLE-UUID>" -int 0
   ```

### Empty States

Each tab has an empty state view when there is no data. To capture:
1. Create a vehicle but don't add any fill-ups or costs.
2. Go to each tab — the empty state with an icon and message appears.
3. Screenshot as needed.

The **Map - Fill-ups** empty state (no fill-ups with GPS data yet) is worth capturing for the Data page too — it shows a hint about enabling location permission.

### Dark Mode

To switch the Simulator to dark mode:
- In the Simulator: Features > Toggle Appearance (or **Cmd + Shift + A**).
- Or in the app: Settings > Appearance > Dark.

Capture dark mode variants of key screenshots by toggling appearance and re-taking the same screenshot.

### Multiple Languages

To capture the Polish version:
- In Xcode: Product > Scheme > Edit Scheme > Run > Options > App Language > Polish.
- Rebuild and re-run in the Simulator.

### Custom Simulator Location

Several screenshots (the location prompt, the fill-up detail map preview, the Map - Fill-ups screen) benefit from a non-default simulator location:

- In the Simulator menu: **Features > Location > Custom Location...** and enter latitude/longitude.
- For the Map screen, change this between fill-ups so the pins spread out across a recognisable area.
- Reset with **Features > Location > None** when finished.

---

## Tips

- **Consistent data:** Use the same vehicle name and data across related screenshots for a cohesive look.
- **Realistic values:** Use plausible fuel prices (e.g. 6.49 PLN/L for diesel), volumes (35–50 L), and odometer readings.
- **Clean status bar:** The Simulator shows a clean status bar (9:41, full battery, full signal) by default.
- **Hide keyboard:** Tap away from text fields before taking screenshots to hide the keyboard, unless the keyboard is relevant.
- **File naming:** Save screenshots with the exact filenames listed in `SCREENSHOTS.md` and place them in this directory (`static/images/docs/1.1/`).
