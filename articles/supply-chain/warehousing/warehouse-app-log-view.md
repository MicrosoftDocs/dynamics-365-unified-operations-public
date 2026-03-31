---
title: View the app log on a mobile device
description: Learn how to use the Local log view page in the Warehouse Management mobile app. The page lets you access and manage logs related to app activity.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 09/15/2025
ms.custom:
  - bap-template
---

# View the app log on a mobile device

The Warehouse Management mobile app maintains a local log of app operations. Use the **Local log view** page to review activity, identify errors, and export logs for troubleshooting with the Microsoft support team.

## What the app log records

The app log captures events as they happen on the device, including:

- Sign-in attempts and authentication events
- Page navigation and workflow steps
- Connection events and network activity
- Errors and exceptions

Logs are stored locally on the device and can be exported as a file for sharing with support.

## Open the Local log view page

1. Open the Warehouse Management mobile app on the affected device.
1. Navigate to the **Diagnostics** page:
    - From the **Welcome** page: Select **Set up connection** (or select **Connect** and then **Set up connection**), then select **Diagnostics**.
    - From the **Main menu**: Select **Connection settings**, then **Set up connection**, then **Diagnostics**.
1. Select **Local log view**.

    :::image type="content" source="media/wma-local-log-view.png" alt-text="Screenshot of the Local log view page." lightbox="media/wma-local-log-view.png":::

## Find and filter log entries

- **Filter by time or type:** Select the filter button next to the **Search** field to narrow the log list by time range or issue type.
- **Search:** Enter text in the **Search** field to find specific log entries (for example, an error message or connection event).
- **View details:** Select a log entry to see its full details, including timestamp, type, and message.

## Export and share logs

You can export logs from the device in two ways:

- **Save to local file:** Select the **Save** button next to the **Search** field. The app saves all log entries as a text file to the device's local storage.
- **Share:** Use the device's share function to send the log file directly via email or other apps.

When contacting the Microsoft support team, export and attach the log file to your support request. This helps the team understand the sequence of events that led to the issue.
