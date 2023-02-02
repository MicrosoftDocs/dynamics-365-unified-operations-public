---
# required metadata

title: Generate invoices from billing schedules
description: This article describes how to create invoices from billing schedules in Subscription billing.
author: JodiChristiansen
ms.date: 01/27/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24

---
# Generate invoices from billing schedules

> [!NOTE]
> Billing schedules with projects are available in Microsoft Dynamics 365 Finance version 10.0.32 and later.

Billing schedules use the standard sales order process to bill customers. Sales orders are created and can be automatically invoiced by selecting **Generate invoice**.

To bill a customer for the recurring charges, follow these steps.

1. On the **Billing schedules** page, select **Billing schedule \> Generate invoice**.
2. Set up the billing schedule lines. 

On the **General** FastTab, you can filter the billing schedules that are included by start date or end date. Leave the **From date** field blank to select all billing schedule lines until the end date that's selected in the **To date** field. 

Set the **Exclude zero consumption** option to **Yes** to exclude usage-type billing schedule lines that have zero consumption and therefore a net amount of 0.00 from the sales order lines. Set it to **No** to include lines that have a net amount of 0.00 on the sales order. 

On the **Invoice processing** FastTab, the default value of the **Invoice transaction type** field (**Sales order** or **Free text invoice**) is taken from the billing schedule header. 

In the **Posting option** field, select one of the following values:

- **Create sales order** – Create one or more sales orders for the billing schedule lines.
- **Show Posting invoice or Create invoice proposal page** – Create the sales order, and open the **Posting invoice** page, where you can review and manually post the invoice, or save it and post it later. If a project exists for any line, a project invoice proposal is created for the sales order.
- **Create free text invoice** – Create the free text invoice. This value is used only when the **Invoice transaction type** field is set to **Free text invoice**.
- **Post invoice automatically** – Create the sales order, and automatically post the invoice. If a project exists for any line, a project invoice proposal is created and then posted. 

In the **Invoice date** field, specify the date to create the invoice. The default value is the session date for Dynamics 365 Finance. If the **Posting option** field is set to **Create sales order**, the invoice date isn't applicable and can't be edited. 

Set the **Don't print child items** option to **Yes** to suppress child items if revenue splitting is used on the billing schedule lines. In this case, only the parent item appears on the sales invoice. All child items are hidden. If the net amount of the (hidden) child items is a non-zero sum, the net amount of the parent line shows a summary of the child lines. Set this option to **No** to print the parent and child items when revenue splitting is used. In this case, all child items appear below the parent item on the sales invoice. The net amount for each child item appears on the invoice. This option can be used only when all items (parent and child) in a revenue split are included on the invoice. 

On the **Records to include** FastTab, if you're invoicing only one billing schedule, the **Billing schedule** field is set to the selected billing schedule by default. Use the **Filter** button to change the **Billing schedule** range or **Project** range. 

Select **View billing schedules** to review the billing schedule lines that are available to bill to a customer. If you don't want to invoice one or more of the lines at this time, select the lines, and then select **Remove selected**. All remaining lines will be billed when you select **Generate all**.

Use the **Batch** button to add the lines to a batch job that will be processed later.

## Consolidation

Use the options on the **Consolidation** FastTab to combine multiple billing schedule lines when you create the sales order.

- **Consolidate all periods** – Set this option to **Yes** to combine multiple billing periods for the same line item into one line on the sales order. For example, a billing schedule line item has a monthly billing frequency from January through December. The quantity is 1, and the billing amount is 100.00. If the first three periods (January through March) are selected, the sales order that's created will have one line that has a quantity of 3 and a net amount of 300.00. If this option is set to **No**, the sales order will have three lines, one for each billing period, and each line will have a quantity of 1 and a net amount of 100.00. 
- **Consolidate by customer** – Set this option to **Yes** to combine billing schedules lines if the customer ID, document ID, customer reference, project (if it's used), and currency ID are the same. Terms of payment, payment method, and payment schedule must also be the same to consolidate by customer. 
- **Consolidate by item** – Set this option to **Yes** to combine billing schedule lines if the items and project are the same. If any items belong to item groups where the value of the **Number of top lines** field on the **Item group setup** page is more than 0 (zero), this option is automatically set to **No**. 
- **Split by item group** – Set this option to **Yes** to use the top billing feature. For more information, see the [Top billing items](#top-billing-items) section later in this article. 

Select **Preview invoice** to show a preview of all sales order lines that will be created. Remember that all item group splitting and all consolidations have occurred, and the top billing feature has been applied to the top items. The sales number that's shown in the preview is temporary and contains the prefix "Preview." The actual sales order number will be generated when the sales order is created. 

The order of the lines in the list depends on whether the top billing feature is used. If the feature is used, the lines appear in this order:

1. Descending order by net amount (The largest net amount is at the top.)
2. Ascending order by end date (The earliest date is at the top, and the latest future date is at the bottom.)
3. Ascending order by original billing schedule number
4. Ascending order by line number

If the top billing feature isn't used, the lines appear in this order:

1. Ascending order by end date (The earliest date is at the top, and the latest future date is at the bottom.)
2. Ascending order by original billing schedule number
3. Ascending order by line number

## Different bill-to addresses

Sales orders for billing schedule lines that use different bill-to addresses are processed in the following way:

- If all lines use the same bill-to address, one sales order is created that has all the lines.
- If some lines use a different bill-to address, a separate sales order is created for each bill-to address, and all the appropriate lines appear on the correct sales order.

For example, if one billing schedule has three billing schedule lines, one or more sales order might be created, depending on the number of bill-to addresses:

- **All lines use the same bill-to address and delivery address:** One sales order is created that has three lines.
- **All lines use the same bill-to address, but each uses a different delivery address:** One sales order is created that has three lines.
- **Each line uses a different bill-to address and delivery address:** Three sales orders are created, each of which has one line.
- **Two lines use the same bill-to address, but each uses a different delivery address:** Two sales orders are created. One sales order has two lines, and the other has one line.

The bill-to address appears on the generated pro forma invoice and the sales invoice report.

## Top billing items

To use the top billing feature on a sales invoice, make sure that the **Split by item group** option on the **Generate invoice** page is set to **Yes**. The feature is applied to each invoice, and the most expensive items are determined by the net amount, not the unit price.

The following process is used to determine the top items for invoices that are created from the **Generate invoice** page.

1. All item group splitting and consolidation are done.
2. For each sales order, the following validations occur:

    - The **Split by item group** option must be set to **Yes**.
    - The item group must be in the **Top billing setup** list and must have a value that's more than 0 (zero).

3. After the validations are passed, the top most expensive items are determined based on the net amount. The amounts for these lines remain unchanged.

    If multiple lines have the same amount, the items that are used for the invoice are randomly selected. For example, the top billing for an item group is **3**, and the net amounts for the top-three items are as follows:

    - **Item A:** $900 
    - **Item B:** $800 
    - **Item C:** $700 
    - **Item D:** $700 
    - **Item E:** $700

    For the $700 amount, one of item C, D, or E is selected at random for inclusion in the top three.

4. None of the remaining items below the top billing are billed, and the unit price and net amount are changed to **0** (zero).

> [!NOTE]
> When the top billing feature is used (that is, one or more lines in the item group setup have a **Number of top lines** value that's more than 0 \[zero\]), the following features are unavailable:
>
> - The revenue splitting functionality in multiple element revenue allocation can't be used.
> - The **Revenue allocation** button isn't available for billing schedules on any page.
> - The unbilled revenue feature can't be used.
> - The **Unbilled revenue** button on the **Billing schedules** page isn't available.
> - On the **Generate invoice** page, the **Consolidate by item** and **Split by item group** options can't work together. (If the **Split by item group** option is set to **Yes**, the **Consolidate by item** option is automatically set to **No** and can't be set to **Yes**.)

## Separating invoices based on item groups

The following setup is required to create separate invoices for renewal schedules, based on item groups.

- As part of the standard setup, items must be assigned to item groups.
- On the **Recurring contract billing parameters** page, the **Unique schedule type** field must be set to **Customer**.
- When invoices are created on the **Sales order** or **Generate invoice** page, the **Split by item group** option must be set to **Yes**.

For billing schedules that have multiple item groups, separate sales orders are created for each item group. 

For lines that use revenue splitting, all child items are on the same sales order as the parent item.
