---
title: "Fuel Tracking"
weight: 20
description: "Logging fill-ups, receipt scanning, and fuel efficiency"
---

## Adding a Fill-Up

1. Go to the **Fuel** tab.
2. Tap the **+** button.
3. Fill in the details:
   - **Vehicle** (when you have multiple vehicles) — pick the car you're refuelling.
   - **Odometer** — your current odometer reading. If you have a connected service integration set up, tap the download button next to the field to fetch the reading automatically.
   - **Location** — the row at the bottom of the Vehicle section. See [Location Capture](#location-capture) below.
   - **Fuel Type** — select the fuel type if different from your vehicle's default.
   - **Price per Unit** — the unit price of fuel.
   - **Volume** — how much fuel you added.
   - **Total Cost** — the total amount paid.
   - **Discount** — any discount applied.
   - **Full Tank** — toggle on if you filled the tank completely. This is needed for accurate fuel efficiency calculations.
   - **Date** — defaults to now, but you can change it.
   - **Note** — optional text note (up to 200 characters).
   - **Photos** — attach photos of receipts or the pump display.
4. Tap **Save**.

<!-- SCREENSHOT: Add fill-up form — the "Add Fill-Up" screen with vehicle picker at top, odometer with the connected-service download button, the Location row showing a place name and the per-entry icons, and price / volume / total fields filled with sample values. The "Full Tank" toggle should be visible and turned on. -->
![Add fill-up](/images/docs/1.2/fuel-tracking-add-fillup.png)

### Smart Field Calculation

When entering fuel data, the app automatically calculates the third value if you provide two of the three fields (price per unit, volume, total cost). For example, if you enter the price per unit and the volume, the total cost is calculated automatically.

## Location Capture

Drivest can attach GPS coordinates to each fill-up so you can see your fuel stops on a map (see [Data → Map](../data/#map)). When you open the Add Fill-Up form, the app silently asks for your current location and stores it on the fill-up if it's accurate enough.

- **Default is on, automatic capture** — no taps needed in the happy path.
- **Place name display** — once captured, the row shows the locality (e.g. `Warsaw, PL`) instead of raw coordinates. The full-precision coordinate is still what's persisted.
- **While the row is loading or geocoding fails** — a ✓ **Captured** badge is shown so you still know the fix was recorded.

### Adjusting the Location

The **Location** row in the Vehicle section gives you three controls:

- **Leading icon** (📍) — tap to toggle capture **on/off** for this entry. When off, the row collapses to "Location · Off" and no GPS is persisted. Useful for entries where the place is irrelevant (e.g. refilling a jerry can at home).
- **Trailing pin icon** — tap to force a fresh GPS read (clears any manual override).
- **Long-press the row** — opens a map and lets you drop a pin at a different spot (manual override).

The first time you save a fill-up, iOS will ask for **"While Using"** location permission. Granting it enables the auto-capture; denying it means no fill-up will carry GPS data until you grant permission later in **Settings > Drivest > Location**.

<!-- SCREENSHOT: Location row controls — close-up of the Location row showing the leading toggle icon (capture on), the displayed place name (e.g. "Warsaw, PL"), and the trailing pin/refresh icon. A second variant of the same row showing "Location · Off" with a slashed icon is also useful. -->
![Location row](/images/docs/1.2/fuel-tracking-location-row.png)

<!-- SCREENSHOT: Map picker — the long-press map picker sheet with a draggable pin centred on a sample street and a "Use this location" button at the bottom. -->
![Location map picker](/images/docs/1.2/fuel-tracking-location-picker.png)

### Edit Fill-Up

Open a saved fill-up and tap **Edit**. The Location row appears here too — long-press it to adjust the pin via the map picker. The Location row only appears in Edit if the fill-up already carries coordinates; legacy or imported entries with no GPS keep that state.

## Receipt Scanning

Tap the **Scan Receipt** button at the top of the Fuel section to use your camera to scan a fuel receipt. The app uses on-device OCR to extract the price, volume, and total cost from the receipt. All processing happens locally on your device.

The scanned values are filled into the form automatically. You can review and adjust them before saving.

<!-- SCREENSHOT: Take photo option — the fill-up form with the "Scan Receipt" button at the top of the fuel section, showing the entry point for capturing a receipt with the camera. -->
![Scan Receipt — take photo](/images/docs/1.2/fuel-tracking-receipt-scan-a.png)

<!-- SCREENSHOT: OCR result — the fill-up form after a receipt has been scanned, with price per unit, volume, and total cost auto-filled from the OCR pass. -->
![Scan Receipt — OCR result](/images/docs/1.2/fuel-tracking-receipt-scan-b.png)

## Fuel Efficiency

The app calculates fuel efficiency automatically when you have at least two consecutive full-tank fill-ups. The efficiency is displayed as a badge next to each fill-up in the list.

The efficiency format depends on your vehicle settings:

- **L/100km** — liters per 100 kilometers (lower is better).
- **km/L** — kilometers per liter (higher is better).
- **MPG (US)** — miles per US gallon.
- **MPG (UK)** — miles per imperial gallon.

For a period-wide breakdown including charts and a Per fill-up / Daily granularity toggle, see [Data → Efficiency](../data/#efficiency).

<!-- SCREENSHOT: Fill-up list with efficiency — the Fuel tab list showing several fill-ups, each with date, volume, cost, and an efficiency badge (e.g. "7.2 L/100km") displayed on the right side. -->
![Fuel efficiency badges](/images/docs/1.2/fuel-tracking-efficiency.png)

## Multi-Currency Support

If you have multiple currencies configured (see [Currency](../currency/)), a currency selector appears next to the price and total cost fields. Select the currency you paid in, and the app will store the exchange rate for statistics.

<!-- SCREENSHOT: Currency selector — the fill-up form with the currency badge (e.g. "EUR") visible next to the price field, showing that a non-default currency is selected. -->
![Currency selector](/images/docs/1.2/fuel-tracking-currency.png)

## Editing and Deleting

- Tap any fill-up in the list to view its details.
- Tap **Edit** to modify a fill-up.
- Swipe left on a fill-up in the list to delete it.
