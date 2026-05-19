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
![Integrations](/images/docs/1.1/connected-services-integrations.png)

## Apple Shortcuts Integration

Drivest provides a **Fetch Odometer** action for Apple Shortcuts. This lets you automate data collection — for example, you can create a Shortcut that fetches your vehicle's odometer on a schedule.

To set up:
1. Go to **Settings > Integrations**.
2. Tap **Set auto fetch in Shortcuts** to open the Shortcuts app.
3. Create a new Shortcut using the **Fetch Odometer** action provided by Drivest.

This is useful for keeping your odometer readings up to date without manually opening the app.

### Setting up a scheduled automation

To make the fetch run on its own, wrap the **Fetch Odometer** action in a Personal Automation:

![Automation](/images/docs/1.1/shortcuts-automation.png)

1. Open the **Shortcuts** app and switch to the **Automation** tab.
2. Tap **+** in the top right and choose **New Automation**.
3. Pick a trigger — common choices are:
   - **Time of Day** — for example, every day at 23:00, so a fresh reading is ready each morning.
   - **Arrive** / **Leave** — fetch when you arrive home or leave work.
   - **CarPlay** — fetch each time you disconnect from CarPlay (end of trip).
4. After choosing the trigger, tap **Next** and then **New Blank Automation**.
5. Tap **Add Action**, search for **Fetch Odometer**, and add it.
6. Tap the action to select the **Vehicle** you want to update. Repeat the action for each vehicle if you own more than one.
7. Turn **Run Immediately** on so the automation fires without a notification prompt, then tap **Done**.

![Shortcuts fetch](/images/docs/1.1/shortcuts-fetched-odometer-for-vehicle.png)

Typing **Drivest** into the action search filters the list down to the **Fetch Odometer** action immediately, so you don't have to scroll through the full action library. Once the action is configured, it displays a small confirmation subtitle such as *"Fetched odometer for 1 vehicle(s)"* — a quick way to verify that a vehicle is actually selected before you save. The finished automation then appears under **Personal** on the Automation tab, summarised by its trigger and action (for example *"At 23:50, daily — Fetch Odometer"*), and runs silently from there on.

Every successful run is recorded in the vehicle's **Snapshot History** with a **Scheduled** badge; see [Reliability](#reliability) below for what happens when a run fails.

<!-- SCREENSHOT: Odometer fetch button — the fill-up form odometer field with the circular download button visible next to the odometer value, indicating that connected service fetch is available. -->
![Odometer fetch](/images/docs/1.1/ev-snapshot-history.png)

### Reliability

Every Shortcuts trigger creates a row in the **Snapshot History** for the vehicle. The badge tells you how the fetch was triggered and whether it succeeded:

- **Scheduled** (grey) — a routine background or Shortcuts fetch that succeeded.
- **Manual** (accent) — a user-triggered fetch from inside the app.
- **Failed** (red) — the fetch reached Drivest but couldn't complete. The row's subtitle carries the underlying error message; common reasons include:
  - *Volvo / Toyota token not configured* — no integration is set up for this make.
  - *Keychain locked — device must be unlocked at least once after boot* — a background fetch fired while the device was still locked after a reboot. The next fetch after you unlock the device once will succeed.
  - Manufacturer-side errors such as HTTP 429 (rate limit) or 5xx (server error).

If the API is rate-limited, temporarily unavailable, or the network drops, Drivest:

1. Retries the call up to three times with a short back-off (1s, then 2s).
2. If retries don't recover, inserts a snapshot anyway with a red **Failed** badge and the underlying error message.

This means **no Shortcuts trigger is silently dropped** — every attempt leaves a visible record. Failed rows are kept indefinitely (or until the 2-year purge cutoff) so you can see attempts even when they didn't succeed.

<!-- SCREENSHOT: Snapshot History — the vehicle's Snapshot History list showing several rows with different badges: a grey "Scheduled" row with a fresh odometer value, an accent "Manual" row, and a red "Failed" row whose subtitle shows a "Keychain locked" or similar error message and where the previous odometer is carried over. -->
![Snapshot History](/images/docs/1.1/connected-services-snapshot-history.png)

## Privacy

All communication with manufacturer APIs happens directly between your device and their servers. The developer of Drivest never sees your credentials or vehicle data. See the [Privacy Policy](/privacy/) for full details.
