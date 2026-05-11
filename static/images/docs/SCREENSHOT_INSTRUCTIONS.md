# How to Capture Documentation Screenshots

Step-by-step instructions for reproducing each screenshot using the iOS Simulator.

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
4. Screenshot with the vehicle picker card at top and the fill-up list below. The tab bar at bottom should show Fuel, Costs, Statistics.

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

### cost-tracking-categories.png

**What to show:** Categories management and the "New Category" sheet.

This requires two screenshots composited, or take them separately:

**Screenshot A — Category list:**
1. Go to **Settings > Categories**.
2. Screenshot the list of categories with their icons.

**Screenshot B — Add Category sheet:**
1. Tap **+** in the Categories screen.
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

### statistics-chart.png

**What to show:** The Statistics tab with a chart and summary data.

1. Use a vehicle with 5+ fill-ups spread over several months.
2. Go to the **Statistics** tab.
3. The chart should show data points. Select a meaningful period.
4. Screenshot the full tab — chart at top, summary section below.

---

### statistics-summary.png

**What to show:** Close-up of the spending summary section.

1. Same vehicle as above.
2. Go to **Statistics** tab.
3. Scroll so the summary rows (Total Spent, Total Fuel, Fill-Ups, Avg Efficiency) are fully visible.
4. Screenshot focusing on the summary section.

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

### Dark Mode

To switch the Simulator to dark mode:
- In the Simulator: Features > Toggle Appearance (or **Cmd + Shift + A**).
- Or in the app: Settings > Appearance > Dark.

Capture dark mode variants of key screenshots by toggling appearance and re-taking the same screenshot.

### Multiple Languages

To capture the Polish version:
- In Xcode: Product > Scheme > Edit Scheme > Run > Options > App Language > Polish.
- Rebuild and re-run in the Simulator.

---

## Tips

- **Consistent data:** Use the same vehicle name and data across related screenshots for a cohesive look.
- **Realistic values:** Use plausible fuel prices (e.g. 6.49 PLN/L for diesel), volumes (35–50 L), and odometer readings.
- **Clean status bar:** The Simulator shows a clean status bar (9:41, full battery, full signal) by default.
- **Hide keyboard:** Tap away from text fields before taking screenshots to hide the keyboard, unless the keyboard is relevant.
- **File naming:** Save screenshots with the exact filenames listed in `SCREENSHOTS.md` and place them in this directory (`static/images/docs/`).
