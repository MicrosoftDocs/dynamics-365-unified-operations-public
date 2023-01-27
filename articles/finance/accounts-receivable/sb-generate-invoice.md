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

Billing schedules use the standard sales order process to bill customers. Sales orders are created and can be invoiced automatically using Generate invoice. 

To bill a customer for the recurring charges setup on the Billing schedule lines, from the Billing schedules page, select Billing schedule and Generate invoice. In the **General** fastTab you can filter the billing schedules to be included by the **Start date** or **End date**. Leave the **From date** field blank to select all billing schedule lines until the To date. Set **Exclude zero consumption** to Yes to not include usage type billing schedule lines with zero consumption, which have 0.00 net amount, in the sales order lines. Set this to No to include the 0.00 net amount line on the sales order. 
On the Invoice processing fastTab the **Invoice transaction type** will default from the billing schedule header as Sales order or Free text invoice. 

-  Select the **Posting option**  
   -   **Create sales order** only creates the sales order(s) for the billing schedule lines.
   -   **Show Posting invoice or Create invoice proposal page** creates the sales order and then oepns the Posting invoice page. You can review and manually post the invoice or save it and post it at a later time. When a project ID exists for any of the lines, a project invoice proposal is created for the sales order.  
   -   **Create free text invoice** creates the free text invoice and is only used when the **Invoice transaction type** is **Free text invoice**.
   -   **Post invoice automatically** creates the sales order and posts the invoice automatically. When a project ID exists for any of the lines, a project invoice proposal is created and then posted. 

Specify the date to create the invoice in the **Invoice date**. The default date is the session date for Microsoft Dynanmics 365 Finance. When the **Posting option** is **Create slaes order**, the invoice date is not applicable and cannot be edited. 

Set **Don't print child items** to **Yes** if you want to suppress the child items when using revenue split on the billing schedule lines. All child items are hidden from the sales invoice and only the parent item appears on the invoice. If the net amount of the (hidden) child items has a non-zero sum, the net amount of the parent line shows a summary of the child lines. Select **No** to print the parent and child items when using revenue split. All child items appear below the parent item on the sales invoice. The net amount for each child item appears on the invoice. This only can only be used when all (parent and child) items in a revenue split are included on the invoice. 

In the **Records to include** fastTab the Billing schedule defaults the selected Billing schedule when invoicing only one Billing schedule. Use the Filter button to change the Billing schedule range or Project ID range (if a project is used on the billing schedule). 

Select **View billing schedules** to review the Billing schedules available to bill to a customer. To remove any lines that you do not want to invoice at this time select one more lines and then the **Remove selected** button. Any remaining lines will then be billed. 

## Consolidation
Use the options in the **Consolidation** fastTab to combine multiple billing schedule lines when creating the sales order. 
Set **Consolidate all periods** to **Yes** to combine multiple billing periods for the same line item into one line on the sales order. For example, a billing schedule line item has a billing frequency set to monthly from January - December. The quantity is 1 and billing amount is 100.00. The invoice is created for the first three periods (January to March). The sales order is created with one line, quantity of 3, net amount of 300.00. If set to **No** then the sales order will have three lines, one for each billing period, quantity of 1 and net amount of 100.00. 
Set **Consolidate by customer** to **Yes** to combine billing schedules lines if the Customer ID, document ID, customer reference, project ID (if using), and currency ID are the same. Terms of payment, payment method or payment schedule. 
Set **Consolidate by item** to **Yes** to combine billing schedles lines if the items and project ID (if using) are the same. If any items belong to item groups that have a **Number of top lines** greater than zero on the **Item Group Setup** page, this option is automatically set to **No**. 
Set **Split by item group** to **Yes**

Use the **Preview invoice** button to see a preview of all sales order lines to be created. Keep in mind that all item group splitting and all consolidations have occurred. Also, the top billing feature has been applied to the top items. The sales number available in the preview is a temporary number for the purpose of the preview and contains the prefix **Preview**. The actual sales order number is generated at the time the invoice for the sales order is created. 

The order for the lines that appear in the list are based on whether the top billing feature is used. When the top billing feature is used, the lines appear in this order: 
1. Descending order according to the net amount, where the largest net amount is at the top
2. Ascending order according to the end date, where the earliest date is at the top and the furthest future date is at the bottom
3. Ascending order by the original billing schedule number
4. Ascending order by the line number

When the top billing feature is not used, the lines appear in ths order:
1. Ascending order according to the end date, where the earliest date is at the top and the furthest future date is at the bottom. 
2. Ascending order by the original billing schedule number
3. Ascending order by the line number
