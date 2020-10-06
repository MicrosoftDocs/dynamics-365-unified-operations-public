--- 
# required metadata 
 
title: Create call center orders
description: This procedure walks through looking up a customer, creating a new order, searching for a product, and collecting payment from the customer. 
author: josaw1
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: MCRCustomerService, SalesTable, MCRSourceIdTargetLookup, MCRSalesQuickQuote, MCRSalesOrderRecap, MCRCustPaymDialog, MCRCustPaymLookup   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create call center orders

[!include [banner](../includes/banner.md)]

This procedure walks through looking up a customer, creating a new order, searching for a product, and collecting payment from the customer. This procedure uses demo data company USRT and is intended for the Sales Order Clerk. Pre-requisites:  The user who completes the procedure is set up as a Call center user and the Fabrikam Semi-Annual Catalog is published with at least one Source code on it.

1. Go to Retail and Commerce > Customers > Customer service.
2. In the SearchText field, enter the search criteria to look up the customer.
    * For this example procedure type in 'karen' and press tab.  
3. Click Search.
    * Since there is only one customer named Karen in demo data they will be automatically selected.  
4. Click New sales order.
5. Expand or collapse the Sales order header section.
6. Select the source code for the catalog.
    * If there are no active Source codes you can close the Source field and skip this step.  
7. Click Add line.
8. In the Item number field, enter the item search term.
    * For this sample procedure enter a partial item number of '8111' and press tab. This will pop up the item search window.  
9. Select the product to add to the sales order
10. Enter the sales quantity.
11. Click Create.
12. Click Complete to capture the customer payment.
13. Click Add.
    * The Add link is in the Payments tab. Expand the Payments tab if it is collapsed.  
14. Select the payment method.
    * For this procedure, select the cash payment method.  
15. Close the page.
16. Enter the amount.
    * For this procedure enter an amount equal to the order balance which can be seen in the Sales order summary page to the left of the amount field. This will allow you to complete the order as fully paid.  
17. Click OK.
18. Click Submit.

