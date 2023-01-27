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
Billing schedules use the standard sales order process to bill customers. Sales orders are created and can be invoiced automatically using Generate invoice. 

To bill a customer for the recurring charges setup on the Billing schedule lines, from the Billing schedules page, select Billing schedule and Generate invoice. In the **General** fastTab you can filter the billing schedules to be included by the **Start date** or **End date**. Leave the **From date** field blank to select all billing schedule lines until the To date. Set **Exclude zero consumption** to Yes to not include usage type billing schedule lines with zero consumption, which have 0.00 net amount, in the sales order lines. Set this to No to include the 0.00 net amount line on the sales order. 
On the Invoice processing fastTab the **Invoice transaction type** will default from the billing schedule header as Sales order or Free text invoice. 

Select the **Posting option**  
   -   **Create sales order** only creates the sales order(s) for the billing schedule lines
   -   **Show Posting invoice or Create invoice proposal page** creates the sales order and then displays the Posting invoice page. You can review and then post the invoice. The Create invoice proposal page displays if the billing schedule line (and sales order) has a project ID. 
   -   **Create free text invoice** creates the free text invoice and is only used when the Invoice transaction type is Free text invoice
   -   **Post invoice automatically** creates the sales order and posts the invoice automatically

Set **Don't print child items** to **Yes** if you want to suppress the child items when using revenue split on the billing schedule lines. Select **No** to print the parent and child items when using revenue split. 

In the **Records to include** fastTab the Billing schedule defaults the selected Billing schedule when invoicing only one Billing schedule. Use the Filter button to change the Billing schedule range or Project ID range (if a project is used on the billing schedule). 

Select **View billing schedules** to review the Billing schedules available to bill to a customer. To remove any lines that you do not want to invoice at this time select one more lines and then the **Remove selected** button. Any remaining lines will then be billed. 

## Consolidation
Use the options in the **Consolidation** fastTab to combine multiple billing schedule lines when creating the sales order. 
   -   Consolidate all periods - Combines multiple billing periods for the same line item into one line on the sales order. 

