---
title: Business performance analytics troubleshooting
description: Learn about some current known issues in Business performance analytics.
author: lizmora
ms.author: jiwo
ms.topic: troubleshooting-general
ms.date: 08/27/2026
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
---

# Business performance analytics troubleshooting

[!include [banner](../includes/banner.md)]

This article describes some known issues in Business performance analytics.

## Diagnostics page

The Business performance analytics admin has access to a diagnostics page that acts as a self-help tool to monitor their Business performance analytics data and app health. This page includes a message center where the admin receives proactive notifications when action is required to correct an error in their environment.

### View notifications from the diagnostics page

To view messages from the **Diagnostics** page, follow these steps:

1. Go to bell icon on the top right of the application.
1. Messages are displayed with a link to the diagnostics page.

### Access the Diagnostics page

You can access the diagnostic page from the **Administration** section of the app.

### View system status

The status section helps the admin troubleshoot if anything is misconfigured in their app. For example:

- The status of their background flows
- Are the app users set up correctly
- Do the app admins have access to the required roles and settings

### View and complete messages

To view and complete messages, follow these steps:

1. On the **Diagnostics** page, select the **Messages active** tab to see active messages.
1. Expand the messages to view details. These messages require admin attention to fix any errors detected in the app.
1. After you perform the action, mark the message as **Complete**. This step confirms to telemetry that the action is complete.
1. Find all completed messages on the **Completed** tab.

## Troubleshooting and maintenance reminders

### By default, the Order to cash data model isn't enabled for customers

Customers must submit a request to Microsoft Support to enable the *Order to cash* data model. In the future, Microsoft automatically enables this data model for all customers.

### Custom reports are lost when you uninstall Business performance analytics

If you uninstall and then reinstall Business performance analytics, you can restore reports if the following conditions are true:

- You manually back up the reports, or 24 hours pass to trigger an automated backup.
- The Business performance analytics configuration solution (msdyn\_BpaConfigs) is still installed.
- No external issues affect the data lake.
- You reinstall in the same environment. Cross-environment restoration isn't supported.

To reinstall Business performance analytics and restore reports, follow these steps:

1. Before you uninstall Business performance analytics, confirm that a backup is completed.
1. Ensure that you don't uninstall the Business performance analytics configuration solution (msdyn\_BpaConfigs).
1. Reinstall Business performance analytics through the Microsoft Power Platform admin center.
1. After the installation is completed, do a restore.

To back up a report, follow these steps:

1. In [Power Apps](https://make.powerapps.com/), on the left navigation pane, select **Flows**.
1. Select **Play** to run the **Business performance analytics backup reports** flow.
1. Select **Run flow** in the pane that appears.

To do a self-service restore, follow these steps:

1. Run the **Business performance analytics restore reports** flow.
1. Select whether you want to restore all reports, only custom reports, or only the report that has a specific Financial Reporting Hub (FRH) report ID.
1. Select **Run flow** to begin the restoration process.

### Excel drill-down doesn't work when I analyze Business performance analytics data in Power Pivot

Microsoft is investigating this issue, and a fix will be available in the future.

### Customers receive only two refreshes per day, at 12:00 AM and 12:00 PM (Coordinated Universal Time)

This limit will be removed in the future.

### The size of the data lake folder increases every time Business performance analytics is refreshed

Customers might notice that the size of the data lake folder increases each time that Business performance analytics refreshes its data. This issue occurs because stale folders are cleaned only every 30 days. In the future, stale folders are cleaned more often.

### Administration controls aren't visible for a user in another language

If a user with the Business performance analytics administrator role signs into the **Reporting hub** and can't see the **Administration** controls, this condition can occur when the user's UI language isn't English (currently the only language that Business performance analytics supports). The Microsoft Dataverse sitemap that Business performance analytics uses isn't yet localized for other languages, so some controls don't appear.

As a temporary workaround, switch to English (United States) in the following three places:

1. **Environment language pack**: If English isn't already enabled for the environment, an administrator must add it before any user can select it. For more information, see [Enable languages in the Power Platform admin center](/power-platform/admin/enable-languages).
1. **Personal Dataverse language**: After English is enabled for the environment, update your personal language preference. For more information, see [Set personal options: Languages tab](/power-apps/user/set-personal-options#languages-tab-options).
1. **Browser language**: Set English (United States) as the top preferred language in your browser, since the browser's preferred language also affects how Business performance analytics renders.

This is a temporary workaround until Business performance analytics is localized for additional languages.
