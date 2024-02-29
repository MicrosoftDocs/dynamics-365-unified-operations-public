---
# required metadata

title: General ledger account balances
description: This article explains two ways to view general ledger account balances -  the Trial balance list page and financial reports. 
author: aprilolson
ms.date: 02/29/2024
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerTrialBalanceListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: ea3650ac-34a0-4516-b75b-801c2164107d
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# General ledger account balances

[!include [banner](../includes/banner.md)]

This article explains two ways to view general ledger account balances -  the Trial balance list page and financial reports. It also discusses how to update dimension set balances.

There are a variety of ways users can view balances in the general ledger. Some of the most common options are:

-   Trial balance
-   Financial reports
-   Voucher transactions
-   Ledger reports

The most common ways are the trial balance list page and financial reports.

## Trial balance
The trial balance is a list page that shows all of the balances of an account and/or dimensions for a given period of time. When the trial balance is first opened it refreshes with the balances for the dates and properties that are set in the Parameters. Properties that can be changed in Parameters are the dates, posting layer, how they want opening balances to appear, and what closing transaction types to show. 

When a user changes the parameters the balances are refreshed. The user can also pick what dimension set they want to view balances for and whether each of the dimensions show in separate columns. 

Users can drill down on the balances to view the transactions that make up the balance.    

For more information, see [View financial reports](view-financial-reports.md).

## Trial balance snapshots
In Dynamics 365 Finance version 10.0.39, Trial balance snapshots are added to the **Trial balance** list page. The **Trial balance snapshot** calculates the balances of the selected Financial dimensions that can be exported to Excel using OData entity. Each snapshot is available for reporting purposes to external systems using the External tracking ID. 

### Process a Trial balance snapshot
To process a **Trial balance snapshot**, follow these steps:
1. Go to **Trial balance list page**, select **Trial balance snapshots** in the action pane.
2. Select **Add trial balance snapshot** in the action pane.
3. In the **Add trial balance snapshot** page, select the **Ledger**(legal entity) for the snapshot.
4. Select **Financial dimension set** for the snapshot and the **Posting layer**.
5. In the **Fiscal years to process**, the available options are:
 - **Selected fiscal year**
 - **Current fiscal year**
 - **Current and previous fiscal year**
 - **Current and two previous fiscal years**
The fiscal year is available when **Selected fiscal year** is set in **Fiscal years to process**.
6. Click **OK** to create the snapshot entry.  

To create a one time snapshot, select **Run snapshot once** in the action pane. This creates a **Process trial balance data for a given fiscal year by period** batch job in the batch queue.  

To display the external tracking ID in any snapshot in the list, select **Show external tracking ID**. Because this external ID stays the same each time it is generated, this is an ID that can be used by external reporting systems.  

Select **Open in Excel** in the action pane to download the contents of the snapshot to Excel using the LedgerTrialBalanceFiscalYearSnapshotDataEntity. This is an OData entity that can be used to view the data in Excel or other reporting tools.

### Process automation with Trial balance snapshots

To create a trial balance snapshot on a regular schedule, follow these steps:
1. Go to **System administration > Setup > Process automations**.
2. Select **Create new process automation** from the action pane.
3. In **Schedule type** field, select Trial balance snapshots update.
4. Select the company (ledger) and select **Create series**.
5. Enter a **Name**, and a **Schedule time**. Update any other process automation settings.
6. Select **Next**.
7. Select the **Financial dimension set**, **Posting layer** and the **Fiscal years to process** options. These are the same options as the **Trial balance snapshot** page.
8. Select **Finish**.
This creates the scheduled process automation that will run daily, weekly or monthly. The calendar view shows the scheduled work in a simple view including the status. After the process is complete, the **View results** button doesn't display the results of the Trial balance snapshot.  

To view results, go to **General ledger > Inquiries and reports > Trial balance**. Select **Trial balance snapshots**. Any snapshots created by process automation will have the checkmark in the **Process automation** column, but all defined snapshots are displayed. The results can be viewed by selecting **Open in Excel**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
