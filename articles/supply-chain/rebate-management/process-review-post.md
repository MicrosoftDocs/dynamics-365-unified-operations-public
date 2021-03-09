---
# required metadata

title: Process, review, and post rebates
description: This topic describes how to process your Rebate management deals, calculate their discounts, review the generated transactions, post transactions, and review the postings.
author: sherry-zheng
manager: tfehr
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
ms.search.scope:  Core, Operations
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

This topic describes how to process your Rebate management deals, calculate their discounts, review the generated transactions, post transactions, and review the postings.

## Change the status of a deal

You can assign a status to each deal to help keep track it. The status is for informational purpose only. To set the status of a deal:

1. Select a deal (for example on the [**All rebate management deals** page](rebate-management-deals.md)).
1. On the Action Pane, open the **Rebate management deals** tab and, from the **Maintain** group, select **Change status**.
1. The **Change status** dialog box opens. Set **Rebate status** to the new status.
1. Select **OK**.

## Calculate FIFO purchase prices

The **Calculate FIFO purchase price** periodic task must run to calculate the rebates for [deals](rebate-management-deals.md) where the **Price basis** is *FIFO*. Based on a FIFO rule, the system will calculate the value of the sold stock. This value will then be used to calculate the vendor rebates.

To run the FIFO calculation, go to **Rebates management > Periodic tasks > Calculate FIFO purchase price**. A dialog box opens. Select **OK** to run the calculation.

## Process Rebate management deals

When you process a deal, the system calculates all relevant rebates and royalties that are set up. Only those selected deals that have calculation periods that are ready to be calculated and that have a status of *Active* will be processed. After processing, the system will generate a set of *transactions*, which you will be able to review and then post.

> [!NOTE]
> In all cases, rebates will be processed at the level specified by each deal's **Reconcile by** setting (*Deal* or *Line*). You can only do single-line calculations for deals where **Reconcile by** is set to *Line*.

### Process all lines for one or more deals

1. Open the [rebate deals list page](rebate-management-deals.md) for the type of deal that you want to work with.
1. Mark the check box column for each deal that you want to process (or open the deal you want to process).
1. On the Action Pane, open the **Rebate management deals** tab and, from the **Generate** group, select one of the following:
    - **Process \> Provision** - Provisions a set of accruals for each relevant rebate deal, but doesn't post them.
    - **Process \> Rebate management** - Processes a series of transactions that provide the value of the rebate for each deal.
    - **Process \> Write off** - Reverses previously posted transactions to write them off, therefore making it possible to recalculate new rebate deal transactions.
1. A dialog box opens. Set the **From date** and **To date** to establish the date range for the calculation.
1. Select **OK** to run the calculation.

### Process one or more specific deal lines for a selected deal

1. Open the [rebate deals list page](rebate-management-deals.md) for the type of deal that you want to work with.
1. Open the deal you want to process a line from.
1. Select the **Lines** tab at the upper-right corner.
1. On **Rebate management** FastTab, mark the check box column for each deal line that you want to process.
1. On the toolbar for the **Rebate management** FastTab, select one of the following (these buttons are only active for deals where **Reconcile by** is set to *Line*):
    - **Process \> Provision** - Provisions a set of accruals for each relevant deal line, but doesn't post them.
    - **Process \> Rebate management** - Processes a series of transactions that provide the value of the rebate for each deal line.
    - **Process \> Write off**  - Reverses previously posted transactions to write them off, therefore making it possible to recalculate new rebate deal transactions.
1. A dialog box opens. Set the **From date** and **To date** to establish the date range for the calculation.
1. Select **OK** to run the calculation.

### Process deals using a batch job

As an alternative to processing specific deals or deal deal lines, you can instead run a batch job to process several deals at once, optionally with record filters and/or a recurring schedule. To process deals using a batch job:

1. Go to one of the following:
    - **Rebate management \> Periodic tasks \> Process \> Provision** - Provisions a set of accruals for each relevant deal, but doesn't post them.
    - **Rebate management \> Periodic tasks \> Process \> Rebate management** - Processes a series of transactions that provide the value of the rebate for each deal.
    - **Rebate management \> Periodic tasks \> Process \> Write off** - Reverses previously posted transactions to write them off, therefore making it possible to recalculate new rebate deal transactions.
1. A dialog box opens. On the **Parameters** FastTab, make settings in the following sections:
    - **Period** - Set the **From date** and **To date** to establish the date range of transactions for the calculation.
    - **Guarantee Period** - Set the **From date** and **To date** to establish the date range of guarantees for the calculation.
1. On the **Records to include** FastTab, you can set up some filters to limit the set of deals the batch job will process. These settings work just as they do for other kinds of bach jobs.
1. Use the **Run in the background** FastTab to set up batch processing and scheduling options as needed. These settings work just as they do for other kinds of bach jobs.
1. Select **OK** to run and/or schedule the calculation.

## View and edit Rebate management transactions

When you process one or more deals, the system creates *transactions*, which you can view and possibly edit before posting.

1. Do one of the following:
    - Select the deal you want to view transactions for (for example on the [**All rebate management deals** page](rebate-management-deals.md)). On the Action Pane, open the **Rebate management deals** tab and, from the **Transactions** group, select **Transactions** or **Guarantee transactions**, depending on which type of transaction you want to view.
    - Open a deal (for example on the [**All rebate management deals** page](rebate-management-deals.md)) to view its details. On the **Rebate management** FastTab, select the deal line you want to see transactions for. Then, from the FastTab toolbar, select **Transactions** or **Guarantee transactions**, depending on which type of transaction you want to view. (These buttons only active for deals where **Reconcile by** is set to *Line*.)
1. The **Rebate management date transactions** or **Rebate management guarantee transactions** page opens. It displays a grid, where each line represents a collection of transaction from a single rebate or guarantee period. Select a row from the grid and then select **Source transactions** on the Action Pane to view transactions that belong to that row.
1. A page opens showing a list of transactions of the selected type that belong to the selected row. Each transaction provides relevant details (depending on the transaction type). For guarantee transactions, you are only able to view the list. For other types of transactions, you can do the following actions on this page:
    - To verify the total value of all claimed transactions shown on this page, view the **Claimed amount** field.
    - To see more information about any transaction, select it and then open the **General**, **Financial dimension**, or **Dimension** tab.
    - Select **Reduction transactions** on the Action Pane to see any reductions that apply. More information: [Rebate reduction principles](rebate-reduction-principle.md)
    - If you are using a claims process (enabled on the [**Rebate management parameters** page](rebate-management-parameters.md)), you can mark any or all transactions as either claimed or unclaimed, as needed, by selecting the relevant rows and selecting one of the following from the Action Pane:
        - **Set claimed \> All** - Marks all transactions as claimed.
        - **Set claimed \> Selected** - Marks the selected transactions as claimed.
        - **Set unclaimed \> All** - Marks all transactions as unclaimed.
        - **Set unclaimed \> Selected** - Marks the selected transactions as unclaimed. 
    - To post the claim for noe or more lines, select the relevant lines and then select **Post** from the Action Pane. The **Post** dialog box opens, with its **From date** and **To date** already set. Set the **Posting date** and select **OK**. (The **Post** button is only available for rebate transactions. It is disabled for provision and write-off transactions.).
    - You can adust the amount shown for any open or un-posted transactions if necessary. To do so, select a transaction and then either edit the value in the **Corrected amount** column or select **Set correction** on the Action Pane to open a drop-down dialog box and enter a **Corrected amount** there.

> [!NOTE]
> When you process the next period, the transactions list will include any unclaimed transactions from the previous posting, plus any new transactions for the selected period.

## Post rebates transactions

To post the value of the rebates and deductions the posting process needs to be run, unless you have set your system to post them automatically.

### Set the system to post all transactions automatically

To set your system to post all transactions as soon as they are generated, enable the **Automatically post journals** and/or **Automatically post free text invoices** options on the **Rebate management parameters** page, as needed. More information: [Rebate management parameters](rebate-management-parameters.md)

### Post transactions for all lines for one or more deals

If you aren't using automatic posting, then after you have processed the relevant deals, do the following to review and post the generated transactions for all lines for one or more deals:

1. Open the [rebate deals list page](rebate-management-deals.md) for the type of deal that you want to work with.
1. Mark the check box column for each deal that you want to post (or open the deal you want to post).
1. On the Action Pane, open the **Rebate management deals** tab and, from the **Generate** group, select one of the following:
    - **Post \> Provision** - Posts available accruals transactions that you have created.
    - **Post \> Rebate management** - Posts available rebate transactions that you have created.
    - **Post \> Write off** - Posts available write off transactions that you have created.
1. A dialog box opens. Set the **Posting date**. Then set **From date** and **To date** to establish the date range for the transactions to be posted.
1. Select **OK** to post the transactions.

### Post transactions for one or more specific deal lines for a selected deal

If you aren't using automatic posting, then after you have processed the relevant deals, do the following to review and post the generated transactions for one or more specific deal lines for a selected deal:

1. Open the [rebate deals list page](rebate-management-deals.md) for the type of deal that you want to work with.
1. Open the deal that has a line you want to post transactions for.
1. Select the **Lines** tab at the upper-right corner.
1. On **Rebate management** FastTab, mark the check box column for each deal line that you want to post.
1. On the toolbar for the **Rebate management** FastTab, select one of the following (these buttons are only active for deals where **Reconcile by** is set to *Line*):
    - **Post \> Provision** - Posts available accruals transactions that you have created.
    - **Post \> Rebate management** - Posts available rebate transactions that you have created.
    - **Post \> Write off** - Posts available write off transactions that you have created.
1. A dialog box opens. Set the **Posting date**. Then set **From date** and **To date** to establish the date range for the transactions to be posted.
1. Select **OK** to post the transactions.

### Post transactions using a batch job

As an alternative to post transactions for specific deals or deal deal lines, you can instead run a batch job to post transactions for several deals at once, optionally with record filters and/or a recurring schedule. To post transactions using a batch job:

1. Go to one of the following:
    - **Rebate management \> Periodic tasks \> Post \> Provision** - Posts available accruals transactions that you have created.
    - **Rebate management \> Periodic tasks \> Post \> Rebate management** - Posts available rebate transactions that you have created.
    - **Rebate management \> Periodic tasks \> Post \> Write off** - Posts available write off transactions that you have created.
1. A dialog box opens. On the **Parameters** FastTab, make settings in the following sections:
    - **Period** - Set the **Posting date**. Then set **From date** and **To date** to establish the date range for the transactions to be posted. 
    - **Guarantee Period** - Set the **From date** and **To date** to establish the date range of guarantees to be posted.
1. On the **Records to include** FastTab, you can set up some filters to limit the set of deals the batch job will process. These settings work just as they do for other kinds of bach jobs.
1. Use the **Run in the background** FastTab to set up batch processing and scheduling options as needed. These settings work just as they do for other kinds of bach jobs.
1. Select **OK** to run and/or schedule the calculation.

## Review Rebate management journals

Once your transactions have been posted, you are able to review the resulting journals, documents, or items. Target transactions for rebates and royalties are based on the payment type set in the posting profile and the rebate's output type. For example, if the rebate output is set to *Item*, a sales order will be created and can be viewed via the target transactions. Or, for example, if the payment is set to use *Accounts payable*, a vendor invoice for the vendor set up on the customer will be created for customer rebates.

To review journal entries associated with a Rebate management deal:

1. Open the [rebate deals list page](rebate-management-deals.md) for the type of deal that you want to work with.
1. Select deal that you want to inspect journal entires for.
1. On the Action Pane, open the **Rebate management deals** tab and, from the **Transactions** group, select **Transactions** or **Rebate transactions** (depending on which type of transactions you want to look at).
1. Make sure **Show** is set to *All* or *Posted*. Then find and select the transaction collection you want to inspect. Then select one of the following on the Action Pane;
    - **Target transactions** - To review relevant journals and other types of documents generated by the selected deal. (This button is only active when relevant posting exist for the selected transaction collection.)
    - **Items** - To review relevant items granted by the deal. (This button is only active when relevant posting exist for the selected transaction collection.)
1. A list of relevant journals, documents, or items opens. To get more information, select a row and then select **View details** from the Action Pane.
