---
title: "Fuel Tracking"
weight: 20
description: "Logging fill-ups, receipt scanning, and fuel efficiency"
---

## Adding a Fill-Up

1. Go to the **Fuel** tab.
2. Tap the **+** button.
3. Fill in the details:
   - **Odometer** — your current odometer reading. If you have a connected service integration set up, tap the download button next to the field to fetch the reading automatically.
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

<!-- SCREENSHOT: Add fill-up form — the "Add Fill-Up" screen with odometer, price per unit, volume, total cost fields filled with sample values. The "Full Tank" toggle should be visible and turned on. -->
![Add fill-up](/images/docs/fuel-tracking-add-fillup.png)

### Smart Field Calculation

When entering fuel data, the app automatically calculates the third value if you provide two of the three fields (price per unit, volume, total cost). For example, if you enter the price per unit and the volume, the total cost is calculated automatically.

## Receipt Scanning

Tap the **Scan Receipt** button at the top of the fuel section to use your camera to scan a fuel receipt. The app uses on-device OCR to extract the price, volume, and total cost from the receipt. All processing happens locally on your device.

The scanned values are filled into the form automatically. You can review and adjust them before saving.

<!-- SCREENSHOT: Receipt scanning — the camera view with a receipt being scanned, or the fill-up form after scanning with values auto-filled and the "Scan Receipt" button visible at the top. -->
![Receipt scanning](/images/docs/fuel-tracking-receipt-scan.png)

## Fuel Efficiency

The app calculates fuel efficiency automatically when you have at least two consecutive full-tank fill-ups. The efficiency is displayed as a badge next to each fill-up in the list.

The efficiency format depends on your vehicle settings:
- **L/100km** — liters per 100 kilometers (lower is better).
- **km/L** — kilometers per liter (higher is better).
- **MPG (US)** — miles per US gallon.
- **MPG (UK)** — miles per imperial gallon.

<!-- SCREENSHOT: Fill-up list with efficiency — the Fuel tab list showing several fill-ups, each with date, volume, cost, and an efficiency badge (e.g. "7.2 L/100km") displayed on the right side. -->
![Fuel efficiency badges](/images/docs/fuel-tracking-efficiency.png)

## Multi-Currency Support

If you have multiple currencies configured (see [Currency](../currency/)), a currency selector appears next to the price and total cost fields. Select the currency you paid in, and the app will store the exchange rate for statistics.

<!-- SCREENSHOT: Currency selector — the fill-up form with the currency badge (e.g. "EUR") visible next to the price field, showing that a non-default currency is selected. -->
![Currency selector](/images/docs/fuel-tracking-currency.png)

## Editing and Deleting

- Tap any fill-up in the list to view its details.
- Tap **Edit** to modify a fill-up.
- Swipe left on a fill-up in the list to delete it.
