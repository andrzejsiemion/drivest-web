---
title: "Connected Services"
weight: 80
description: "Vehicle manufacturer integrations and Apple Shortcuts"
---

Drivest can connect to supported vehicle manufacturers to automatically fetch odometer readings.

## How It Works

Some vehicle brands offer official APIs that allow Drivest to read your odometer remotely. The list of supported manufacturers is shown in **Settings > Integrations**.

### Setup

1. Go to **Settings > Integrations**.
2. Select your vehicle's manufacturer.
3. Sign in with your manufacturer account credentials.
4. The app authenticates directly with the manufacturer — your password is never stored by Drivest.
5. An authentication token is stored securely in your device's Keychain.

### What It Does

- **Odometer fetch** — when adding a fill-up, tap the download button next to the odometer field to pull the latest reading from your vehicle.

### Requirements

- Your vehicle's **Make** must match a supported manufacturer.
- A valid **VIN** must be entered in the vehicle settings.
- You need an account with the manufacturer, with the vehicle linked.

### Disconnecting

Go to **Settings > Integrations**, select the manufacturer, and sign out. This removes the stored token from your Keychain.

<!-- SCREENSHOT: Integrations screen — the Integrations settings screen showing supported manufacturers (with a green checkmark for connected ones) and "Set auto fetch in Shortcuts" link with an external link icon. -->
![Integrations](/images/docs/1.0/connected-services-integrations.png)

## Apple Shortcuts Integration

Drivest provides a **Fetch Odometer** action for Apple Shortcuts. This lets you automate data collection — for example, you can create a Shortcut that fetches your vehicle's odometer on a schedule.

To set up:
1. Go to **Settings > Integrations**.
2. Tap **Set auto fetch in Shortcuts** to open the Shortcuts app.
3. Create a new Shortcut using the **Fetch Odometer** action provided by Drivest.

This is useful for keeping your odometer readings up to date without manually opening the app.

<!-- SCREENSHOT: Odometer fetch button — the fill-up form odometer field with the circular download button visible next to the odometer value, indicating that connected service fetch is available. -->
![Odometer fetch](/images/docs/1.0/connected-services-odometer-fetch.png)

## Privacy

All communication with manufacturer APIs happens directly between your device and their servers. The developer of Drivest never sees your credentials or vehicle data. See the [Privacy Policy](/privacy/) for full details.
