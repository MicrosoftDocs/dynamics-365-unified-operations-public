--- 
# required metadata 
 
title: Manage order holds
description: This procedure demonstrates how to place customer sales orders on hold, how to work with order hold checkouts, and how to remove order holds. 
author: Henrikan
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: MCRHoldCodeTable, SalesTableListPage, SalesCreateOrder, SalesTable, MCRHoldCodeTrans, MCRHoldCheckOutOverride, MCRHoldCodeTable, MCRItemListCopying, MCRItemListTable, MCROMHoldList   
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
# Manage order holds

[!include [banner](../../includes/banner.md)]

This procedure demonstrates how to place customer sales orders on hold, how to work with order hold checkouts, and how to remove order holds. An order might be placed on hold for a variety of reasons. For example, you might hold an order until a customer address or payment method can be verified or until a manager can review the customer's credit limit. While the order on hold, it cannot be processed by the warehouse for shipping. 

You can run this procedure in demo data company USMF or on your own data.


## Set up order holds
1. Go to **Sales and marketing > Setup > Sales orders > Order hold codes**.
2. Click **New**.
3. In the **Hold code** field, type a value. For example, type 'Call back'.  
4. In the **Description** field, type a value.
    - For example, Order held waiting for customer callback.  
    - Optionally, select the **Remove reservations** check box to remove any physical reservations from the order when this hold code is added.  
5. Click **Save**.

## Place order on hold
1. Go to **Sales and marketing > Sales orders > All sales orders**.
2. Click **New**.
3. In the **Customer account** field, enter or select a value.
4. Click **OK**.
5. In the **Item number** field, enter or select a value.
6. In the **Quantity** field, enter a number.
7. On the **Action Pane**, click **Sales order**.
8. Click **Order holds**.
9. Click **New**.
10. In the **Hold code** field, select the code you have created in the previous subtask.
11. Click **Save**.
12. Close the page.
13. Go to **Sales and marketing > Sales orders > All sales orders**.
14. In the list, mark the selected row. Orders that are currently on hold have the "Do not process" and "Hold" fields marked.
15. On the Action Pane, click **Pick and pack**.

## Manage order holds
1. Go to **Sales and marketing > Sales orders > Open orders > Order holds**. **Order holds** page functions as a workbench where you can get an overview of all the current and processed holds, and handle them and associated sales orders.     
2. In the list, mark the selected row.
3. On the **Action Pane**, click **Hold checkout**.
4. Click **Check out**.
5. In the list, unmark the selected row. The **Checkout out to** field now shows your user ID.   
6. Click **Clear checkout**.
7. On the **Action Pane**, click **Clear hold**.
    - When you are ready to remove the hold and allow the order to proceed to the next fulfilment step, you must clear the hold. If the order requires no changes, you can run the Clear holds action. However, you can use the Clear and modify action if, when clearing a hold, the order has to be updated.      
    - The **Clear and submit** action is only applicable when you use Call center functionality.  
8. Click **Clear holds**. The hold has now been cleared from the order and removed from the list of Active holds. To see all the holds or their subset according to a specific status, change the value in the Show field.     



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]