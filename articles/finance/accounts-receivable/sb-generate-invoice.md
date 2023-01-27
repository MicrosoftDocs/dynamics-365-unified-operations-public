---
# required metadata

title: Subscription billing generate invoice
description: This topic describes how to create invoices from billing schedules in Subscription billing.
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
> Billing schedules with projects was added in version 10.0.32

Billing schedules use the standard sales order process to bill customers. Sales orders are created and can be invoiced automatically using Generate invoice. To bill a customer for the recurring charges setup on the Billing schedule lines, from the Billing schedules page, select Billing schedule and Generate invoice. 

In the **General** fastTab you can filter the billing schedules to be included by the **Start date** or **End date**. Leave the **From date** field blank to select all billing schedule lines until the To date. Set **Exclude zero consumption** to **Yes** to not include usage type billing schedule lines with zero consumption, which have 0.00 net amount, in the sales order lines. Set this to **No** to include the 0.00 net amount line on the sales order. 

On the **Invoice processing** fastTab the **Invoice transaction type** will default from the billing schedule header as Sales order or Free text invoice. 
-  Select the **Posting option**  
   -   **Create sales order** only creates the sales order(s) for the billing schedule lines.
   -   **Show Posting invoice or Create invoice proposal page** creates the sales order and then oepns the **Posting invoice** page. You can review and manually post the invoice or save it and post it at a later time. When a project exists for any of the lines, a project invoice proposal is created for the sales order.  
   -   **Create free text invoice** creates the free text invoice and is only used when the **Invoice transaction type** is **Free text invoice**.
   -   **Post invoice automatically** creates the sales order and posts the invoice automatically. When a project exists for any of the lines, a project invoice proposal is created and then posted. 

Specify the date to create the invoice in the **Invoice date**. The default date is the session date for Microsoft Dynanmics 365 Finance. When the **Posting option** is **Create sales order**, the invoice date is not applicable and cannot be edited. 

Set **Don't print child items** to **Yes** if you want to suppress the child items when using revenue split on the billing schedule lines. All child items are hidden from the sales invoice and only the parent item appears on the invoice. If the net amount of the (hidden) child items has a non-zero sum, the net amount of the parent line shows a summary of the child lines. Select **No** to print the parent and child items when using revenue split. All child items appear below the parent item on the sales invoice. The net amount for each child item appears on the invoice. This can only be used when all (parent and child) items in a revenue split are included on the invoice. 

In the **Records to include** fastTab the Billing schedule defaults the selected Billing schedule when invoicing only one Billing schedule. Use the Filter button to change the Billing schedule range or Project range. 

Select **View billing schedules** to review the Billing schedule lines available to bill to a customer. To remove any lines that you do not want to invoice at this time select one more lines and then the **Remove selected** button. Any remaining lines will then be billed when selecting **Generate all**. Use the Batch button to add the lines to a batch job to be processed later.  

## Consolidation
Use the options in the **Consolidation** fastTab to combine multiple billing schedule lines when creating the sales order. 
Set **Consolidate all periods** to **Yes** to combine multiple billing periods for the same line item into one line on the sales order. For example, a billing schedule line item has a billing frequency set to monthly from January to December. The quantity is 1 and billing amount is 100.00. If the first three periods (January to March) are selected the sales order is created with one line, quantity of 3, net amount of 300.00. If set to **No** then the sales order will have three lines, one for each billing period, quantity of 1 and net amount of 100.00. 

Set **Consolidate by customer** to **Yes** to combine billing schedules lines if the Customer ID, document ID, customer reference, project ID (if using), and currency ID are the same. Terms of payment, payment method or payment schedule. 

Set **Consolidate by item** to **Yes** to combine billing schedles lines if the items and project are the same. If any items belong to item groups that have a **Number of top lines** greater than zero on the **Item Group Setup** page, this option is automatically set to **No**. 

Set **Split by item group** to **Yes** to use the Top billing feature. See **Top billing items** below. 

Use the **Preview invoice** button to see a preview of all sales order lines to be created. Keep in mind that all item group splitting and all consolidations have occurred. Also, the top billing feature has been applied to the top items. The sales number available in the preview is a temporary number for the purpose of the preview and contains the prefix **Preview**. The actual sales order number is generated at the time the sales order is created. 

The order for the lines that appear in the list are based on whether the top billing feature is used. When the top billing feature is used, the lines appear in this order: 
1. Descending order according to the net amount, where the largest net amount is at the top.
2. Ascending order according to the end date, where the earliest date is at the top and the furthest future date is at the bottom.
3. Ascending order by the original billing schedule number.
4. Ascending order by the line number.

When the top billing feature is not used, the lines appear in ths order:
1. Ascending order according to the end date, where the earliest date is at the top and the furthest future date is at the bottom. 
2. Ascending order by the original billing schedule number.
3. Ascending order by the line number.

## Different bill-to addresses
Sales orders for billing schedule lines that use different bill-to addresses are processed as follows:

-   If all lines have the same bill-to address, one sales order with all the lines is created.
-   If the bill-to address is different for some lines, a sales order is created for each bill-to address with all corresponding lines on the correct sales order.

Consider the following example, one billing schedule has three billing schedule lines:

-   All lines use the same delivery and bill-to address: One sales order with three lines is created.
-   All lines use the same bill-to address, but have three different delivery addresses: One sales order with three lines is created.
-   All lines use three different bill-to addresses and delivery address: Three different sales orders, with one line each, are created.
-   Two lines use the same bill-to address, but different delivery addresses: Two different sales orders are created: one sales order has two lines, the other sales order has one line.

The bill-to address appears on the generated pro forma invoice and the sales invoice report.

## Top billing items

To use the top billing feature on a sales invoice, ensure that **Split by item group** is **Yes** on the Generate invoice page. The top items feature is applied to each separate invoice with the most expensive items determined by the net amount, not the unit price.

The process for determining the top items for invoices created from the Generate invoice page is as follows:

1.	All item group splitting and consolidation is performed.
2.	For each individual sales order, the following validations occur
-  The **Split by item group** option is set to **Yes**.
-  The item group is on the Top billing setup list with a value greater than zero (0).
3.	After the validations pass, the top most expensive items are determined based on the net amount.

The amounts for these lines remain unchanged.

If multiple lines have the same amount, the items that are used for the invoice are randomly selected. For example, the top billing for an item group is 3. The net amount for the top 3 items are:

-   Item A = $900 
-   Item B = $800 
-   Item C = $700 
-   Item D = $700 
-   Item E = $700

The top 3 items have the amounts: $900, $800, and $700. For the amount of $700, one of item C, D or E is selected at random to be included in the top 3.

4.	The remaining items below the top billing are not billed and the unit price and net amount are changed to zero (0).

> [!NOTE]
> When the top billing feature is used (one or more lines on the **Item Group Setup** have **Number of top lines** greater than zero), the following features are not available.

-   The revenue splitting functionality in Multiple Element Revenue Allocation cannot be used
-   The Revenue Allocation button for billing schedules on any page is not available
-   The unbilled revenue feature cannot be used
-   The Unbilled revenue button on the Billing Schedules page is not available.
-   On the Generate invoice, the **Consolidate by Item** and the **Split by item group** options cannot work together (Split by item group is Yes, Consolidate by Item is automatically set to No and cannot be changed to Yes). 

## Item group: separating invoices
To be able to create separate invoices for renewal schedules based on item groups, the following setup is needed:

-   As part of the standard Microsoft Dynamics 365 for Finance and Operations setup, items must be assigned to item groups.
-   On the Advanced Recurring Contract Billing Parameters page, Unique schedule type is set to Customer.
-   When creating invoices on the Sales Order or the Invoice Creator pages, set Split by item group to Yes.

For billing schedules with multiple item groups, separate sales orders are created for each item group. 

For lines that use revenue splitting, all child items are on the same sales order as the  parent item.

