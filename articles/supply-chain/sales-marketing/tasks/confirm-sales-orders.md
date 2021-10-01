--- 
# required metadata 
 
title: Confirm sales orders
description: This procedure demonstrates how to confirm sales orders. 
author: Henrikan
ms.date: 06/26/2019
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SalesTableListPage, SalesTable, SalesEditLines,  SrsReportViewerForm, CustConfirmJournal, SysQueryForm, SysQueryFieldLookUp, SysLookup, SalesParmIdLookup, SalesUnconfirmedOrdersPart   
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
# Confirm sales orders

[!include [banner](../../includes/banner.md)]

This procedure demonstrates how to confirm sales orders. You'll be shown how to confirm a single order, and how to confirm multiple orders at once. These tasks would typically be carried out by a sales order processor. You can use this procedure in demo data company USMF or on your own data. Before you start, make sure there are several open sales orders for the same customer. If you're using USMF, you can use customer US-027.


## Confirm a single sales order
1. Go to **Navigation pane > Modules > Sales and marketing > Sales orders > All sales orders**.
2. In the list, find and select the order that you want to confirm.
3. Click the link on the sales order number to open the selected order.
4. On the **Action Pane**, click **Sell**.
5. Click **Confirm sales order**.
6. Expand the **Parameters** section. Make sure that the **Posting** option is set to 'Yes'.  
7. Set the **Print confirmation option** to 'Yes'. The **Check credit limit** field specifies the method that's used to calculate a customer's remaining credit. By default, it's copied from the Accounts receivable parameters page. If you want to skip the credit limit check when confirming a specific sales order, set the **Check credit limit** to 'None'. However, you should be aware that even with if this field is set to 'None', the credit limit check will still be performed if the **Mandatory credit limit** option is selected on the customer master data. 
8. Click **OK**.
9. Click **Yes**.
10. Close the page.
11. On the **Action Pane**, click **Options**.
12. Click **Change view**.
13. Click **Header view**. When an order is confirmed, the **Document status** is set to 'Confirmation'. 
14. On the **Action Pane**, click **Sell**.
15. Click **Sales order confirmation**.
16. Close the page.

## Confirm multiple sales orders at once
1. Go to **Sales and marketing > Sales orders > Order confirmation > Confirm sales order**.
2. Click **Select**.
3. In the list on the **Range** tab, find and select the record that references the **Customer account** field.
4. In the **Criteria** field, click the drop-down button to open the lookup.
5. In the list, find and select the customer account that has multiple orders which you want to mass confirm. If you're using USMF, you can select account US-027.  
6. Click **OK**.
    - The **Overview** tab displays a list of the orders that match the query criteria. These will be included in the confirmation.  
    - The **Summary update for** field in the **Parameters** section specifies the parameter by which multiple orders are to be summarized into one confirmation document. By default, the option is copied from the D**efault values for summary update setting** on the **Accounts receivable parameters** page.  
7. In the **Summary update for** field, select 'Order'. The minimum parameters that are required to create summary updates are **Invoice account** and **Currency**. This means that summary updates that have different invoice accounts and different currencies are not allowed. Additional parameters can be set up in the **Summary update parameters** page which is accessible from the **Accounts receivable parameters** page. 
8. In the **Sales order** field, click the drop-down button to open the lookup.
9. In the list, select the order number that you want to be the summary order.
10. Click **Arrange**.
11. Click **OK**.
12. Click **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]