---
title: Business performance analytics troubleshooting
description: Learn about some current known issues in Business performance analytics.
author: lizmora
ms.author: jiwo
ms.topic: conceptual
ms.date: 10/30/2024
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
---

# Business performance analytics troubleshooting

[!include [banner](../includes/banner.md)]

This article describes some known issues in Business performance analytics.

### By default, the Order to cash data model isn't enabled for customers.

Customers must submit a request to Microsoft Support to have the *Order to cash* data model enabled. In the future, this model will automatically be enabled for all customers.

### Custom reports are lost when Business performance analytics is uninstalled.

If Business performance analytics was uninstalled and then reinstalled, reports can be restored if the following conditions are met:

- A manual backup was completed. Alternatively, 24 hours have passed, so that the automated backup was completed.
- The Business performance analytics configuration solution (msdyn\_BpaConfigs) is still installed.
- No external issues are affecting the data lake.
- The reinstallation occurs in the same environment. Cross-environment restoration isn't supported.

To reinstall Business performance analytics and restore reports, follow these steps.

1. Before you uninstall Business performance analytics, confirm that a backup was completed.
2. Make sure that you don't uninstall the Business performance analytics configuration solution (msdyn\_BpaConfigs).
3. Reinstall Business performance analytics through the Microsoft Power Platform admin center.
4. After the installation is completed, do a restore.

To back up a report, follow these steps.

1. In [Power Apps](https://make.powerapps.com/), on the left navigation pane, select **Flows**.
2. Select **Play** to run the **Business performance analytics backup reports** flow.
3. Select **Run flow** in the pane that appears.

To do a self-service restore, follow these steps.

1. Run the **Business performance analytics restore reports** flow.
2. Select whether you want to restore all reports, only custom reports, or only the report that has a specific Financial Reporting Hub (FRH) report ID.
3. Select **Run flow** to begin the restoration process.

### Excel drill-down doesn't work when I analyze Business performance analytics data in Power Pivot.

Microsoft is investigating this issue, and a fix will be available in the future.

### Customers receive only two refreshes per day, at 12:00 AM and 12:00 PM (Coordinated Universal Time).

This limit will be removed in the future.

### The size of the data lake folder increases at each Business performance analytics refresh.

Customers might notice that the size of the data lake folder increases each time that Business performance analytics refreshes its data. This issue occurs because stale folders are cleaned only every 30 days. In the future, stale folders will be cleaned more often.
