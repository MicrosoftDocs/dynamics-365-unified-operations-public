--- 
# required metadata 
 
title: Create a free text invoice template
description: This procedure demonstrates how to create a free text invoice template. 
author: abruer
ms.date: 02/15/2022
ms.topic: article 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a free text invoice template

[!include [banner](../includes/banner.md)]

For this walkthrough, use the USMF demo company. This procedure is intended for the user who is responsible for managing and processing A/R invoices.

## Create a template

1. Go to **Accounts receivable > Invoices > Recurring invoices > Free text invoice templates**.
    * Use this page to create free text invoice templates that can include invoice lines, charges, an accounting distribution template, and ledger account information.  
2. Click **New** to create a new free text invoice template.
3. In the **Template name** field, type a value.
    * ‘Template name’ uniquely identifies a free text invoice template. No two templates can have the same ‘Template name’.  
4. In the **Description** field, enter a description of the template.
5. Expand the **Invoice lines** tab.
6. In the **Description** field, enter a description of the invoice line.
7. In the **Main account** field, select a revenue account.
    * You can select the offset transaction account of a customer credit for the total invoice amount in the **Customer posting profiles** page.  
8. In the **Sales tax group** field, click the drop-down button to open the lookup.
    * The sales tax group for the current invoice line is the default sales tax group for the customer account.  
9. In the list, click the link in the selected row.
10. In the **Item tax group** field, select the item sales tax group for the current invoice line.
11. In the list, click the link in the selected row.
12. In the **Unit price** field, enter or view the price per unit for the invoice line
    * This amount is multiplied by the **Quantity** field to determine the invoice line amount.  
13. Add a new line to free text invoice template.
14. In the **Description** field, enter a description of the invoice line.
15. In the **Main account** field, select a revenue account.
    * You can select the offset transaction account of a customer credit for the total invoice amount in the **Customer posting profiles** page.  
16. In the **Sales tax group** field, click the drop-down button to open the lookup.
    * The sales tax group for the current invoice line is the default sales tax group for the customer account.  
17. In the list, click the link in the selected row.
18. In the **Item sales tax group** field, click the drop-down button to open the lookup.
    * The item sales tax group for the current invoice line.  
19. In the list, click the link in the selected row.
20. Enter or view the number of units for the invoice line.
    * This number is multiplied by the value in the Unit price field to determine the invoice line amount.  
21. Enter or view the price per unit for the invoice line. 
    * This amount is multiplied by the value in the **Quantity** field to determine the invoice line amount.  
22. View and modify the accounting distributions for an individual line and any child lines.
    * Accounting distributions define how an amount will be accounted for, such as how the revenue, tax, or charges will be accounted for on a free text invoice.  
23. Update the accounting distributions for the selected invoice line.
24. Click **Close**.

## Save a free text invoice as a template
You can also save an existing free text invoice as a template. When you select **Save to template** from the **Invoice** tab, provide a name and a description for the template. If a template with the name already exists, you will see a notification that a template with that name already exists. You can still click on **Ok** to replace it. 


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
