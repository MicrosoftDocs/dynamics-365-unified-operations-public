--- 
# required metadata 
 
title: Manage order holds
description: This procedure demonstrates how to place customer sales orders on hold, how to work with order hold checkouts, and how to remove order holds. 
author: omulvad
manager: tfehr 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: MCRHoldCodeTable, SalesTableListPage, SalesCreateOrder, SalesTable, MCRHoldCodeTrans   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: omulvad
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Manage order holds

[!include [banner](../../includes/banner.md)]

This procedure demonstrates how to place customer sales orders on hold, how to work with order hold checkouts, and how to remove order holds. An order might be placed on hold for a variety of reasons. For example, you might hold an order until a customer address or payment method can be verified or until a manager can review the customer's credit limit. While the order on hold, it cannot be processed by the warehouse for shipping. 

You can run this procedure in demo data company USMF or on your own data.


## Set up order holds
1. Go to **Navigation pane > Modules > Sales and marketing > Setup > Sales orders > Order hold codes**.
2. Click **New**.
3. In the **Hold code** field, type a value. For example, type 'Call back'.  
4. In the **Description** field, type a value.
    - For example, Order held waiting for customer callback.  
    - Optionally, select the **Remove reservations** check box to remove any physical reservations from the order when this hold code is added.  
5. Click **Save**.

## Place order on hold
1. Go to **Navigation pane > Modules > Sales and marketing > Sales orders > All sales orders**.
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

## Set account receivable preferences for order holds and order classes

There are a few additional parameters that will allow you to enhance your order hold process.

1. Go to **Accounts receivable \&gt; Setup \&gt; Accounts receivable parameters.**
2. Open the **General** taband expand the **Order management** FastTab.
3. Make the settings described in the following table as needed.

| **Setting** | **Description** |
| --- | --- |
| **Default order class fields** | Select the default holds to be applied if an order class isn&#39;t selected. |
| **Mandatory field check** | Run a check and notify the user when they create an order with a certain order class and haven&#39;t provided values for all the mandatory fields. |
| **Hold on mandatory check failed** | If an order fails the mandatory field check, then you automatically place it on a specified hold. |
| **Hold control** |
 |
| **Holds control list** | These are the default hold codes that will be applied to your sales orders. They will be overridden if you chose a specific order class for an order.
 |

## Trigger an order hold

To learn more about how to setup an order hold refer to the documentation on [managing order holds](https://docs.microsoft.com/en-us/dynamics365/supply-chain/sales-marketing/tasks/manage-order-holds#set-up-order-holds).

When you create a new &quot;order hold code&quot; you can set it to automatically gets applied when a certain order event is triggered. To do this:

1. Ensure that your triggering order event is enabled, as described in [Set up order event](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/set-up-order-events)s.
2. Go to **Sales and marketing \&gt; Sales orders \&gt; Open orders \&gt; Order holds.**
3. Select an order hold.
4. Go to the **Trigger events** section
5. Select the order event that should automatically trigger the order hold.

This will ensure that your order hold will automatically get applied as soon as that specific order event is triggered

To automatically remove an order hold based on a triggering event:

1. Navigate to your order hold code setup. (**Sales and marketing \&gt; Sales orders \&gt; Open orders \&gt; Order holds.)**
2. Navigate to the **Remove hold on application** FastTab
3. Select the triggering event that will remove this hold in the Trigger event field.

To automatically add another hold as soon as a current one is removed:

1. Navigate to your order hold code setup. (**Sales and marketing \&gt; Sales orders \&gt; Open orders \&gt; Order holds.)**
2. Navigate to the **Manual following hold** section.
3. Select the order hold code that should apply automatically as soon as the current hold is removed.

To block certain documents when a hold is applied:

1. Navigate to the **Related document blocking** section of your hold code setup.
2. Select the documents that you want to prevent being created when this is hold is being applied.

## Trigger a hold based on the mandatory field check

In certain situations, you might want to automatically place an order on hold if it doesn&#39;t have the mandatory fields required by the order class. If you want to do this you need to do the following:

1. Navigate to **Accounts receivable \&gt; setup \&gt; accounts receivable parameters**.
2. Then you need to navigate to the **General** taband go to the **Order** management section.
3. Turn on the &#39;Mandatory field check&#39; parameter
4. Turn on the &#39;Hold on mandatory check failed&#39; parameter

Now you need to create a hold code that is triggered by this order event.

1. Create a new order hold code
2. Set the trigger event to &#39;Mandatory fields check&#39;

Lastly, you need to link the order hold to the order class.

## Link an order hold to an order class

You can set up an order class to apply an order hold to all orders belonging that class. This enables the order class to automatically place and remove an order hold without relying on another user to manually remove it. For details about how to configure order classes, including how to set some or all of them to apply order holds, see XXXX.

