--- 
# required metadata 
 
title: Set up accounts payable invoice matching validation
description: This recording uses the USMF demo company. 
author: abruer
manager: AnnBe 
ms.date: 11/14/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: abruer
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---

# Set up accounts payable invoice matching validation

[!include[task guide banner](../../includes/task-guide-banner.md)]

This recording uses the USMF demo company. The accounts payable manager or accounting manager role would perform these steps. Before you begin, make sure that the Invoice matching configuration key is selected. If your legal entity tracks expenses, such as freight, by using charges, make sure that the Charges configuration key is selected.  Accounts payable invoice matching is the process of matching vendor invoice, purchase order, and product receipt information. Differences among these documents are called matching discrepancies. Matching discrepancies are compared with the tolerances that are specified. If a matching discrepancy exceeds the tolerance percentage or amount, match variance icons are displayed in the Vendor invoice form and in the Invoice matching details form.

1. Go to Accounts payable > Setup > Accounts payable parameters.
2. Click the Invoice validation tab.
3. Check or uncheck the Enable invoice matching validation checkbox.
    * Select whether approval is required before an invoice that contains discrepancies for invoice matching can be posted. If this is set to Allow with warning, visual indication will display when a discrepancy for invoice matching exceeds the tolerance. However, you will be able to post the invoice. To use workflows together with invoice matching validation, make sure that the Post invoice with discrepancies field is set to Allow with warning to avoid having to approve multiple times.  
    * In the Automatically update invoice header match status field, select whether matching will be performed automatically during invoice data entry by the system. The recommended setting is Yes, unless you are experiencing data entry performance concerns. Disabling automatic updates may enable faster system performance because the invoice matching validation will be bypassed during data entry. The data entry clerk will need to manually update the invoice’s match status to see the invoice matching validation results when this is set to No.  
4. Toggle the expansion of the Invoice totals matching section.
5. Check or uncheck the Match invoice totals checkbox to match actual invoice totals with expected totals.
    * Select whether an icon is displayed if a discrepancy for invoice matching exceeds the tolerance. You can select to display the icon when a positive discrepancy exceeds the tolerance, or when either a positive or a negative discrepancy exceeds the tolerance.  
    * For example, the tolerance is 5 percent, and the total invoice amount on the purchase order is 100.00. Therefore, a price match icon is displayed if the total invoice amount on the invoice exceeds 105.00. If you select If greater than or less than tolerance, the icon is also displayed if the invoice amount is less than 95.00.  
6. In the Invoice totals tolerance percentage field, enter a number.
7. Toggle the expansion of the Price and quantity matching section.
    * In the Line matching policy field, select a value to be used as the default policy for the legal entity that you are working with. “Not required” means there is no verification of individual invoice line prices to purchase order price or invoice quantities to packing slip quantities required. “Two-Way Match” means that the verification of invoice lines is required but only the purchase order and the supplier’s invoice documents are involved in the verification. The product receipt isn’t factored into the matching validations. “Three-Way Match” means that the invoice net unit price will be compared to the purchase order’s net unit price and the matching product receipt quantity will be compared to the invoice quantity.  
    * If you use a line matching policy of Two-way matching or Three-way matching, you can set up price tolerance percentages for your legal entity, items, and vendors on the Item price tolerance page. When vendor invoices are compared with the information on purchase orders, the applicable price tolerance percentage is searched for.  
8. In the Line matching policy field, select an option.
    * To allow a different level of matching to be applied for an item, vendor, vendor and item combination, or purchase order line, select a value in the Allow matching policy override field. The legal entity line matching policy can be overridden for a specific vendor, item, or vendor and item combination in the Matching policy page.  
    * To match price totals for line items on invoices, select a value in the Match price totals field. This type of matching is useful when the vendor sends multiple invoices for the same purchase order line. You can compare price information for the net amount of each line on the invoice and all pending and previously posted invoice lines, with the net amount of the corresponding purchase order line.  
9. In the Match price totals field, select an option.
10. In the Purchase price total tolerance field, enter a number.
11. Toggle the expansion of the Charges matching section.
12. To match actual charges with expected charges, based on information on the purchase order, select the Match charges check box.
13. Close the page.

