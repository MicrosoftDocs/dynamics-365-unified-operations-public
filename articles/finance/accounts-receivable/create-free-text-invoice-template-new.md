--- 
title: Create a free text invoice template
description: This procedure demonstrates how to create a free text invoice template, including a step-by-step process that details creating a template.
author: twheeloc
ms.author: shpandey
ms.topic: how-to
ms.date: 08/05/2026
ms.custom:
ms.reviewer: twheeloc 
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form:  
ms.dyn365.ops.version: AX 7.0.0 
---

# Create a free text invoice template

[!INCLUDE [banner](../includes/banner.md)]

For this walkthrough, use the USMF demo company. This procedure is intended for the user responsible for managing and processing A/R invoices.

## Create a template

1. Go to **Accounts receivable > Invoices > Recurring invoices > Free text invoice templates**.
    * Use this page to create free text invoice templates that can include invoice lines, charges, an accounting distribution template, and ledger account information.  
1. Select **New** to create a new free text invoice template.
1. In the **Template name** field, enter a value.
    * The template name uniquely identifies a free text invoice template. No two templates can have the same template name.  
1. In the **Description** field, enter a description of the template.
1. Expand the **Invoice lines** tab.
1. In the **Description** field, enter a description of the invoice line.
1. In the **Main account** field, select a revenue account.
        * On the **Customer posting profiles** page, select the offset transaction account of a customer credit for the total invoice amount.    
1. In the **Sales tax group** field, select the drop-down button to open the lookup.
    * The sales tax group for the current invoice line is the default sales tax group for the customer account.  
1. In the list, select the link in the selected row.
1. In the **Item tax group** field, select the item sales tax group for the current invoice line.
1. In the list, select the link in the selected row.
1. In the **Unit price** field, enter or view the price per unit for the invoice line.
    * This amount is multiplied by the **Quantity** field to determine the invoice line amount.  
1. Add a new line to free text invoice template.
1. In the **Description** field, enter a description of the invoice line.
1. In the **Main account** field, select a revenue account.
        * On the **Customer posting profiles** page, select the offset transaction account of a customer credit for the total invoice amount.    
1. In the **Sales tax group** field, select the drop-down button to open the lookup.
    * The sales tax group for the current invoice line is the default sales tax group for the customer account.  
1. In the list, select the link in the selected row.
1. In the **Item sales tax group** field, select the drop-down button to open the lookup.
    * The item sales tax group for the current invoice line.  
1. In the list, select the link in the selected row.
1. Enter or view the number of units for the invoice line.
    * This number is multiplied by the value in the **Unit price** field to determine the invoice line amount.  
1. Enter or view the price per unit for the invoice line.
    * This amount is multiplied by the value in the **Quantity** field to determine the invoice line amount.  
1. View and modify the accounting distributions for an individual line and any child lines.
    * Accounting distributions define how an amount is accounted for, such as how the revenue, tax, or charges are accounted for on a free text invoice.  
1. Update the accounting distributions for the selected invoice line.
1. Select **Close**.

## Save a free text invoice as a template

You can also save an existing free text invoice as a template. When you select **Save to template** from the **Invoice** tab, enter a name and a description for the template. If a template with the same name already exists, you see a notification. You can still select **OK** to replace it.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
