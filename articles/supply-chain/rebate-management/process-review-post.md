---
# required metadata

title: Process, review, and post rebates
description: This topic describes how to process your Rebate management deals, calculate their discounts, review the transactions that are generated, post transactions, and review the postings.
author: sherry-zheng
ms.date: 02/19/2021
ms.topic: article
ms.prod: 
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

## Create source transactions

You can create the sales or purchase orders with source transactions either before or after creating an applicable Rebate management deal.

You can set each deal line to automatically create a rebate provision by posting a sales or purchase order's delivery or invoice. You can do this by setting the deal line's **Transaction type** (*Delivery* or *Invoice*) and **Process at posting** set to *Yes*. Process at posting is disabled where **Transaction type** is set to *Order*. For source transaction that were created after a deal was activated, you can still process the provision as described in [Process Rebate management deals](#process-deals).

### Enable price details

Before you can create source transactions, you must enable the price details option for account receivables, as described in the following procedure.

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Open the **Prices** tab.
1. Expand the **Price details** FastTab.
1. Set **Enable price details** to *Yes*.

### Create a source transaction

To create a source transaction:

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Select **New**. To mimic the way in which rebate claims would be generated, the next task is to create a sales order, where the product and quantity will qualify the customer in question for a rebate.
1. In the **Customer account** field, enter or select a customer that will qualify for a rebate deal.
1. Select **OK** to create the sales order.
1. On the **Sales order lines** FastTab, add a line with the following values
    - **Item number** – Specify an item that qualifies for a rebate.
    - **Quantity** – Specify a quantity that would qualify for a rebate deal that includes a line where **Basis** is set to *Quantity.*
    - **Unit price** – Specify a price that would qualify for a rebate deal that includes a line where **Basis** is set to *Value.*
    - **Site** – Select a site where the relevant product is available, and which qualifies for a rebate deal.
    - **Warehouse** – Select a warehouse where the relevant product is available, and which qualifies for a rebate deal.
1. From the **Sales order lines** FastTab toolbar, select **Sales order line \> Price details**. (If you don't see this option, it's because you didn't enable the pricing details option, as described in the previous subsection.)
1. The **Price details** page opens. Expand the **Rebate management** FastTab. The **Rebate management** tab lists all the rebate management deals that apply to the current order line and shows the estimated rebate amount in the order's currency. Note that the displayed amounts are only estimates of what the future rebate claims may be. The actual rebate amounts may differ depending on factors including:
    - The total sales volume achieved by the customer under a periodic rebate agreement
    - Whether the customer had returned all or partial quantities
    - Whether the applicable sales order achieved the **Transaction type** (*Order, Delivery* or *Invoice*) defined for the Rebate management deal.
    - For deals where **Output** set to *Item*, the deal will be displayed with a blank rebate amount.
1. Expand the **Detail** FastTab. Note that the **Margin estimation** field group includes the following fields added by Rebate management, each of which shows values per unit (while the **Rebate management** FastTab shows total values for the line):
    - **Rebate management rebate amount** (sales orders only)
    - **Rebate management royalty amount** (sales orders only)
    - **Rebate management vendor rebate amount** (sales orders and purchase orders)
1. Close the **Price details** page.
1. If the sales order should not qualify for rebates you just saw, you would do the following (but usually you would not do this):
    1. On the **Sales order lines** FastTab, select the relevant line.
    1. Expand the **Line details** FastTab and then open the **Price and discount** tab.
    1. Set **Exclude from rebate management** to *Yes.* This option does not apply to Purchase orders. Only customer rebates will be excluded when this option is set to *Yes*&mdash;customer royalty and vendor rebates will still apply.
1. On the **Action Pane**, open the **Pick and pack** tab and, from the **Generate** group, select **Post packing slip**.
1. Expand the **Parameters** FastTab and set **Quantity** to *All*.
1. Select **OK**.
1. If you're asked to confirm the operation, select **OK**.
1. On the **Action Pane**, open the **Invoice** tab and, from the **Generate** group, select **Invoice**.
1. Expand the **Parameters** FastTab.
1. In the **Quantity** field, select *All* or *Packing slip*.
1. Select **OK**.
1. If you're asked to confirm the operation, select **OK**.

<a name="process-deals"></a>

## Process Rebate management deals

When you process a deal, the system calculates all relevant rebates and royalties that are set up. Only selected deals that have calculation periods that are ready to be calculated and that have a status of *Active* will be processed. After processing is completed, the system generates a set of transactions that you can review and then post.

> [!NOTE]
> In all cases, rebates are processed at the level that is specified by each deal's **Reconcile by** setting (*Deal* or *Line*). You can do single-line calculations only for deals where the **Reconcile by** field is set to *Line*.

### Process all lines for one or more deals

1. Open the appropriate [rebate deals list page](rebate-management-deals.md) for the type of deal that you want to work with.
1. Select the row for each deal that you want to process (or open the deal that you want to process).
1. On the Action Pane, on the **Rebate management deals** tab, in the **Generate** group, select one of the following commands:

    - **Process \> Provision** – Provision a set of accruals for each relevant rebate deal, but don't post them. This menu item is unavailable for deals where the **Rebate output** field is set to *Item*.
    - **Process \> Rebate management** – Process a series of transactions that provide the value of the rebate for each deal.
    - **Process \> Write off** – For each source transaction for the rebate deal and specified period, process the variance between the amounts that were posted for a provision and for rebate management. This menu item is unavailable for deals where the **Rebate output** field is set to *Item*.

1. In the dialog box that appears, set the **From date** and **To date** fields to define the date range for the calculation.
1. Select **OK** to run the calculation.

### Process one or more specific deal lines for a selected deal

1. Open the appropriate [rebate deals list page](rebate-management-deals.md) for the type of deal that you want to work with.
1. Open the deal that you want to process a line from.
1. Select the **Lines** tab in the upper-right corner.
1. On **Rebate management** FastTab, select the row for each deal line that you want to process.
1. On the toolbar of the **Rebate management** FastTab, select one of the following commands. (These commands are available only for deals where the **Reconcile by** field is set to *Line*.)

    - **Process \> Provision** – Provision a set of accruals for each relevant deal line, but don't post them. This menu item is unavailable for deals where the **Rebate output** field is set to *Item*.
    - **Process \> Rebate management** – Process a series of transactions that provide the value of the rebate for each deal line.
    - **Process \> Write off** – For each source transaction for the rebate deal and specified period, process the variance between the amounts that were posted for a provision and for rebate management. This menu item is unavailable for deals where the **Rebate output** field is set to *Item*. 

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

### Process deals using the rebate workbench

Instead of processing specific deals or deal lines, you can use the *rebate workbench* to process several deals at the same time. You can optionally apply record filters and/or set up a recurring schedule. Use the following procedure to process deals by using the rebate workbench. You don't need to select any rows&mdash;the system will process all lines that meet the date and filter requirements you set up during the following procedure.

1. Go to **Rebate management > Rebate management deals > Rebate workbench**.
1. On the Action Pane, open the **Rebate workbench** tab and then select one of the following commands in the **Processing** group:
    - **Process > Provision** – Provision a set of accruals for each relevant deal line, but don't post them.
    - **Process > Rebate management** – Process a series of transactions that provide the value of the rebate for each deal line.
    - **Process > Write off** – Process the variance between provision and rebate management posted for each source transaction per rebate deal and specified period.
1. The **Rebate management** dialog opens. In the **Period** field group, set the **From date** and **To date** fields to define the date range for the calculation.
1. In the **Guarantee period** field group, set the **From date** and **To date** fields to define the date range for guarantees for the calculation.
1. On the **Records to include** FastTab, you can set up filters to limit the set of deals that the batch job will process. These settings work in the same way that they work for other types of batch jobs.
1. On the **Run in the background** FastTab, you can set up batch processing and scheduling options as required. These settings work in the same way that they work for other types of batch jobs.
1. Select **OK** to run and/or schedule the calculation.

## View and edit Rebate management transactions

When you process one or more deals, the system creates transactions that you can view and, perhaps, edit before you post them.

### View and edit Rebate management transactions using the rebate deals list page

To view and edit Rebate management transactions using the rebate deals list page:

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

    - Select **Post** on the Action Pane to post the claim for all the relevant lines. If you're using a claims process (when the **Use claim process** option is enabled on the **Rebate management parameters** page), only the lines that are marked as **Claimed** are posted. Otherwise, all the source transactions for the selected rebate transaction are posted. The **Post** button is available only for rebate transactions. It's unavailable for provision and write-off transactions. In the **Post** dialog box, the **From date** and **To date** fields are automatically set. Set the **Posting date** field, and then select **OK**.
    - To adjust the amount that is shown for any open or unposted transaction, select the transaction, and then follow one of these steps:

        - Edit the value in the **Corrected amount** field.
        - On the Action Pane, select **Set correction**. Then, in the drop-down dialog box that appears, in the **Corrected amount** field, enter a value.

> [!NOTE]
> If you're using a claims process, when you process the next period, the transaction list will include any unclaimed transactions from the previous posting, plus any new transactions for the selected period.

### View and edit Rebate management transactions using the rebate workbench

To view and edit Rebate management transactions using the rebate workbench:

1. Go to **Rebate management \> Rebate management deals \> Rebate workbench**
1. Set the **Show** field to *Not posted*.
1. The **Rebate workbench** page shows a list of the transactions, each of which provides relevant details, depending on the transaction type. You can perform the following actions on this page:
    - To view more information about any transaction, select it, and then select the **General**, **Financial dimension**, or **Dimension** tab.
    - If you're using a claims process, you can mark transactions as either claimed or unclaimed. Select the relevant rows, and then, on the Action Pane, open the **Rebate workbench** tab and select one of the following commands. (You enable claims processes on the [**Rebate management parameters** page](rebate-management-parameters).)
        - **Set claimed** – Mark the selected transactions as claimed.
        - **Set unclaimed** – Mark the selected transactions as unclaimed.
    - To post the claim for one or more lines, select the relevant lines. Then, on the Action Pane, open the **Rebate workbench** tab and select **Post**. The **Post** button is available for provision, rebate and write off transactions. In the **Post** dialog box, the **From date** and **To date** fields are automatically set. Set the **Posting date** field, and then select **OK**.
    - To adjust the amount that is shown for any open or unposted transaction, select the transaction, and then follow one of these steps:
        - Edit the value in the **Corrected amount** field.
        - On the Action Pane, open the **Rebate workbench** tab and select **Set correction**. Then, in the drop-down dialog box that appears, in the **Corrected amount** field, enter a value.

> [!NOTE]
> If you're using a claims process, when you process the next period, the transaction list will include any unclaimed transactions from the previous posting, plus any new transactions for the selected period.

## Post rebates transactions

To post the value of a processed provision, rebate management amount, and write-off, you must run the posting process. The posting process marks the provision, rebate management, or write-off transactions as posted, and creates the target transaction. If you don't have to review the target transaction, these transactions can be set up so that they are automatically posted.

### Set up the system to post all target transactions automatically

To set up your system to post all target transactions as soon as they are generated by a posting provision, rebate management amount, and write-off, turn on the **Automatically post journals** and/or **Automatically post free text invoices** option on the **Rebate management parameters** page. For more information, see [Rebate management parameters](rebate-management-parameters.md).

### Post transactions for all lines for one or more deals

After you've processed the relevant deals, follow these steps to review and post the generated transactions for all lines for one or more deals.

1. Open the appropriate [rebate deals list page](rebate-management-deals.md) for the type of deal that you want to work with.
1. Select the row for each deal that you want to post (or open the deal that you want to post).
1. On the Action Pane, on the **Rebate management deals** tab, in the **Generate** group, select one of the following commands:

    - **Post \> Provision** – Post available accruals transactions that you've created.
    - **Post \> Rebate management** – Post available rebate transactions that you've created.
    - **Post \> Write off** – Post available write-off transactions that you've created.

1. In the dialog box that appears, set the **Posting date** field. Then set the **From date** and **To date** fields to define the date range for the transactions that must be posted.
1. Select **OK** to post the transactions.

### Post transactions for one or more specific deal lines for a selected deal

After you've processed the relevant deals, follow these steps to review and post the generated transactions for one or more specific deal lines for a selected deal. This procedure is applicable only for deals where the **Reconcile by** field is set to *Line*.

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

### Post transactions using the rebate workbench

After you've processed provision, rebate, or write off transactions, follow these steps to use the rebate workbench to review and post the generated transactions for one or more specific transaction lines for all deals.

1. Go to **Rebate management \> Rebate management deals \> Rebate workbench**
1. On the grid, select the row for each transaction line that you want to post. You can select unposted provision, rebate, and/or write off transactions. The following rules apply:
    - The system will also post all of the lines that have the same **Rebate transaction number** as the line(s) you have selected.
    - The system will not post any lines of **Transaction type** *Rebate* that aren't marked as claimed.
    - If you select lines that have already been posted, the posted lines will simply be skipped.
    - You must select at least one unposted line for the **Post** button to be available.
1. On the Action Pane, open the Rebate workbench tab and, from the Processing group, select **Post**.
1. The **Post** dialog opens. Set the **Posting date**. The **From date** and **To date** fields will automatically be defined by the earliest **From date** and last **To date** of selected rows.
1. Select **OK** to post the transactions.

<a name="review-journals"></a>

## Review Rebate management journals

After your transactions have been posted, you can review the resulting journals, documents, or items. Target transactions for rebates and royalties are based on the payment type that is set in the posting profile and the rebate's output type. For example, if the rebate output is set to *Item*, a sales order will be created for a customer rebate, and a purchase order will be created for a vendor rebate. These orders can be viewed via the target transactions. Alternatively, if the payment is set up to use Accounts payable, a vendor invoice for the vendor that is set up on the customer will be created for customer rebates.

### Review journals using the rebate deals list page

To review the journal entries that are associated with a Rebate management deal, follow these steps.

1. Open the appropriate [rebate deals list page](rebate-management-deals.md) for the type of deal that you want to work with.
1. Select the deal to inspect journal entries for.
1. On the Action Pane, on the **Rebate management deals** tab, in the **Transactions** group, select either **Transactions** or **Guarantee transactions**, depending on the type of transactions that you want to look at.
1. Set the **Show** field to *All* or *Posted*.
1. Find and select the transaction collection that you want to inspect, and then, on the Action Pane, select one of the following buttons. (These buttons are available only when relevant postings exist for the selected transaction collection.)

    - **Target transactions** – Review relevant journals and other types of documents that were generated by the selected deal.
    - **Items** – Review relevant sales orders or purchase orders that were generated by the selected deal.

1. A list of relevant journals, documents, or items appears. To view more information about any journal, document, or item, select its row, and then, on the Action Pane, select **View details**.

### Review journals using the rebate workbench

To review journals using the rebate workbench, follow these steps.

1. Go to **Rebate management \> Rebate management deals \> Rebate workbench**
1. Set the **Show** field to _All_ or _Posted_.
1. Find and select the line that you want to inspect. Then, on the Action Pane, open the **Rebate workbench** tab, and in the **View** group, select **Target transactions** (this button is only available when relevant postings exist for the selected line).
1. A list of relevant journals, documents, or items appears. To view more information about any journal, document, or item, select its row, and then, on the Action Pane, select **View details**.

## Rebate management transactions on the deduction workbench

When you post a Rebate management transaction with one of the following **Payment type** settings, the system creates a customer deduction journal or a free text invoice for the relevant customer account:

- *Customer deductions*
- *Tax invoice customer deductions*
- *Trade spending*
- *Reporting*

Once a created target transaction has been posted, it will be available as an **Open transaction** on the **Deduction workbench** page (**Sales and marketing > Trade allowances > Deductions > Deduction workbench**). Open transactions will have a **Claim type** of *Rebate management* and the **Rebate transaction number** will be available for traceability. The date will be populated with the posting date of the rebate management target transaction. You can use the deduction workbench to settle open transactions to existing deductions for the same customer account by selecting **Maintain > Match** from the Action Pane.

<!--KFM: Add a link to the deduction workbench topics -->

## Purge unposted transactions

After you've processed provision, rebate, or write off transactions, follow these steps to purge selected unposted transactions.

1. Go to **Rebate management \> Rebate management deals \> Rebate workbench**
2. Set the **Show** field to *Not posted*.
3. Find and select the transactions to be deleted. Then, on the Action Pane, open the **Rebate workbench** tab and, in the **Processing** group, select **Purge**.
4. Select **OK** to delete the unposted transactions.

## Cancel a posted provision

After you've processed and posted a provision, follow these steps to cancel the selected posted provision transactions:

1. Go to **Rebate management \> Rebate management deals \> Rebate workbench**
2. Set the **Show** field to *Posted*.
3. Find and select the provision transactions to be cancelled. Then, on the Action Pane, open the **Rebate workbench** tab and, in the **Processing** group, select **Cancel provision**.
4. Select **OK** to reverse the transactions.

These provision reversals will also be visible in the relevant [Rebate management journals](#review-journals).
