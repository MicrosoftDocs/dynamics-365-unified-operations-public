---
# required metadata

title: Process, review, and post rebates
description: 
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

<!-- KFM: Maybe add a few words about what happens when we "process". Do we generate invoices/credit notes, or update a journal, or something?  -->

When you process a deal, the system calculates all relevant rebates and royalties that are set up. Only those selected deals that have calculation periods that are ready to be calculated and that have a status of *Active* will be processed. After processing, the system will generate a set of *transactions*, which you will be able to review and then post.

> [!NOTE]
> In all cases, rebates will be processed at the level specified by each deal's **Reconcile by** setting (*Deal* or *Line*). You can only do single-line calculations for deals where **Reconcile by** is set to *Line*.

### Process all lines for one or more deals

1. Open the [rebate deals list page](rebate-management-deals.md) for the type of deal that you want to work with.
1. Mark the check box column for each deal that you want to process (or open the deal you want to process). <!-- KFM: Please confirm that we can calculate several deals at once. -->
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
1. The **Rebate management date transactions** or **Rebate management guarantee transactions** page opens. It displays a grid, where each line represents a collaction of transaction from a single rebate or guarantee period. Select a row from the grid and then select one of the following buttons on the Action Pane to view transactions that belong to that row:
    - **Source transactions** - <!-- KFM: This is what we are doing-->
    - **Target transactions** - <!-- KFM: Link to last section -->
    - **Items** - <!-- KFM: Link to last section. Ask Natalie. -->
1. A page opens showing a list of transactions of the selected type that belong to the selected row. Each transaction provides relevant details (depending on the transaction type). For guarantee transactions, you are only able to view the list. For other types of transactions, you can do the following actions on this page:
    - To verify the total value of all claimed transactions shown on this page, view the **Claimed amount** field.
    - To see more information about any transaction, select it and then open the **General**, **Financial dimension**, or **Dimension** tab.
    - Select **Reduction transactions** on the Action Pane to <!-- KFM: See transactions generated by reduction principles. Link to that topic. -->
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

To post the value of the rebates and deductions the posting process needs to be run. <!-- KFM: We need to generate transactions first, right? --> 

### Set the system to post all transactions automatically

<!-- KFM: If we enable **Post a journal automatically** parameter, then is none of this necessary (maybe add section to explain this)? -->


### Post transactions for all lines for one or more deals

1. Open the [rebate deals list page](rebate-management-deals.md) for the type of deal that you want to work with.
1. Mark the check box column for each deal that you want to post (or open the deal you want to post).
1. On the Action Pane, open the **Rebate management deals** tab and, from the **Generate** group, select one of the following:
    - **Post \> Provision** - Posts available accruals transactions that you have created.
    - **Post \> Rebate management** - Posts available rebate transactions that you have created.
    - **Post \> Write off** - Posts available write off transactions that you have created.
1. A dialog box opens. Set the **Posting date**. Then set **From date** and **To date** to establish the date range for the transactions to be posted.
1. Select **OK** to post the transactions.

### Post transactions for one or more specific deal lines for a selected deal

1. Open the [rebate deals list page](rebate-management-deals.md) for the type of deal that you want to work with.
1. Open the deal that has a line you want to post transactions for.
1. Select the **Lines** tab at the upper-right corner.
1. On **Rebate management** FastTab, mark the check box column for each deal line that you want to post.
1. On the toolbar for the **Rebate management** FastTab, select one of the following (these buttons are only active for deals where **Reconcile by** is set to *Line*):
    - **Post \> Provision** - Posts available accruals transactions that you have created.
    - **Post \> Rebate management** - Posts available rebate transactions that you have created.
    - **Post \> Write off** - Posts available write off transactions that you have created.
1. A dialog box opens. Set the **Posting date**. Then set **From date** and **To date** to establish the date range for the transactions to be posted. <!-- KFM: Confirm these date descriptions. -->
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

<!-- KFM: This section seems to repeat the previous one. What are we doing here? How does this relate to the next section? Maybe this should come after the next section? -->

The creation process creates transactions which can be viewed before posting and creating either a journal or debit/credit note. Users are only able to review and edit journal transactions if the Rebate parameters is not set to automatically post the journal transactions. Target transactions for rebates and royalties are based on the payment type set in the posting profile and the rebate's output type. For example, if the rebate output is set to Item, a Sales order will be created and can be viewed via the target transactions. Or, for example, if the payment is set to use accounts payable, a vendor invoice for the vendor setup on the customer will be created for Customer rebates. The form is accessed from:

1. The **transactions** button on the transactions group of the rebates and deductions form.
_Note: The transaction will be processed at the level specified in the reconcile by field._
1. The **process** button in the rebates and deductions fast tab.
_Note: The rebates will be processed for the selected rebates and deductions calculation only. This option will not be available if reconcile by deal has been specified._
1. It can be run multiple times however it refreshes the value each time with the latest calculation in this case it should be remembered that any edited transactions will be **reset**. <!-- KFM: I don't understand this -->
1. The journals generated could also be posted if the **Post a journal automatically** parameter is switched on.
1. To view the journal or free text invoice (free text information will only display once the invoice has been posted) information, select original document. To see the details, select **show**.<!-- KFM: I don't understand this -->

To assist with identifying which transactions will be created during rebates and deductions processing, the 'document posted' on the Transactions form indicates the target (journal, vendor invoice, or sales/purchase order) <!-- KFM: Seems like it just shows a check mark? --> and it's posting status. This is different to the other 'posted' status displayed, which identifies if the provision/write-off/rebate has been posted. <!-- KFM: I don't understand this -->