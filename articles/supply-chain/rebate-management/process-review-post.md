---
# required metadata

title: Process, review, and post rebates
description: This topic describes how to process your Rebate management deals, calculate their discounts, review the transactions that are generated, post transactions, and review the postings.
author: sherry-zheng
ms.date: 02/19/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: TAMRebateDeal
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: chuzheng
ms.search.validFrom: 2021-02-19
ms.dyn365.ops.version: Release 10.0.18
---

# Process, review, and post rebates

[!include [banner](../includes/banner.md)]

This topic describes how to process your Rebate management deals, calculate their discounts, review the transactions that are generated, post transactions, and review the postings.

## Change the status of a deal

You can assign a status to each deal to help track it. The status is for informational purposes only.

1. Select a deal (for example, on the [**All rebate management deals** page](rebate-management-deals.md)).
1. On the Action Pane, on the **Rebate management deals** tab, in the **Maintain** group, select **Change status**.
1. In the **Change status** dialog box, set the **Rebate status** field to a new status.
1. Select **OK**.

## Calculate FIFO purchase prices

The **Calculate FIFO purchase price** periodic task must be run to calculate the rebates for [deals](rebate-management-deals.md) where the **Price basis** field is set to *FIFO*. The system will use a first in, first out (FIFO) rule to calculate the value of the stock that was sold. This value will then be used to calculate the vendor rebates.

Go to **Rebates management \> Periodic tasks \> Calculate FIFO purchase price**. In the dialog box that appears, select **OK** to run the calculation.

## Process Rebate management deals

When you process a deal, the system calculates all relevant rebates and royalties that are set up. Only selected deals that have calculation periods that are ready to be calculated and that have a status of *Active* will be processed. After processing is completed, the system generates a set of transactions that you can review and then post.

> [!NOTE]
> In all cases, rebates are processed at the level that is specified by each deal's **Reconcile by** setting (*Deal* or *Line*). You can do single-line calculations only for deals where the **Reconcile by** field is set to *Line*.

### Process all lines for one or more deals

1. Open the appropriate [rebate deals list page](rebate-management-deals.md) for the type of deal that you want to work with.
1. Select the row for each deal that you want to process (or open the deal that you want to process).
1. On the Action Pane, on the **Rebate management deals** tab, in the **Generate** group, select one of the following commands:

    - **Process \> Provision** – Provision a set of accruals for each relevant rebate deal, but don't post them.
    - **Process \> Rebate management** – Process a series of transactions that provide the value of the rebate for each deal.
    - **Process \> Write off** – Reverse previously posted transactions to write them off so that new rebate deal transactions can be calculated.

1. In the dialog box that appears, set the **From date** and **To date** fields to define the date range for the calculation.
1. Select **OK** to run the calculation.

### Process one or more specific deal lines for a selected deal

1. Open the appropriate [rebate deals list page](rebate-management-deals.md) for the type of deal that you want to work with.
1. Open the deal that you want to process a line from.
1. Select the **Lines** tab in the upper-right corner.
1. On **Rebate management** FastTab, select the row for each deal line that you want to process.
1. On the toolbar of the **Rebate management** FastTab, select one of the following commands. (These commands are available only for deals where the **Reconcile by** field is set to *Line*.)

    - **Process \> Provision** – Provision a set of accruals for each relevant deal line, but don't post them.
    - **Process \> Rebate management** – Process a series of transactions that provide the value of the rebate for each deal line.
    - **Process \> Write off** – Reverse previously posted transactions to write them off so that new rebate deal transactions can be calculated.

1. In the dialog box that appears, set the **From date** and **To date** fields to define the date range for the calculation.
1. Select **OK** to run the calculation.

### Process deals using a batch job

Instead of processing specific deals or deal lines, you can run a batch job to process several deals at the same time. You can optionally apply record filters and/or set up a recurring schedule. To process deals by using a batch job, follow these steps.

1. Follow one of these steps:

    - Go to **Rebate management \> Periodic tasks \> Process \> Provision** to provision a set of accruals for each relevant deal, but without posting them.
    - Go to **Rebate management \> Periodic tasks \> Process \> Rebate management** to process a series of transactions that provide the value of the rebate for each deal.
    - Go to **Rebate management \> Periodic tasks \> Process \> Write off** to reverse previously posted transactions to write them off so that new rebate deal transactions can be calculated.

1. In the dialog box that appears, on the **Parameters** FastTab, in the **Period** section, set the **From date** and **To date** fields to define the date range for transactions for the calculation.
1. In the **Guarantee Period** section, set the **From date** and **To date** fields to define the date range for guarantees for the calculation.
1. On the **Records to include** FastTab, you can set up filters to limit the set of deals that the batch job will process. These settings work in the same way that they work for other types of batch jobs.
1. On the **Run in the background** FastTab, you can set up batch processing and scheduling options as required. These settings work in the same way that they work for other types of batch jobs.
1. Select **OK** to run and/or schedule the calculation.

## View and edit Rebate management transactions

When you process one or more deals, the system creates transactions that you can view and, perhaps, edit before you post them.

1. Follow one of these steps:

    - Select the deal to view transactions for (for example, on the [**All rebate management deals** page](rebate-management-deals.md)). On the Action Pane, on the **Rebate management deals** tab, in the **Transactions** group, select **Transactions** or **Guarantee transactions**, depending on the type of transaction that you want to view.
    - Open a deal (for example, on the [**All rebate management deals** page](rebate-management-deals.md)) to view its details. On the **Rebate management** FastTab, select the deal line to view transactions for. Then, on the toolbar, select **Transactions** or **Guarantee transactions**, depending on the type of transaction that you want to view. (These buttons are available only for deals where the **Reconcile by** field is set to *Line*.)

1. The **Rebate management date transactions** or **Rebate management guarantee transactions** page appears. It contains a grid, where each line represents a collection of transactions from a single rebate or guarantee period. Select a row in the grid, and then, on the Action Pane, select **Source transactions** to view the transactions that belong to that row.
1. The page that appears shows a list of the transactions of the selected type that belong to the selected row. Each transaction provides relevant details, depending on the transaction type. For guarantee transactions, you can only view the list. For other types of transactions, you can perform the following actions on this page:

    - To verify the total value of all claimed transactions on the page, view the **Claimed amount** field.
    - To view more information about any transaction, select it, and then select the **General**, **Financial dimension**, or **Dimension** tab.
    - To view any reductions that apply, select **Reduction transactions** on the Action Pane. For more information, see [Rebate reduction principles](rebate-reduction-principle.md).
    - To mark transactions as either claimed or unclaimed if you're using a claims process, select the relevant rows, and then, on the Action Pane, select one of the following commands. (You enable claims processes on the [**Rebate management parameters** page](rebate-management-parameters.md).)

        - **Set claimed \> All** – Mark all transactions as claimed.
        - **Set claimed \> Selected** – Mark the selected transactions as claimed.
        - **Set unclaimed \> All** – Mark all transactions as unclaimed.
        - **Set unclaimed \> Selected** – Mark the selected transactions as unclaimed.

    - To post the claim for one or more lines, select the relevant lines, and then, on the Action Pane, select **Post**. (The **Post** button is available only for rebate transactions. It's unavailable for provision and write-off transactions.) In the **Post** dialog box, the **From date** and **To date** fields are automatically set. Set the **Posting date** field, and then select **OK**.
    - To adjust the amount that is shown for any open or unposted transaction, select the transaction, and then follow one of these steps:

        - Edit the value in the **Corrected amount** field.
        - On the Action Pane, select **Set correction**. Then, in the drop-down dialog box that appears, in the **Corrected amount** field, enter a value.

> [!NOTE]
> When you process the next period, the transaction list will include any unclaimed transactions from the previous posting, plus any new transactions for the selected period.

## Post rebates transactions

To post the value of the rebates and deductions, you must run the posting process, unless you've set up your system to post them automatically.

### Set up the system to post all transactions automatically

To set up your system to post all transactions as soon as they are generated, turn on the **Automatically post journals** and/or **Automatically post free text invoices** option on the **Rebate management parameters** page. For more information, see [Rebate management parameters](rebate-management-parameters.md).

### Post transactions for all lines for one or more deals

If you aren't using automatic posting, after you've processed the relevant deals, follow these steps to review and post the generated transactions for all lines for one or more deals.

1. Open the appropriate [rebate deals list page](rebate-management-deals.md) for the type of deal that you want to work with.
1. Select the row for each deal that you want to post (or open the deal that you want to post).
1. On the Action Pane, on the **Rebate management deals** tab, in the **Generate** group, select one of the following commands:

    - **Post \> Provision** – Post available accruals transactions that you've created.
    - **Post \> Rebate management** – Post available rebate transactions that you've created.
    - **Post \> Write off** – Post available write-off transactions that you've created.

1. In the dialog box that appears, set the **Posting date** field. Then set the **From date** and **To date** fields to define the date range for the transactions that must be posted.
1. Select **OK** to post the transactions.

### Post transactions for one or more specific deal lines for a selected deal

If you aren't using automatic posting, after you've processed the relevant deals, follow these steps to review and post the generated transactions for one or more specific deal lines for a selected deal.

1. Open the appropriate [rebate deals list page](rebate-management-deals.md) for the type of deal that you want to work with.
1. Open the deal that has a line that you want to post transactions for.
1. Select the **Lines** tab in the upper-right corner.
1. On **Rebate management** FastTab, select the row for each deal line that you want to post.
1. On the toolbar of the **Rebate management** FastTab, select one of the following commands. (These commands are available only for deals where **Reconcile by** is set to *Line*.)

    - **Post \> Provision** – Post available accruals transactions that you've created.
    - **Post \> Rebate management** – Post available rebate transactions that you've created.
    - **Post \> Write off** – Post available write-off transactions that you've created.

1. In the dialog box that appears, set the **Posting date** field. Then set the **From date** and **To date** fields to define the date range for the transactions that must be posted.
1. Select **OK** to post the transactions.

### Post transactions using a batch job

Instead of posting transactions for specific deals or deal lines, you can run a batch job to post transactions for several deals at the same time. You can optionally apply record filters and/or set up a recurring schedule. To post transactions by using a batch job, follow these steps.

1. Follow one of these steps:

    - Go to **Rebate management \> Periodic tasks \> Post \> Provision** to post available accrual transactions that you've created.
    - Go to **Rebate management \> Periodic tasks \> Post \> Rebate management** to post available rebate transactions that you've created.
    - Go to **Rebate management \> Periodic tasks \> Post \> Write off** to post available write-off transactions that you've created.

1. In the dialog box that appears, on the **Parameters** FastTab, in the **Period** section, set the **Posting date** field. Then set the **From date** and **To date** fields to define the date range for the transactions that must be posted. 
1. In the **Guarantee Period** section, set the **From date** and **To date** fields to define the date range for the guarantees that must be posted.
1. On the **Records to include** FastTab, you can set up filters to limit the set of deals that the batch job will process. These settings work in the same way that they work for other types of batch jobs.
1. On the **Run in the background** FastTab, you can set up batch processing and scheduling options as required. These settings work in the same way that they work for other types of batch jobs.
1. Select **OK** to run and/or schedule the calculation.

## Review Rebate management journals

After your transactions have been posted, you can review the resulting journals, documents, or items. Target transactions for rebates and royalties are based on the payment type that is set in the posting profile and the rebate's output type. For example, if the rebate output is set to *Item*, a sales order will be created and can be viewed via the target transactions. Alternatively, if the payment is set up to use Accounts payable, a vendor invoice for the vendor that is set up on the customer will be created for customer rebates.

To review the journal entries that are associated with a Rebate management deal, follow these steps.

1. Open the appropriate [rebate deals list page](rebate-management-deals.md) for the type of deal that you want to work with.
1. Select the deal to inspect journal entries for.
1. On the Action Pane, on the **Rebate management deals** tab, in the **Transactions** group, select either **Transactions** or **Rebate transactions**, depending on the type of transactions that you want to look at.
1. Make sure that the **Show** field is set to *All* or *Posted*.
1. Find and select the transaction collection that you want to inspect, and then, on the Action Pane, select one of the following buttons. (These buttons are available only when relevant postings exist for the selected transaction collection.)

    - **Target transactions** – Review relevant journals and other types of documents that were generated by the selected deal.
    - **Items** – Review relevant items that were generated by the selected deal.

1. A list of relevant journals, documents, or items appears. To view more information about any journal, document, or item, select its row, and then, on the Action Pane, select **View details**.
