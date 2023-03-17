---
title: Confirm sales orders
description: This procedure demonstrates how to confirm sales orders. 
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SalesTableListPage, SalesTable, SalesEditLines,  SrsReportViewerForm, CustConfirmJournal, SysQueryForm, SysQueryFieldLookUp, SysLookup, SalesParmIdLookup, SalesUnconfirmedOrdersPart   
ms.topic: how-to
ms.date: 02/06/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---
# Confirm sales orders

[!include [banner](../../includes/banner.md)]

This procedure demonstrates how to confirm sales orders. You'll be shown how to confirm a single order, and how to confirm multiple orders at once. These tasks would typically be carried out by a sales order processor.

## Confirm a single sales order

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. In the list, find and select the order that you want to confirm.
1. Select the link on the sales order number to open the selected order.
1. On the Action Pane, select *Sell*.
1. Select **Confirm sales order**.
1. Expand the **Parameters** section. Make sure that the **Posting** option is set to *Yes*.  
1. Set the **Print confirmation option** to *Yes*. The **Check credit limit** field specifies the method that's used to calculate a customer's remaining credit. By default, it's copied from the **Credit and collections parameters** page. If you want to skip the credit limit check when confirming a specific sales order, set the **Check credit limit** to *None*. However,  even when this field is set to *None*, the credit limit check will still be performed if the **Mandatory credit limit** option is selected on the customer master data.
1. Select **OK**.
1. Select **Yes**.
1. Close the page.
1. On the **Action Pane**, select **Options**.
1. Select **Change view**.
1. Select **Header view**. When an order is confirmed, the **Document status** is set to *Confirmation*.
1. On the Action Pane, select **Sell**.
1. Select **Sales order confirmation**.
1. Close the page.

## Confirm multiple sales orders at once

1. Go to **Sales and marketing \> Sales orders \> Order confirmation \> Confirm sales order**.
1. Select **Select**.
1. In the list on the **Range** tab, find and select the record that references the **Customer account** field.
1. In the **Criteria** field, find and select the customer account that has multiple orders to confirm.
1. Select **OK**.
    - The **Overview** tab displays a list of the orders that match the query criteria. These orders will be included in the confirmation.  
    - The **Summary update for** field in the **Parameters** section specifies the parameter by which multiple orders are to be summarized into one confirmation document. By default, the option is copied from the **Default values for summary update** setting on the **Accounts receivable parameters** page.  
1. In the **Summary update for** field, select *Order*. The minimum parameters that are required to create summary updates are **Invoice account** and **Currency**. This requirement means that summary updates that have different invoice accounts and different currencies aren't allowed. You can set up other parameters on the **Summary update parameters** page, which is accessible from the **Accounts receivable parameters** page.
1. In the **Sales order** field, select the order number that you want to be the summary order.
1. Select **Arrange**.
1. Select **OK**.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
