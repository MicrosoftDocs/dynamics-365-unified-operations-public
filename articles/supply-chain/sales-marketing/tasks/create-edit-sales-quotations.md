--- 
# required metadata 
 
title: Create and edit sales quotations
description: This procedure demonstrates how to create and update a sales quotation. 
author: Henrikan
ms.date: 06/26/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SalesQuotationListPage, SalesCreateQuotation, SalesQuotationTable, SalesQuotationTotals, SalesQuotationPriceSimulation, SalesQuotationEditLines, SrsReportViewerForm, smmSetNumSeqIfManual, CustTable, SalesTable, CustQuotationConfirmationJournal, CustQuotationJournal, CustSalesLines, SalesQuotationCopying, SalesQuotationDeleteQuotations, SalesQuotationListPagePreviewPane, SalesQuotationTypeGroup   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: henrikan
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create and edit sales quotations

[!include [banner](../../includes/banner.md)]

This procedure demonstrates how to create and update a sales quotation. You can run this procedure on your own data or in demo data company USMF.


## Create a sales quotation
1. Go to **Sales and marketing > Sales quotations > All quotations**.
2. Click **New**.
3. In the **Account type** field, select 'Prospect'.
4. In the **Prospect** field, enter or select a value.
5. Expand the **General** section. Because you chose to create a quotation from the Sales and Marketing area, the type is automatically set to 'Sales quotation'. To create a quotation for a project you must access it from the **Project management and accounting** module.
6. Click **OK**. The fields and actions on the quotation lines are very similar to the ones on the sales order lines.   Like sales orders, quotations can be created for a specific item or, when item number is not known or does not exist at the time of quotation creation, quotations can be created for a sales category.     
7. In the **Item** field, enter or select a value.
8. In the **Site** field, type a value.
9. In the **Quantity** field, enter a number. If there are valid trade agreements for the item selected on the line, the applicable price and discounts will be automatically copied to the quotation line. Make sure that the Unit price field contains a value and you can also enter discount values if you want to. 
10. Click **Save**.
11. On the **Action Pane**, click **Sales quotation**.
12. Click **Totals**.
13. Click **OK**.
14. Select the sales quotation line.
15. On the **Action Pane**, click **Quotation**.
16. Click **Price simulation**.
    - In the **Run price simulation** page you can experiment with adjusting the expected revenue or profitability of your quotation based on the desired unit price, discount amount, discount percentage, total amount, margin, or contribution ratio. When you are satisfied with the target figures, you apply the suggestion to the quotation line, and its price-related fields will be updated accordingly.  
    - You can create as many price simulations as you wish. When you click **New**, the price conditions from the current quotation line are copied to the page. You can then modify values in any of the price-related fields to the target ones. A change in one of the fields will trigger recalculation in all the other fields. In order for the system to calculate the sales margin and contribution ratio, the product's unit cost has to be known. Use the Simulated prices tab for a detailed view of the original prices, proposed changes and their effect on the quotation totals. As a general rule, when a simulation that sets a new amount is applied to the quotation line, the system recalculates and enters a new value in the Unit price field. If the simulation is based on a new margin or a new contribution ratio, only the Net amount field is updated, and the Unit price is blank. In both cases, any discounts that were on the quotation line before simulation will be deleted.
17. On the **Action Pane**, click **Quotation**.
18. Click **Send quotation**.
19. Select 'Yes' in the **Print quotation** field.
20. Click **OK**. The report may take a minute to generate. Don't close the page until it does so.

## Update a sales quotation
1. Go to **Sales and marketing > Sales quotations > All quotations**.
2. On the **Action Pane**, click **Follow up**.
3. Click **Convert to customer**.
4. In the **Customer account** field, type a value.
5. Click **Check**. Make sure you see a message that the account number you typed in is free to use.  
6. Click **OK**. The system has now created a new customer account for the prospect on the quotation.  
7. Close the page.
8. On the **Action Pane**, click **Follow up**.
9. Click **Confirm**.
10. In the **Reason** field, enter or select a value.
11. Click **OK**.
12. On the **Action Pane**, click **General**.
13. Click **Sales orders**.
14. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]