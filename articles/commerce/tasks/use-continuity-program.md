---
title: Using continuity program
description: This procedure walks through selling a continuity program and processing related sales orders.
author: josaw1
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.industry: Retail
ms.search.form: MCRCustomerService, MCRCustSearch, SalesTable, MCRContinuityCustInfo, MCRCustPaymLookup, CreditCardTokenization, CreditCardLookup, MCRSalesOrderRecap
---
# Using continuity program

[!include [banner](../includes/banner.md)]

This procedure walks through selling a continuity program and processing related sales orders. To complete this procedure, the user has to be set up as a call center user. This procedure uses the USRT demo data company.

1. Go to Retail and Commerce > Customers > Customer service.
2. In the SearchText field, type 'Karen' and then press the Tab key.
    * The advanced search dialog should pop up. If it doesn't, click Search to the right of this field.  
3. In the list, mark the selected row.
    * There should be only one row with Karen Berg showing. Select the row by clicking on the checkmark column on the far left of the grid.  
4. Click Select.
5. Click New sales order.
    * It's a good idea to note the sales order number. You'll need it later in this procedure.  
6. In the Item number field, type '88000' and then press the Tab key.
    * This is a continuity item in the USRT demo data.  
7. Click Complete.
8. In the Payment method field, enter 'Visa'.
9. Click Add credit card.
    * Enter the required credit card information on this page.  
10. Click OK.
11. Expand the Payment section.
    * To submit a call center order, payments have to be entered for the order.  
12. Click OK.
13. Click Submit.
    * You're done creating a new continuity order. Next, you'll run two batch processes that are used to process the continuity orders.  
14. Close the page.
15. Go to Retail and Commerce > Continuity > Process continuity payments.
16. In the Continuity item field, type '88000' and then press the Tab key.
17. Click OK.
18. Go to Retail and Commerce > Continuity > Create continuity child orders.
    * This process will create new sales orders based on the settings of your continuity programs.  
19. In the Continuity item field, type '88000' and then press the Tab key.
    * Item '88000' is a continuity item in the USRT demo data.  
20. In the Sales order field, enter or select a value.
    * Enter the sales order number that you noted earlier in the procedure. This will keep the processing time to a minimal for this procedure. The Sales order field field is optional--you could process all orders for any one program.  
21. Click OK.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
