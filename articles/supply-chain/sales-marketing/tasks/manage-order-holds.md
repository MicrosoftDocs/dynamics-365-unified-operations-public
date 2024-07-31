---
title: Manage order holds
description: Learn how to place customer sales orders on hold, how to work with order hold checkouts, and how to remove order holds with a process for setting up order holds.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: MCRHoldCodeTable, SalesTableListPage, SalesCreateOrder, SalesTable, MCRHoldCodeTrans, MCRHoldCheckOutOverride, MCRHoldCodeTable, MCRItemListCopying, MCRItemListTable, MCROMHoldList
ms.topic: how-to
ms.date: 07/01/2024
ms.custom: 
  - bap-template
---

# Manage order holds

[!include [banner](../../includes/banner.md)]

This article demonstrates how to place customer sales orders on hold, how to work with order hold checkouts, and how to remove order holds. An order might be placed on hold for various reasons. For example, you might hold an order until a customer address or payment method can be verified or until a manager can review the customer's credit limit. While the order on hold, it can't be processed by the warehouse for shipping.

## Set up order hold codes

There could be many reasons why an order should be placed on hold. Use hold codes to set up each of the various types of holds you'd like to be able to apply to sales orders.

1. Go to **Sales and marketing > Setup > Sales orders > Order hold codes**.
1. Do one of the following actions:
    - To create a new hold code, select **New** on the Action Pane.
    - To edit an existing hold code, select **Edit** on the Action Pane, and then select an existing hold code on the list pane.
1. Make the following settings for your new or selected hold code:
    - **Hold code** – Enter a short name for the hold code (for example, *Call back*).
    - **Description** – Enter a short description to provide more information about the hold code (for example, *Order held waiting for customer callback*).
    - **Role** – Select the security role that a user must have to be able to remove this hold code from an order. For example, if you select *Collections agent*, only users with that role can remove this hold code from an order.
    - **Default for sales order** – Select this check box to make this hold code selected by default each time a user adds a new hold to an order.
    - **Remove inventory reservations** – Select this check box to remove any physical reservations from an order when this hold code is added to it.  
1. Select **Save**.

## Place order on hold

To place a sales order on hold, follow these steps:

1. Go to **Sales and marketing > Sales orders > All sales orders**.
1. Select the sales order you want to put on hold.
1. On the Action Pane, open the **Sales order** tab and from the **Functions** group, select **Order holds**.
1. On the Action Pane, select **New**.
1. In the **Hold code** field, select the hold code you want to apply.
1. Select **Save**.
1. Go back to the **All sales orders** list page.
1. On the grid, find the order you put on hold and note that it now shows a check mark in the **Do not process** column and a pause symbol in the **Hold** column.
1. On the Action Pane, open the **Pick and pack** tab and note that the buttons for generating picking lists and packing slips are disabled. This is because the order is on hold and can't be processed further until the hold is removed.

## Manage orders that are on hold

To manage orders that are on hold, and remove holds, follow these steps:

1. Go to **Sales and marketing** \> **Sales orders** \> **Open orders** \> **Order holds**. The **Order holds** page functions as a workbench where you can get an overview of all the current and processed holds, and handle them and associated sales orders.
1. Use the **Filter** field and/or the **Show** drop-down list to filter the list by value and/or hold status. Then select the hold you want to change.
1. It's possible to check out order holds. Other users are prevented from clearing a hold while you have it checked out. To check an order hold in or out, open the **Hold checkout** tab on the Action Pane and choose one of the following actions:
    - **Check out** – Select this option to check out the selected hold. The **Checked out to** column updates to show your user ID for the selected hold.
    - **Clear checkout** – Select this option to check in a hold that you previously checked out. Your user ID is removed from **Checked out to** column for the selected hold.
    - **Override checkout** – Select this option to reassign a checked-out hold to another user (or yourself). The **Checked out to** column updates to show the selected user's ID.
1. When you're ready to remove the hold and allow the order to proceed to the next fulfillment step, you must clear it. On the Action Pane, open the **Clear hold** tab and select one of the following options:
    - **Clear holds** – If the order requires no changes, select this option to clear the holds on it.
    - **Clear and modify** – If the order requires changes, the select this option to clear the holds on it and then open the order so you can modify it.
    - **Clear and submit** – Clear all holds and submit the order for further processing. This action only applies when you're using call center functionality.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
