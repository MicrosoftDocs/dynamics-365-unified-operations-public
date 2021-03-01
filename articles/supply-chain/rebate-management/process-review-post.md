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

## Process Rebate management deals

<!-- KFM: Maybe add a few words about what happens when we "process". Do we generate invoices/credit notes, or update a journal, or something?  -->

To calculate the value of a rebate, you must run the calculation process. When processing transactions, only those deals that have a status of *Active* can be processed; other deals will be skipped.

> [!NOTE]
> In all cases, rebates will be processed at the level specified by each deal's **Reconcile by** setting (*Deal* or *Line*). You can only do single-line calculations for deals where **Reconcile by** is set to *Line*.

### Process all lines for one or more deals

1. Open the [rebate deals list page](rebate-management-deals.md) for the type of deal that you want to work with, (For example, **Rebate management \> Rebate management deals \> All rebate management deals**).
1. Mark the check box column for each deal that you want to process (or open the deal you want to process). <!-- KFM: Please confirm that we can calculate several deals at once. -->
1. On the Action Pane, open the **Rebate management deals** tab and, from the **Generate** group, select **Process \> XXXX**. <!-- KFM: I see three options here. Which to I pick? What do the others do? -->
1. The **Rebate management** dialog box opens. Set the **From date** and **To date** to establish the date range for the calculation.
1. Select **OK** to run the calculation.

### Process one or more specific deal lines for a selected deal

1. Open the [rebate deals list page](rebate-management-deals.md) for the type of deal that you want to work with, (For example, **Rebate management \> Rebate management deals \> All rebate management deals**).
1. Open the deal you want to process a line from.
1. Select the **Lines** tab at the upper-right corner.
1. On **Rebate management** FastTab, mark the check box column for each deal line that you want to process.
1. On the toolbar for the **Rebate management** FastTab, select **Process \> XXXX**. (This button is only active for deals where **Reconcile by** is set to *Line*) <!-- KFM: I see three options here. Which to I pick? What do the others do? -->
1. The **Rebate management** dialog box opens. Set the **From date** and **To date** to establish the date range for the calculation.
1. Select **OK** to run the calculation.

### Process deals using a batch job

<!-- KFM: I'm assuming we use the "Rebate management" entry here. What about the other two entries? -->

1. Go to **Rebate management \> Periodic tasks \> Process \> Rebate management**.
1. The **Rebate management** dialog box opens. On the Parameters FastTab, make settings in the following sections:
    - **Period** - Set the **From date** and **To date** to establish the date range for the calculation.
    - **Guarantee Period** - <!-- KFM: What are these for? I suppose these are for royalties? Anything special to say about them? -->
1. On the **Records to include** FastTab, you can set up some filters to limit the set of deals the batch job will process. These settings work just as they do for other kinds of bach jobs.
1. Use the **Run in the background** FastTab to set up batch processing and scheduling options as needed. These settings work just as they do for other kinds of bach jobs.
1. Select OK to run and/or schedule the calculation.

## View and edit Rebate management transactions

<!-- KFM: This section doesn't make any sense to me. What is this about? -->

When you process one or more deals, the system creates *transactions*, which you can view and possibly edit before posting.

1. Do one of the following: <!-- KFM: What will I see with each of these options? Are the transactions filtered?  -->
    - The **transactions** button on the transactions group of the rebates/deductions form.
    _Note: The transaction will be processed at the level specified in the reconcile by field._
    - The **transactions** button in the rebates and deductions fast tab.
    _Note: The rebates will be processed for the selected rebates and deductions calculation only. This option will not be available if reconcile by deal has been specified._
    - The **transactions** button lists all the invoices/delivery notes/orders that were found to formulate the rebates and deductions.
    _Note: The rebates and deductions transaction lines could be deleted._ <!-- KFM: What do you mean by "found"? -->
1. It is possible (use claims process parameter must be active) to select only those the invoices/delivery notes/orders that are actually being claimed by the customer. The selection of these is possible within the **transactions** form. Any unclaimed transactions will appear on the next rebates. <!-- KFM: I don't understand this. -->
1. To use the claims process, deselect any transactions that haven't been claimed by the customer. It is possible to use the set claimed and set unclaimed buttons to facilitate this process. The all option will select/deselect all records. The selected option will select/deselect only those records which have been selected. The value options defaulted during the claims process are set by the rebate parameters form. For more information on these values, please see the **Rebates parameters** details. <!-- KFM: I don't understand this. -->
1. Use the **claimed amount** on this form to verify the amount claimed. <!-- KFM: I don't see this here. -->
1. To post the claim use the post button. Select the **posting date** , the **from** and **to** periods will already be set, click **OK**. When processing, provision and write-off transactions will not have the 'Post' function available for selection. It is only available for Rebate transactions. <!-- KFM: I don't see this here. -->
1. After processing the next period, the transactions will include any unclaimed from the previous posting plus any new transactions for the selected period.
1. The amount on **open** or **un-posted** rebates and deductions transactions can be adjusted should there be any overriding factors to consider. To do this, **enter the correct amount** in the **corrected amount** column for the specific transaction or alternatively select the **set correction** button. The corrected amount will be allocated across all of the claimed transaction lines on a pro-rata basis. <!-- KFM: I don't see any of this here. -->

## Guarantee transactions

<!-- KFM: I suppose these are otherwise similar to the other types of transactions? Assuming the previous section makes sense, can we do all of those things for guarantee transactions too? If so, we should combine these sections. -->

The creation process creates transactions which can be viewed before posting. The form is accessed from:

1. The guarantee transactions button on the transactions group of the rebates and deductions form.
1. The guarantee transactions button in the rebates and deductions fast tab.

## Review Rebate management journals

<!-- KFM: This section doesn't make any sense to me. What is this about? -->

The creation process creates transactions which can be viewed before posting and creating either a journal or debit/credit note. Users are only able to review and edit journal transactions if the Rebate parameters is not set to automatically post the journal transactions. Target transactions for rebates and royalties are based on the payment type set in the posting profile and the rebate's output type. For example, if the rebate output is set to Item, a Sales order will be created and can be viewed via the target transactions. Or, for example, if the payment is set to use accounts payable, a vendor invoice for the vendor setup on the customer will be created for Customer rebates. The form is accessed from:

1. The **transactions** button on the transactions group of the rebates and deductions form.
_Note: The transaction will be processed at the level specified in the reconcile by field._
1. The **process** button in the rebates and deductions fast tab.
_Note: The rebates will be processed for the selected rebates and deductions calculation only. This option will not be available if reconcile by deal has been specified._
1. It can be run multiple times however it refreshes the value each time with the latest calculation in this case it should be remembered that any edited transactions will be **reset**.
1. The journals generate could also be posted if the **Post a journal automatically** parameter is switched on.
1. To view the journal or free text invoice (free text information will only display once the invoice has been posted) information, select original document. To see the details, select **show**.

To assist with identifying which transactions will be created during rebates and deductions processing, the 'document posted' on the Transactions form indicates the target (journal, vendor invoice, or sales/purchase order) and it's posting status. This is different to the other 'posted' status displayed, which identifies if the provision/write-off/rebate has been posted.

## Post rebates transactions

To post the value of the rebates and deductions the posting process needs to be run. The process could be triggered from:

1. The **post** button in the generate group on the action pane of the rebates and deductions form.
1. The **transactions** button in the rebates and deductions fast tab. <!-- KFM: Do you mean the POST button? --> 
1. These can also be processed via a batch job from **rebates and deductions \> process.**

## Change the status of a deal

To change the status of a deal use the **change status** button on the maintain group of the action pane. When changing status of a rebate, an active rebate can be set to inactive and an inactive rebate can be set to active. <!-- KFM: It seems like we have mor status options than this. -->  Select the new **rebate status** and click **ok**. This status is for informational purposes only.




<!-- KFM: Maybe add a section about the FIFO periodic task, though it's also mentioned in the DEALS topic. --> 