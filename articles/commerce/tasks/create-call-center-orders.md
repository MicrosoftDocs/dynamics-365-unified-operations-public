--- 
# required metadata 
 
title: Create call center orders
description: This article walks through an example procedure where call center users can look up a customer, create a new order, search for a product, and collect payment from a customer in Microsoft Dynamics 365 Commerce. 
author: josaw1
ms.date: 07/28/2022
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

This article walks through an example procedure where call center users can look up a customer, create a new order, search for a product, and collect payment from a customer in Microsoft Dynamics 365 Commerce. The procedure uses demo data company USRT and is intended for sales order clerks. 

## Prerequisites

The user who completes the procedure must be set up as a call center user. Optionally, the Fabrikam semi-annual catalog can be published with at least one source code on it. 

## Add yourself as a call center user

To add yourself as a call center user, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Channels \> Call centers \> All call centers**.
1. Under **Users**, select **Channel users**.
1. On the action pane, select **+New**.
1. Under **User ID**, enter your user ID. 
1. Under **Name**, enter your user name. The user name can be the same as the user ID.
1. On the action pane, select **Save**.
1. Go back to **Retail and Commerce \> Channels \> Call centers \> All call centers**.
1. Select the **Retail Channel Id**, select the retail channel ID for the call center.
1. Confirm that the **Enable order completion** option is set to **Yes**. If this option is not visible, you can skip this step.

## Step through the example call center procedure

To step through the example call center procedure, follow these steps.

1. Go to **Retail and Commerce \> Customers \> Customer service**.
1. On the **Customer search** tab, enter the search criteria to look up the customer. For this example procedure, enter "Karen".  
1. Select **Search**. The **Customer search** flyout menu appears. Since there is only one customer named "Karen" in the demo data, the result **Karen Berg** will be listed. Selected the customer record, and then select **Select**.  
1. On the action pane, select **New sales order**.
1. On the right, select the **Header** tab.
1. Select the **Delivery** FastTab.
1. Under **Mode of delivery**, select **99 - Standard shipping** from the drop-down list.

    ![Select a mode of delivery](../media/Select_Mode_of_Delivery.png)
   
1. On the right, select the **Lines** tab.

1. Under **Sales order lines**, select **Add line**.

1. On the row for the new sales line, for **Item number** enter the item number to search for. For this example procedure, enter the item number of '81317' and then select the product from the drop-down list to add it to the sales order.
1. For **Quantity**, enter the sales quantity.
1. For **Source code**, select the source code for the catalog. If there are no active source codes, you can skip this step.
1. On the action pane, select **Complete** to capture the customer payment. This action opens the **Sales order summary** flyout menu that displays the total amount due. Selecting **Complete** also triggers the calculation for any charges such as shipping and handling and displays the charges on the order summary form.

    ![Select Complete](../media/Complete_button.png)

1. On the **Sales order summary** flyout menu, under the **Payments** section, select **+Add** to capture the payments. Expand the **Payments** tab if it is collapsed. 

    ![View order summary](../media/order_summary.png)

1. Select the payment method. For this example procedure, select the cash payment method.  
1. Close the the **Sales order summary** flyout menu.
1. Enter the amount. For this example procedure, enter an amount equal to the order balance that can be seen in the Sales order summary page to the left of the amount field. This action will allow you to complete the order as fully paid.  
1. Select **OK**.
1. Select **Submit**.
    
## Additional resources

[Customize transactional emails by mode of delivery](../customize-email-delivery-mode.md)

[Change mode of delivery in POS](../pos-change-delivery-mode.md)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
