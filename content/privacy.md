---
title: "Privacy Policy"
date: 2026-05-02
description: "Drivest Privacy Policy — all data stays on your device."
type: "privacy"
---

## Overview

Drivest ("the app") is designed with privacy as a priority. All data you enter is stored locally on your device and is never transmitted to any server operated by the developer.

---

## Data We Collect

### Data you provide

The app stores the following data **locally on your device only**:

- Vehicle information (name, make, model, VIN, odometer readings)
- Fuel fill-up records (date, volume, price, odometer, location notes)
- Cost records (date, amount, category, notes)
- Electricity bill records
- Photos attached to fill-ups and cost records
- App preferences and settings

This data never leaves your device unless you explicitly export a backup file and share it yourself.

### Camera and Photo Library

The app requests access to your **camera** and **photo library** solely to let you attach photos to your records and scan receipts using on-device OCR. Photos are stored locally on your device and are never uploaded anywhere.

---

## Volvo Integration (Optional)

If you choose to connect a Volvo vehicle via the Volvo Cars API, the following applies:

- You authenticate directly with **Volvo Cars** using your Volvo ID credentials. The developer never sees or stores your Volvo ID password.
- An OAuth **refresh token** is stored securely in your device's **Keychain** to maintain the connection.
- The app communicates with the **Volvo Cars API** (`api.volvocars.com`) to fetch your vehicle's odometer and energy state. This communication is between your device and Volvo Cars directly.
- You can disconnect the integration at any time from the vehicle settings screen, which removes the stored token from your Keychain.

The Volvo Cars API is subject to [Volvo Cars' own Privacy Policy](https://www.volvocars.com/intl/v/legal/privacy).

---

## Data We Do Not Collect

- We do not collect analytics or usage data.
- We do not use advertising identifiers.
- We do not use crash reporting services.
- We do not share any data with third parties.
- We do not have access to your device or any data stored by the app.

---

## Data Storage and Security

All app data is stored using Apple's SwiftData framework in the app's private container on your device, protected by iOS's standard security model. Sensitive credentials (Volvo OAuth tokens) are stored in the iOS Keychain.

---

## Backup and Export

If you use the app's built-in export feature, a backup file (`.drivestbackup`) is created locally. You are solely responsible for where you share or store that file.

---

## Children's Privacy

The app is not directed at children under the age of 13 and does not knowingly collect any information from children.

---

## Changes to This Policy

If this policy changes in a meaningful way, the updated version will be published at `https://drivest.app/privacy` with a new "Last updated" date.

---

## Contact

If you have any questions about this privacy policy, contact:

**Andrzej Siemion**
[andrzej@siemion.pro](mailto:drivest@siemion.cc)
[https://drivest.app](https://drivest.app)
