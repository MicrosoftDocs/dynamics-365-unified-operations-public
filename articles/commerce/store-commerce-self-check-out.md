---
title: Enable the Self-checkout in the Store Commerce app in Microsoft Dynamics 365 Commerce (preview)
description: This article explains how to enable Self-checkout and related features in the Store Commerce app in Microsoft Dynamics 365 Commerce (preview).
author: anush6121
ms.author: anvenkat 
ms.topic: how-to 
ms.date: 03/19/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Enable the Self-checkout in the Store Commerce app in Microsoft Dynamics 365 Commerce (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article explains how to enable Self-checkout (SCO) and related features in the Store Commerce app in Microsoft Dynamics 365 Commerce.

## Enabling Self-checkout

To enable self-checkout, administrators need to go to **Feature Management**, check for new updates, select the **Configure POS self-checkout register** feature, and enable it.

## Business value

Point of sale customers can turn on kiosk-based Self-checkout on an existing Store Commerce app reusing existing workflows. This release allows your shoppers to use self-checkout terminals to scan or search for items, add the items to a shoppingcart, and pay fo the items using a credit card or debit card.

## Configuration in Headquarters

To enable Self-checkout for a register, follow this step.

Go to **Register** setup and set **Self-checkout** to **Yes**.

The presence of such flag drives the following behavior:
- **Enable task recorder** is set to **off**
- **Hardware station** options are set to **No**.
- **Auto log off** is turned off.
  Additionally, based on this flag following changes are made in point of sale to tailor consumer operations:
  - Header and side navigation bars are hidden if the **self-checkout** flag at register is set to **yes**.
  - Navigating to payment methods from totals is disabled.

To restrict certain products from being offered at Self-checkout, follow this step.

Go to **Released products** and set **Blocked at self-checkout** to **Yes**.

## Self-checkout device activation and kiosk login

To enable only the consumer applicable operations in a self-checkout kiosk, create a new, generic user that has limited permissions and is used to log in on the kiosk.

A new **permission group** called **SCO kiosk** was created with limited permissions. Assigned to this permission group to the new, generic user you created to only allow for consumer operations such as scan and pay.

### Login process

Either the Cashier or the Store Manager must activate Self-checkout on the register using their permissions. Then they must turn on shifts for the SCO user, and then log in to the kiosk using the SCO user ID so that consumers can use Self-checkout throughout the day.

To turn on or end shifts from cashier registers for the SCO kiosks, ensure to set the **Allow manage shared shift** to **yes** for cashier user permissions.
In order to set up the kiosk and the hardware peripherals during initial set up, your admin can log in to the kiosk using their user credentials. Ensure their screen layout is assigned to their user ID in Headquarters.

## Consumer facing out of box layout

As part of the release, the shopper-facing layout has been configured with limited operations and is available in demo environment for export and import. Look for Self-checkout(SCO) layout in **Screen layouts** under **Retail and Commerce**.
Assign the screen layout to the **Registers** set up. 

> [!NOTE]
> In demo data, Houston - Register 49 is set up as SCO register and SCO layout(SCO_POC1) has been assigned to it.
Also, user 000815 is configured as SCO shopper/user. And user 000813 is configured as a SCO manager in demo data.

## Support for operations

Following consumer operations are supported:

- **Scan and add item to cart** - **Action**: **Product sale** Allows user to scan the items and add them to the transaction. If an item is restricted from self-checkout, there's an error message displayed to seek cashier's assistance.
- **Add rewards number** - **Action**: **Add loyalty card** This operation invokes a numpad to enter the loyalty account number, so that the customer can be associated with the transaction.
- **Search item code** - **Action**:**Product sale** This operation invokes a numpad to enter the item code of the product to add to cart if the barcode is missing or won’t scan.
- **Search** - **Action**: **Search** This operation invokes product browsing screen to be able to select product from product categories to add to cart.
- **Pay card**- **Action**: **Pay card** This operation enables payment of the transaction using credit/debit card only.

Once payment is processed, there's an option to print receipts.

## Assisted sale workflow

To provide support for cashier assistance during self-checkout, a new operation **Call for assistance** has been created.

A new action **Allow request for assistance** has been created and associated with this operation. When a consumer selects this operation, a manager or a store associate is required to sign/swipe in to perform one of the following elevated operations.

- **Void**: This operation has two options **Void transaction** to void the whole transaction and **Void item** to select the item to void the item. Only one item can be selected at a time to perform the operation.
- **Tax override**: This operation has two options **Override line tax** to apply an exempt code and void tax for a line and **Override transaction** to void the tax for entire transaction.
- **Suspend transaction**: This operation allows store associates to suspend the transaction from kiosk and resume from a regular cashier non-SCO register.
- **Price override**: This operation allows you to override price of an item by choosing the item.
- **Add discount**: This operation has two options **Discount%** to apply discount% and **Discount amount** to apply a discount amount to the line item.
- **Logout**: This operation allows the store associate to log out of the kiosk.
- **Cancel**: This operation allows the store associate to cancel out of the **Call for assistance** operation.

