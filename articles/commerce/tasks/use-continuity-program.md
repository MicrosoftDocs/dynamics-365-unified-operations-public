---
title: Using continuity program
description: Learn how to sell a continuity program and process related sales orders in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 02/11/2026
ms.topic: how-to
ms.author: josaw
ms.reviewer: v-griffinc
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: MCRCustomerService, MCRCustSearch, SalesTable, MCRContinuityCustInfo, MCRCustPaymLookup, CreditCardTokenization, CreditCardLookup, MCRSalesOrderRecap
ms.custom: 
  - bap-template 
---
# Using continuity program

[!include [banner](../includes/banner.md)]

This article explains how to sell a continuity program and process related sales orders in Microsoft Dynamics 365 Commerce.

The following procedure walks through selling a continuity program and processing related sales orders. To complete the procedure, set up the user as a call center user. This procedure uses the USRT demo data company.

To sell a continuity program and process related sales orders, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce > Customers > Customer service**.
1. In the **SearchText** field, enter "Karen" and then select the Tab key. The advanced search dialog appears. If it doesn't, select **Search**.  
1. In the list, mark the selected row. There should be only one row with "Karen Berg" showing. Select the row by selecting the checkmark column on the far left of the grid.  
1. Select **Select**.
1. Select **New sales order**. Save the sales order number for use later in this procedure.  
1. In the **Item number** field, enter "88000" and then select the Tab key. This number is a continuity item in the USRT demo data.  
1. Select **Complete**.
1. In the **Payment method** field, enter "Visa".
1. Select **Add credit card**.
1. Enter the required credit card information on this page.  
1. Select **OK**.
1. Expand the **Payment** section. To submit a call center order, enter payments for the order.  
1. Select **OK**.
1. Select **Submit**. You're done creating a new continuity order. Next, you run two batch processes that are used to process the continuity orders.  
1. Close the page.
1. Go to **Retail and Commerce > Continuity > Process continuity payments**.
1. In the **Continuity item** field, enter "88000", and then select the Tab key.
1. Select **OK**.
1. Go to Retail and Commerce > Continuity > Create continuity child orders. This process creates new sales orders based on the settings of your continuity programs.  
1. In the **Continuity item** field, enter "88000" and then select the Tab key. Item "88000" is a continuity item in the USRT demo data.  
1. In the **Sales order** field, enter or select a value.
1. Enter the sales order number that you noted earlier in the procedure, which minimizes the processing time. The **Sales order** field value is optional. You can process all orders for any one program.  
1. Select **OK**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
