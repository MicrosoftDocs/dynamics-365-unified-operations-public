---
title: Install Business performance analytics
description: Learn how to install Business performance analytics, including a step-by-step installation process and an outline on accessing reports in Business performance analytics.
author: jinniew
ms.author: jiwo
ms.topic: conceptual
ms.date: 05/20/2024
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
---

# Current Challenges in Business Performance Analytics

## Order to Cash Data Model
Issue: The "Order to Cash" data model is not enabled by default for customers.
Workaround: Customers need to request enablement through Microsoft Support.
Status: This model will be automatically enabled for all customers by December 2024.

## Loss of Custom Reports on Uninstall
Issue: Custom reports will be lost if customers uninstall BPA.
Steps to Save Customizations:
In the event of an uninstall and reinstall of BPA, reports can be restored if the following conditions are met:
	• A backup has been performed, or the user has waited at least 24 hours for the automated backup.
	• The Business performance analytics Configuration solution (msdyn_BpaConfigs) has not been uninstalled.
	• No external issues are affecting the data lake.
	• The reinstallation occurs in the same environment (cross-environment restoration is not currently supported).
Steps for Reinstallation with a Restore:
	1. Before uninstalling, ensure a backup is performed (instructions below).
	2. Do not uninstall the Business performance analytics configs solution (msdyn_BpaConfigs) to prevent backup data loss.
	3. Reinstall BPA via the Power Platform Admin Center (PPAC) portal.
	4. Once the installation is complete, perform a restore (instructions below).
How to Perform a Backup:
	1. Navigate to the “Flows” tab in the Power Platform Maker portal.
	2. Run the "Business performance analytics backup reports flow" by clicking the play button.
	3. Click “Run flow” in the resulting panel.
How to Perform a Self-Service Restore:
	1. Run the "Business performance analytics restore reports flow."
	2. Choose to restore either all reports, only custom reports, or use a specific FRH Report ID.
	3. Click “Run flow” to begin the restoration process.
Status: We are investigating a feature that will allow customers to back up and restore their report customizations when Business performance analytics is uninstalled.

## Excel Drill-Down in Power Pivot
Issue: Excel drill down is not working when analyzing BPA data in Power Pivot.
Status: We are investigating this issue, and a fix will be rolled out soon.

## Limited Data Refreshes
Issue: Customers only receive two refreshes per day, at 12 AM and 12 PM (International Standard Time).
Status: We will remove this limit by December 2024.

## Data Lake Folder Size Increases
Issue: Customers may see the data lake folder size increase with each Business performance analytics refresh. This is due to stale folders only being cleaned every 30 days.
Status: We will clean up folders more frequently by December 2024.![image](https://github.com/user-attachments/assets/881c9783-b7cb-4b35-83b1-807072ff2272)
