---
title: General ledger account balances
description: Learn about two ways to view general ledger account balances - the Trial balance list page and financial reports, including an outline on trail balance snapshots.
author: JodiChristiansen
ms.author: aolson
ms.topic: article
ms.date: 4/22/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: LedgerTrialBalanceListPage
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: ea3650ac-34a0-4516-b75b-801c2164107d
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


## Trial balance snapshots
In Microsoft Dynamics 365 Finance version 10.0.39, *trial balance snapshots* are added to the **Trial balance** list page. A trial balance snapshot calculates the balances of the selected financial dimensions. These balances can be exported to Excel by using an Open Data Protocol (OData) entity. Each trial balance snapshot has an external tracking ID that can be used to make the snapshot available to external systems for reporting purposes.

### Process a trial balance snapshot

To process a trial balance snapshot, follow these steps.

1. On the **Trial balance** list page, on the Action Pane, select **Trial balance snapshots**.
2. On the Action Pane, select **Add trial balance snapshot**.
3. In the **Add trial balance snapshot** dialog box, in the **Ledger** field, select the ledger (legal entity) for the snapshot.
4. In the **Financial dimension set** field, select the financial dimension set for the snapshot. In the **Posting layer** field, select the posting layer.
5. In the **Fiscal years to process** field, select one of the following values:

    - Selected fiscal year
    - Current fiscal year
    - Current and previous fiscal year
    - Current and two previous fiscal years

    If you select **Selected fiscal year**, the fiscal year is available for selection.

6. Select **OK** to create the snapshot entry.

To create a one-time snapshot, select **Run snapshot once** on the Action Pane. A **Process trial balance data for a given fiscal year by period** batch job is created in the batch queue.

To show the external tracking ID of any snapshot in the list, select **Show external tracking ID**. Because the external tracking ID stays the same every time that it's generated, it's an ID that external reporting systems can use.

To download the contents of the snapshot to Excel, select **Open in Excel** on the Action Pane. The LedgerTrialBalanceFiscalYearSnapshotDataEntity OData entity is used. This entity can be used to view the data in Excel or other reporting tools.

### Use process automation with trial balance snapshots

To create a trial balance snapshot on a regular schedule, follow these steps.

1. Go to **System administration** \> **Setup** \> **Process automations**.
2. On the Action Pane, select **Create new process automation**.
3. In **Schedule type** field, select **Trial balance snapshots update**.
4. Select the company (ledger), and then select **Create series**.
5. In the **Name** field, enter a name for the series. In the **Schedule time** field, specify a schedule time. Then update any other process automation settings as you require.
6. Select **Next**.
7. Set the **Financial dimension set**, **Posting layer**, and **Fiscal years to process** fields. These fields are the same as the fields that appear on the **Trial balance snapshot** page.
8. Select **Finish**.

This procedure creates a scheduled process automation that runs daily, weekly, or monthly. The calendar view shows the scheduled work in a simple view that includes the status.

After the process is completed, the **View results** button doesn't show the results of the trial balance snapshot.

To view the results, go to **General ledger** \> **Inquiries and reports** \> **Trial balance**, and select **Trial balance snapshots**. All defined snapshots are shown. Any snapshots that process automation created have a check mark in the **Process automation** column. You can view the results by selecting **Open in Excel**.


For more information, see [View financial reports](view-financial-reports.md).



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
