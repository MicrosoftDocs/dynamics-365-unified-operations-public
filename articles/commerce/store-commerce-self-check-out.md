---
title: Use self checkout
description: This article explains how to use self checkout
author: anush6121
ms.author: anvenkat 
ms.topic: how-to 
ms.date: 03/19/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Store Commerce self-checkout

This article describes how to enable self-check out within Store commerce app and all of the features that are available as part of 10.0.40 release.

## Enabling Self-checkout
To enable self-check out, admins would need to go into **Feature Management**, check for new updates and select feature **Configure POS self-checkout register** and enable it.

## Business value
Point of sale customers can turn on kiosk based Self-checkout on existing store commerce app re-using existing workflows.
This relase allows for your consumers to use self-checkout terminals to scan or search for items, add to cart and pay by credit/debit only.

## Configuration in Head Quarters
To enable self-checkout for a register do the following:
Goto **Register** set up and set **self-checkout** to **yes**
The presence of such flag will drive the following behavior:
- **Enable task recorder** will be set to **off**
- **Hardware station** options will be set to **No**.
- **Auto log off** will be turned off.
Additionally based on this flag following changes are made in point of sale to tailor consumer operations:
  - Header and side navigation bars will be hidden if the **self-checkout** flag at register is set to **yes**.
  - Navigating to payment methods from totals will be disabled.

To restrict certain products from being offered at self-checkout do the following:
Goto **Released products** and set **Blocked at self-checkout** to **yes**

## Self-checkout device activation and kiosk login
To enable only consumer applicable operations in a self-checkout kiosk, a new/generic user with limited permissions should be created that will be used to login to the kiosk.
A new **permission group** called **SCO kiosk** has been created with gated permissions so that the new SCO user can be assigned to this permission group that will only allow for consumer operations such as scan and pay.

### Login process
The cashier or the store manager is expected to activate the selfcheckout device using their permissions, turn on shifts for the "SCO user" and then login to the kiosk using the SCO user id so that consumers can carry out self-checkout throughout the day.
To turn on or end shifs from cashier registers for the SCO kiosks, please ensure to set the **Allow manage shared shift** to **yes** for cashier user permissions.

## Consumer facing out of box layout
As part of the release consumer facing layout has been configured with limited operations and will be available in demo environment for export and import. Look for self-checkout(SCO) layout in **Screen layouts** under **Retail and Commerce**.
Assign the screenlayout to the **Registers** set up. 
Note: In demo data, Houston-49 is set up as SCO register and SCO layout has been assigned to it.
<insert image of out of box layout>

## Support for operations
Following consumer operations are supported:
- **Scan and add item to cart** - **Action**: **Product sale**. Allows user to scan the items and add to the transaction. If an item is restricted from self-checkout, there is an error message displayed to seek cashier's assistance.
- **Add rewards number** - **Action**: **Add loyalty card**. This operation will invoke a numpad to enter the loyalty account number, so that the customer can be associated to the transaction.
- **Search item code** - **Action**:**Product sale** This operation will invoke a numpad to enter the item code of the product to add to cart if the barcode is missing or wont scan.
- **Search** - **Action**: **Search** This operation will invoke product browsing screen to be able to select product from product categories to add to cart.
- **Pay card**- **Action**: **Pay card**This operation will enable payment of the transaction using credit/debit card only.
Once payment is processed, there will be an option to print receipt.

## Assisted sale workflow
To provide support for cashier assistance during self-checkout a new operation **Call for assistance** has been created.
A new action **Allow request for assistance** has been created and associated with this operation. When a consumer selects this operation, manager or store associate will be required to sign/swipe in to perform one of the following elevated operations.
- **Void**: This has two options **Void transaction** to void the whole transaction and **Void item** to select the item to void the item. Only one item can be selected at a time to perform the operation.
- **Tax override**: This has two options **Override line tax** to apply an exempt code and void tax for a line and **Override transaction** to void the tax for entire transaction.
- **Suspend transaction**: This allows store associate to suspend the transaction from kiosk and resume from a regular cashier non-sco register.
- **Price override**: This allows to override price of an item by choosing the item.
- **Add discount**: This has two options **Discount%** to apply discount% and **Discount amount** to apply a discount amount to the line item.
- **Logout**: This allows the store associate to logout of the kiosk.
- **Cancel**: This allows the store associate to cancel out of the **Call for assistance** operation.

  

















