--- 
# required metadata 
 
title: Create and edit sales quotations
description: This procedure demonstrates how to create and update a sales quotation. 
author: omulvad
manager: AnnBe 
ms.date: 11/10/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: omulvad
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create and edit sales quotations

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure demonstrates how to create and update a sales quotation. You can run this procedure on your own data or in demo data company USMF.


## Create a sales quotation
1. Go to Sales and marketing > Sales quotations > All quotations.
2. Click New.
3. In the Account type field, select 'Prospect'.
4. In the Prospect field, enter or select a value.
5. Expand the General section.
    * Because you chose to create a quotation from the Sales and Marketing area, the type is automatically set to Sales quotation. To create a quotation for a project you must access it from the Project management and accounting module.   
6. Click OK.
    * The fields and actions on the quotation lines are very similar to the ones on the sales order lines.   Like sales orders, quotations can be created for a specific item or, when item number is not known or does not exist at the time of quotation creation, quotations can be created for a sales category.  
7. In the Item field, enter or select a value.
8. In the Item field, type a value.
9. Close the page.
10. In the Quantity field, enter a number.
    * If there are valid trade agreements for the item selected on the line, the applicable price and discounts will be automatically copied to the quotation line. Make sure that the Unit price field contains a value and you can also enter discount values if you want to.  
11. Click Save.
12. On the Action Pane, click Sales quotation.
13. Click Totals.
14. Click OK.
15. Click Sales quotation line.
16. Click Prices.
    * In the Run price simulation page you can experiment with adjusting the expected revenue or profitability of your quotation based on the desired unit price, discount amount, discount percentage, total amount, margin, or contribution ratio.   When you are satisfied with the target figures, you apply the suggestion to the quotation line, and its price-related fields will be updated accordingly.  
    * Y ou can create as many price simulations as you wish. When you click New, the price conditions from the current quotation line are copied to the page. You can then modify values in any of the price-related fields to the target ones. A change in one of the fields will trigger recalculation in all the other fields. In order for the system to calculate the sales margin and contribution ratio, the product's unit cost has to be known. Use the Simulated prices tab for a detailed view of the original prices, proposed changes and their effect on the quotation totals.   As a general rule, when a simulation that sets a new amount is applied to the quotation line, the system recalculates and enters a new value in the Unit price field. If the simulation is based on a new margin or a new contribution ratio, only the Net amount field is updated, and the Unit price is blank. In both cases, any discounts that were on the quotation line before simulation will be deleted.  
17. Close the page.
18. On the Action Pane, click Quotation.
19. Click Send quotation.
20. Select Yes in the Print quotation field.
21. Click OK.
    * The report may take a minute to generate. Don’t close the page until it does so.  
22. Close the page.

## Update a sales quotation
1. On the Action Pane, click Follow up.
2. Click Convert to customer.
3. In the Customer account field, type a value.
4. Click Check.
    * Make sure you see a message that the account number you typed in is free to use.  
5. Click OK.
    * The system has now created a new customer account for the prospect on the quotation.  
6. Close the page.
7. On the Action Pane, click Follow up.
8. Click Confirm.
9. In the Reason field, enter or select a value.
10. Click OK.
11. On the Action Pane, click General.
12. Click Sales orders.
13. Close the page.

