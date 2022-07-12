--- 
# required metadata 
 
title: Create call center orders
description: This procedure walks through looking up a customer, creating a new order, searching for a product, and collecting payment from the customer. 
author: josaw1
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: MCRCustomerService, SalesTable, MCRSourceIdTargetLookup, MCRSalesQuickQuote, MCRSalesOrderRecap, MCRCustPaymDialog, MCRCustPaymLookup   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
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

This procedure walks through looking up a customer, creating a new order, searching for a product, and collecting payment from the customer. This procedure uses demo data company USRT and is intended for the Sales Order Clerk. 

## Pre-requisites:##
The user who completes the procedure is set up as a Call center user and optionally, Fabrikam Semi-Annual Catalog is published with at least one Source code on it.To add yourself as a call center user, navigate to the "All call centers" form and add yourself as a user. Refer the images below:
<ADD IMAGE HERE>

Additonally, open the call center form where you are added as a user and ensure that the "Enable order completion" configuration is enabled, if visible. If this configuration is not visible, then you can skip this step. Refer the image below.
<ADD IMAGE HERE>

 ## Steps
 
1. Go to **Retail and Commerce \> Customers \> Customer service**.
2. For **SearchText**, enter the search criteria to look up the customer.
    * For this example procedure, enter "Karen" and select **Tab**.  
3. Select Search.
    * Since there is only one customer named "Karen" in demo data, the result will be automatically selected.  If not selected, then press the "Select" button.  
4. Select **New sales order**.
5. Expand or collapse the **Sales order** header section and choose "Mode of delivery" as 99 - Standard shipping.
 <ADD IMAGE HERE>
  
6. Additionally, select the source code for the catalog.
    * If there are no active source codes you can skip this step.  
  
7. Press the "Lines" tab to come out of the Header tab and then select **Add line**.
  
8. For **Item number**, enter the item search term.
    * For this sample procedure, enter a item number of '813' and press tab. This action will bring up the item search window.  
  
9. Select the product to add to the sales order. For this task, select the item 81327
  
10. Enter the sales quantity.
  
11. Select **Complete** to capture the customer payment. Refer the image below:
 <ADD IMAGE HERE>
  
12. Clicking the Complete buttons opens the sales order summary which displays the total amount due. The Complete button also triggers the calculation for any charges such as shipping, handling etc. and they are displayed on the order summary form.
   <ADD IMAGE HERE>
    
13. Under the "Payments" section, select **Add** to capture the payments
    * Expand the Payments tab if it is collapsed.  
    
14. Select the payment method.
    * For this procedure, select the cash payment method.  
    
15. Close the page.
    
16. Enter the amount.
    * For this procedure, enter an amount equal to the order balance that can be seen in the Sales order summary page to the left of the amount field. This action will allow you to complete the order as fully paid.  
    
17. Select **OK**.
    
18. Select **Submit**.
    
## Additional resources

[Customize transactional emails by mode of delivery](../customize-email-delivery-mode.md)

[Change mode of delivery in POS](../pos-change-delivery-mode.md)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
