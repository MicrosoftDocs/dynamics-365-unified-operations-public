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
ms.dyn365.ops.version: 10.0.18
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

You can create the sales orders or purchase orders that have source transactions either before or after you create an applicable Rebate management deal.

You can set up each deal line so that it automatically creates a rebate provision by posting the delivery or invoice for a sales order or purchase order. Set the **Transaction type** field for the deal line to *Delivery* or *Invoice*, and set the **Process at posting** option to *Yes*. If the **Transaction type** field is set to *Order*, processing at posting is disabled. For source transactions that were created after a deal was activated, you can still process the provision as described in the [Process Rebate management deals](#process-deals) section later in this topic.

### Enable price details

Before you can create source transactions, you must enable the **Enable price details** option for account receivables.

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. On the **Prices** tab, on the **Price details** FastTab, set the **Enable price details** option to *Yes*.

### Create a source transaction

To create a source transaction, follow these steps.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Select **New**.

    To mimic the way that rebate claims are generated, you must now create a sales order where the product and quantity qualify the customer for a rebate.

1. In the **Customer account** field, enter or select a customer that will qualify for a rebate deal.
1. Select **OK** to create the sales order.
1. On the **Sales order lines** FastTab, add a line, and set the following fields for it:

    - **Item number** – Specify an item that qualifies for a rebate.
    - **Quantity** – Specify a quantity that qualifies for a rebate deal that includes a line where the **Basis** field is set to *Quantity*.
    - **Unit price** – Specify a price that qualifies for a rebate deal that includes a line where the **Basis** field is set to *Value*.
    - **Site** – Select a site where the product is available, and that qualifies for a rebate deal.
    - **Warehouse** – Select a warehouse where the product is available, and that qualifies for a rebate deal.

1. On the **Sales order lines** FastTab, on the toolbar, select **Sales order line \> Price details**. This command is available only if you enabled price details as described in the previous section.
1. On the **Price details** page, select the **Rebate management** FastTab. This FastTab lists all the rebate management deals that apply to the current order line and shows the estimated rebate amount in the order's currency. Note that the amounts are only estimates of the future rebate claims. The actual rebate amounts might differ. Here are some of the factors that might affect the actual amounts:

    - The total sales volume that the customer achieved under a periodic rebate agreement.
    - Whether the customer returned all quantities or partial quantities.
    - Whether the applicable sales order achieved the transaction type (*Order, Delivery*, or *Invoice*) that is defined for the Rebate management deal.
    - The deal's **Output** value. A blank rebate amount will be shown for deals where the **Output** field is set to *Item*.

1. On the **Detail** FastTab, notice that the **Margin estimation** section includes the following fields. These fields are added by Rebate management. All of them show values per unit (whereas the fields on the **Rebate management** FastTab show total values for the line).

    - **Rebate management rebate amount** (sales orders only)
    - **Rebate management royalty amount** (sales orders only)
    - **Rebate management vendor rebate amount** (sales orders and purchase orders)

1. Close the **Price details** page.
1. If the sales order should not qualify for the rebates that you just viewed, follow these steps to exclude rebates. (However, you usually won't exclude rebates.)

    1. On the **Sales order lines** FastTab, select the relevant line.
    1. On the **Line details** FastTab, on the **Price and discount** tab, set the **Exclude from rebate management** option to *Yes*. This option doesn't apply to purchase orders. Furthermore, only customer rebates are excluded when this option is set to *Yes*. Customer royalty rebates and vendor rebates still apply.

1. On the Action Pane, on the **Pick and pack** tab, in the **Generate** group, select **Post packing slip**.
1. On the **Parameters** FastTab, in the **Quantity** field, select *All*.
1. Select **OK**.
1. If you're prompted to confirm the operation, select **OK**.
1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. On the **Parameters** FastTab, in the **Quantity** field, select *All* or *Packing slip*.
1. Select **OK**.
1. If you're prompted to confirm the operation, select **OK**.

## <a name="process-deals"></a>Process Rebate management deals

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

### Process deals by using the rebate workbench

Instead of processing specific deals or deal lines, you can use the *rebate workbench* to process multiple deals at the same time. You can optionally apply record filters and/or set up a recurring schedule. You don't have to select any rows. The system will process all lines that meet the date and filter requirements that you set up.

To process deals by using the rebate workbench, follow these steps.

1. Go to **Rebate management \> Rebate management deals \> Rebate workbench**.
1. On the Action Pane, on the **Rebate workbench** tab, in the **Processing** group, select one of the following commands:

    - **Process \> Provision** – Provision a set of accruals for each relevant deal line, but don't post the accruals.
    - **Process \> Rebate management** – Process a series of transactions that provide the value of the rebate for each deal line.
    - **Process \> Write off** – Process the variance between provision and rebate management that is posted for each source transaction per rebate deal and specified period.

1. In the **Rebate management** dialog box, in the **Period** section, set the **From date** and **To date** fields to define the date range for the calculation.
1. In the **Guarantee period** section, set the **From date** and **To date** fields to define the date range for guarantees for the calculation.
1. On the **Records to include** FastTab, you can set up filters to limit the set of deals that the batch job will process. These settings work in the same way that they work for other types of batch jobs.
1. On the **Run in the background** FastTab, you can set up batch processing and scheduling options as required. These settings work in the same way that they work for other types of batch jobs.
1. Select **OK** to run and/or schedule the calculation.

## View and edit Rebate management transactions

When you process one or more deals, the system creates transactions that you can view and, perhaps, edit before you post them.

### View and edit Rebate management transactions by using the rebate deals list page

To view and edit Rebate management transactions using the rebate deals list page, follow these steps.

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

### View and edit Rebate management transactions by using the rebate workbench

To view and edit Rebate management transactions by using the rebate workbench, follow these steps.

1. Go to **Rebate management \> Rebate management deals \> Rebate workbench**.
1. Set the **Show** field to *Not posted*.
1. The **Rebate workbench** page shows a list of the transactions. Each transaction provides relevant details. These details vary, depending on the transaction type. You can perform the following actions on this page:

    - To view more information about any transaction, select it, and then select the **General**, **Financial dimension**, or **Dimension** tab.
    - If you're using a claims process, you can mark transactions as either claimed or unclaimed. Select the relevant rows, and then, on the Action Pane, on the **Rebate workbench** tab, select one of the following commands. (You enable claims processes on the [**Rebate management parameters**](rebate-management-parameters.md) page.)

        - **Set claimed** – Mark the selected transactions as claimed.
        - **Set unclaimed** – Mark the selected transactions as unclaimed.

    - To post the claim for one or more lines, select the relevant lines. Then, on the Action Pane, on the **Rebate workbench** tab, select **Post**. The **Post** button is available for provision, rebate, and write-off transactions. In the **Post** dialog box, the **From date** and **To date** fields are automatically set. Set the **Posting date** field, and then select **OK**.
    - To adjust the amount that is shown for any open or unposted transaction, select the transaction, and then follow one of these steps:

        - Edit the value in the **Corrected amount** field.
        - On the Action Pane, on the **Rebate workbench** tab, select **Set correction**. Then, in the drop-down dialog box that appears, in the **Corrected amount** field, enter a value.

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

### Post transactions by using the rebate workbench

After you've processed provision, rebate, or write-off transactions, follow these steps to use the rebate workbench to review and post the generated transactions for one or more specific transaction lines for all deals.

1. Go to **Rebate management \> Rebate management deals \> Rebate workbench**.
1. In the grid, select the row for each transaction line that you want to post. You can select unposted provision, rebate, and/or write-off transactions. The following rules apply:

    - The system will also post all lines that have the same **Rebate transaction number** value as the lines that you select.
    - The system won't post any lines of the *Rebate* transaction type that aren't marked as claimed.
    - If you select lines that have already been posted, the system will skip the posted lines.
    - The **Post** button is available only if you select at least one unposted line.

1. On the Action Pane, on the **Rebate workbench** tab, in the **Processing** group, select **Post**.
1. In the **Post** dialog box, set the **Posting date** field. The **From date** and **To date** fields are automatically set, based on the earliest **From date** value and the latest **To date** value for the selected rows.
1. Select **OK** to post the transactions.

## <a name="review-journals"></a>Review Rebate management journals

After your transactions have been posted, you can review the resulting journals, documents, or items. Target transactions for rebates and royalties are based on the payment type that is set in the posting profile and the rebate's output type. For example, if the rebate output is set to *Item*, a sales order will be created for a customer rebate, and a purchase order will be created for a vendor rebate. These orders can be viewed via the target transactions. Alternatively, if the payment is set up to use Accounts payable, a vendor invoice for the vendor that is set up on the customer will be created for customer rebates.

### Review journals by using the rebate deals list page

To review the journal entries that are associated with a Rebate management deal, follow these steps.

1. Open the appropriate [rebate deals list page](rebate-management-deals.md) for the type of deal that you want to work with.
1. Select the deal to inspect journal entries for.
1. On the Action Pane, on the **Rebate management deals** tab, in the **Transactions** group, select either **Transactions** or **Guarantee transactions**, depending on the type of transactions that you want to look at.
1. Set the **Show** field to *All* or *Posted*.
1. Find and select the transaction collection that you want to inspect, and then, on the Action Pane, select one of the following buttons. (These buttons are available only when relevant postings exist for the selected transaction collection.)

    - **Target transactions** – Review relevant journals and other types of documents that were generated by the selected deal.
    - **Items** – Review relevant sales orders or purchase orders that were generated by the selected deal.

1. A list of relevant journals, documents, or items appears. To view more information about any journal, document, or item, select its row, and then, on the Action Pane, select **View details**.

### Review journals by using the rebate workbench

To review journals by using the rebate workbench, follow these steps.

1. Go to **Rebate management \> Rebate management deals \> Rebate workbench**.
1. Set the **Show** field to _All_ or _Posted_.
1. Find and select the line that you want to inspect. Then, on the Action Pane, on the **Rebate workbench** tab, in the **View** group, select **Target transactions**. This button is available only if relevant postings exist for the selected line.
1. A list of relevant journals, documents, or items appears. To view more information about any journal, document, or item, select its row, and then, on the Action Pane, select **View details**.

## Rebate management transactions on the deduction workbench

When you post a Rebate management transaction that has one of the following **Payment type** values, the system creates a customer deduction journal or a free text invoice for the relevant customer account:

- Customer deductions
- Tax invoice customer deductions
- Trade spending
- Reporting

After a target transaction is created and posted, it will be available as an open transaction on the **Deduction workbench** page (**Sales and marketing \> Trade allowances \> Deductions \> Deduction workbench**). Open transactions have a **Claim type** value of *Rebate management*, and a **Rebate transaction number** value is available to enable traceability. The date is set to the posting date of the Rebate management target transaction. To use the deduction workbench to settle open transactions to existing deductions for the same customer account, select **Maintain \> Match** on the Action Pane.

For more information, see [Manage deductions using the deduction workbench](deduction-workbench.md).

## Purge unposted transactions

After you've processed provision, rebate, or write-off transactions, follow these steps to purge selected unposted transactions.

1. Go to **Rebate management \> Rebate management deals \> Rebate workbench**.
2. Set the **Show** field to *Not posted*.
3. Find and select the transactions to delete. Then, on the Action Pane, on the **Rebate workbench** tab, in the **Processing** group, select **Purge**.
4. Select **OK** to delete the unposted transactions.

## Cancel a posted provision

After you've processed and posted a provision, follow these steps to cancel the posted provision transactions.

1. Go to **Rebate management \> Rebate management deals \> Rebate workbench**.
2. Set the **Show** field to *Posted*.
3. Find and select the provision transactions to cancel. Then, on the Action Pane, on the **Rebate workbench** tab, in the **Processing** group, select **Cancel provision**.
4. Select **OK** to reverse the transactions.

These provision reversals will also be visible in the relevant [Rebate management journals](#review-journals).
