---
title: "Settings"
weight: 100
description: "Appearance, language, categories, vehicle order, and welcome hints"
---

Access Settings by tapping the **gear icon** in the top-right corner of any tab.

<!-- SCREENSHOT: Settings screen — the main Settings screen showing all sections: Manage Vehicles, Vehicle Order (with sort picker), Manage section (Currency, Categories, Integrations), Appearance (theme picker with System/Light/Dark), Language, Help, and About. -->
![Settings](/images/docs/1.2/settings-main.png)

## Manage Vehicles

View, edit, and delete your vehicles. Tap a vehicle to see its details, edit its information, or export/import data.

## Vehicle Order

Choose how vehicles are sorted in the vehicle picker:

- **Last Used** — most recently used vehicle appears first.
- **Name** — alphabetical order.
- **Created** — newest first.
- **Custom** — drag to arrange vehicles in your preferred order.

When **Custom** is selected, tap **Edit Order** to rearrange.

## Currency

Configure your default currency and additional currencies. See [Currency](../currency/) for details.

## Categories

Manage the expense categories used in cost tracking. See [Cost Tracking](../cost-tracking/#categories) for details.

## Integrations

Connect to supported vehicle manufacturers and Apple Shortcuts. See [Connected Services](../connected-services/) for details.

## Appearance

Choose between three theme options:

- **System** — follows your device's Light/Dark Mode setting.
- **Light** — always light.
- **Dark** — always dark.

<!-- SCREENSHOT: Appearance picker — close-up of the Appearance section in Settings showing the segmented control with System / Light / Dark options, with "System" selected. -->
![Appearance](/images/docs/1.2/settings-appearance.png)

<!-- SCREENSHOT: Dark theme — the app rendered in Dark mode, showing the main screen with the dark colour palette applied across the vehicle picker, fill-up list, and tab bar. -->
![Dark theme](/images/docs/1.2/dark.png)

## Language

Drivest supports **English** and **Polski** (Polish). The app language follows your device language by default. To change it:

1. Open **Settings**.
2. Under **Language**, tap the picker and choose **English** or **Polski**.
3. An inline ✅ acknowledgment appears under the picker: *"Language saved. Restart the app to apply it."*
4. Tap the red **Restart now** button to relaunch immediately, or close Settings and restart the app yourself when convenient.

The "Restart pending" indicator persists across closing/reopening Settings *and* across foreground/background cycles until you actually restart and the new language is applied — so even if you tap **Done** without restarting, the next time you open Settings the reminder is still there.

<!-- SCREENSHOT: Language picker with restart — the Language section of Settings showing the picker set to "Polski", the inline green checkmark with the "Language saved. Restart the app to apply it." copy underneath, and the red "Restart now" button below that. -->
![Language restart](/images/docs/1.2/settings-language-restart.png)

## Help

### Show welcome hints again

The welcome coachmarks (Settings gear, Currency row, EV ➕ button, Latest Reading card, Location row gestures) self-dismiss the first time you perform the gesture they describe. To bring them back:

1. **Settings → Help → Show welcome hints again.**
2. An inline ✅ "Hints will reappear after you restart the app." plus a red **Restart now** button.
3. Tap **Restart now** (or quit the app yourself).

On the next launch, Drivest wipes the tip state datastore *before* TipKit configures itself, so every coachmark is fresh again.

> Why the restart? `Tips.resetDatastore()` only takes effect when called *before* `Tips.configure()`. Drivest sets a UserDefault flag on tap and honours it on the next launch.

<!-- SCREENSHOT: Show welcome hints again — the Help → Show welcome hints again row tapped, with the inline green checkmark acknowledgement and the red "Restart now" button visible. -->
![Show hints again](/images/docs/1.2/settings-show-hints.png)

## About

View the app version, developer information, and links to:

- The Drivest website
- GitHub repository
- Privacy Policy
- MIT License
