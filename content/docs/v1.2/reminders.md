---
title: "Reminders"
weight: 40
description: "Date-based and distance-based reminders for vehicle maintenance"
---

Reminders help you keep track of upcoming vehicle expenses like insurance renewals, service appointments, or distance-based maintenance.

## Types of Reminders

### Date-Based Reminders

Triggered by a specific date. Useful for:

- Insurance renewal dates
- Annual inspections
- Registration renewals
- Scheduled service appointments

You can set:

- **Due Date** — when the reminder is due.
- **Remind days before** — how many days in advance you want to be notified (0–30 days).
- **Notification time** — the time of day to receive the notification.
- **Recurrence interval** — number of days to advance the due date when you mark the reminder as done (default: 365 days for annual reminders).

### Distance-Based Reminders

Triggered when your vehicle approaches a certain odometer reading. Useful for:

- Oil changes
- Tire rotations
- Brake inspections
- Any mileage-based maintenance

You can set:

- **Target odometer** — the odometer reading when the task is due.
- **Lead distance** — how far in advance (in km or miles) you want to be notified.
- **Recurrence interval** — distance to advance the target when you mark the reminder as done.

## Creating a Reminder

When adding a new cost, toggle **Create Reminder** at the bottom of the form. This is useful for recurring expenses — for example, when you pay for insurance, you can immediately set a reminder for next year's renewal. The cost form's Vehicle section (with odometer + location at the top) makes it easy to scaffold a distance-based reminder anchored to the current mileage.

<!-- SCREENSHOT: Reminder in cost form — the bottom section of the "Add Cost" form with "Create Reminder" toggled on, showing the type picker (Date/Distance segmented control), due date picker, and "Remind days before" stepper. -->
![Reminder in cost form](/images/docs/1.2/reminders-cost-form.png)

## Reminder Statuses

Each reminder shows a colored status badge:

- **Overdue** (red) — the due date has passed or the target odometer has been exceeded.
- **Due Soon** (orange) — within the lead time or lead distance window.
- **Pending** (gray) — not yet approaching the due date or distance.
- **Silenced** (gray) — manually silenced by the user.

<!-- SCREENSHOT: Reminder list — the reminders list showing several reminders with different status badges: one red "Overdue", one orange "Due Soon", and one gray "Pending", each with title, category icon, and due date or distance. -->
![Reminder statuses](/images/docs/1.2/reminders-list.png)

## Managing Reminders

- **Mark as Done** — advances the reminder by its recurrence interval (e.g. moves the due date forward by 365 days).
- **Silence** — temporarily mutes notifications for a reminder without deleting it.
- **Edit** — modify any reminder detail.
- **Delete** — permanently remove the reminder.

## Notifications

Reminders send local notifications at the configured time. The app will ask for notification permission when you create your first reminder. Notifications are delivered even when the app is not open.

For distance-based reminders, notifications are checked and sent when the app detects a new odometer reading — from a manual fill-up, a charging session, a cost entry with odometer, or a connected service sync.
