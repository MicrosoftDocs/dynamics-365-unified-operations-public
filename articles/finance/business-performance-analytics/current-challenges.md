---
title: Business performance analytics current challenges
description: This article describes some current challenges in Business performance analytics.
author: lizmora
ms.author: jiwo
ms.topic: conceptual
ms.date: 10/30/2024
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
---

# Current challenges in Business performance analytics

This article describs some currenct challenges in Business performance analytics

## The "Order to cash" data model isn't enabled by default for customers
Customers need to request enablement through Microsoft support. In the future, this model will be automatically enabled for all customers.

## Custom reports are lost when Business performance analytics is uninstalled
To save report customizations, follow these steps:
In the event of an uninstall and reinstall of Business performance analytics, reports can be restored if the following conditions are met:
 - A backup has been performed, or the user has waited at least 24 hours for the automated backup.
 - The Business performance analytics configuration solution (msdyn_BpaConfigs) hasn't been uninstalled.
 - No external issues are affecting the data lake.
 - The reinstallation occurs in the same environment (cross-environment restoration is not currently supported).

To reinstall Business performance analytics with a restore, follow these steps:
1. Before uninstalling, ensure a backup is performed (instructions below).
2. Don't uninstall the Business performance analytics configs solution (msdyn_BpaConfigs) to prevent backup data loss.
3. Reinstall Business performance analytics via the Power Platform Admin Center (PPAC) portal.
4. After the installation is complete, perform a restore.

To backup a report, follow these steps:
1. Go to the **Flows** tab in the Power Platform Maker portal.
2. Click **Play** to run the **Business performance analytics backup reports flow**.
3. Click **Run flow** in the resulting panel.


To perform a self-service restore, follow these steps:
1. Run the **Business performance analytics restore reports flow**.
2.  Choose to restore either all reports, only custom reports, or use a specific FRH Report ID.
3.  Click **Run flow** to begin the restoration process.


### Excel drill down isn't working when analyzing Business performance analytics data in Power Pivot
We are investigating this issue, and a fix will be rolled out soon.

### Customers receive two refreshes per day, at 12 AM and 12 PM (International Standard Time).
This limit will be removed in the future. 

### Customers may see the data lake folder size increase with each Business performance analytics refresh. This is due to stale folders only being cleaned every 30 days.
This is due to stale folders only being cleaned every 30 days. Stale folders will be cleaned more frequently by December 2024.

![image](https://github.com/user-attachments/assets/881c9783-b7cb-4b35-83b1-807072ff2272)
