---
title: Enable Self-checkout in the Store Commerce app in Microsoft Dynamics 365 Commerce (preview)
description: This article explains how to enable Self-checkout and related features in the Store Commerce app in Microsoft Dynamics 365 Commerce (preview).
author: anush6121
ms.author: anvenkat 
ms.topic: how-to 
ms.date: 03/19/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Enable Self-checkout in the Store Commerce app in Microsoft Dynamics 365 Commerce (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article explains how to enable Self-checkout (SCO) and related features in the Store Commerce app in Microsoft Dynamics 365 Commerce.

Point of sale (POS) customers can reuse existing workflows to turn on kiosk-based SCO in an existing Store Commerce app. Your shoppers can then use SCO terminals to scan or search for items, add items to a shopping cart, and pay for the items by using a credit card or debit card.

To enable SCO, administrators must go to **Feature Management**, check for new updates, select **Configure POS self-checkout register**, and enable it.

## Configuration in Commerce headquarters

To enable SCO for a register, follow this step.

- Go to the **Register** setup, and set **Self-checkout** to **Yes**.

The presence of the **Self-checkout** flag drives the following behavior:

- **Enable task recorder** is set to **off**.
- **Hardware station** options are set to **No**.
- **Auto log off** is turned off.

Additionally, if the **Self-checkout** flag at the register is set to **Yes**, the following changes are made in POS to tailor consumer operations:

- Header and side navigation bars are hidden.
- Navigation to payment methods from totals is disabled.

> [!NOTE]
> If the store associate or manager has **manage device** set to **yes** in POS position permissions, the header and
> side navigation bars will still be visible on the self-checkout register. This allows store associates to perform any
> set up or admin tasks easily without switching to a cashier register.

To restrict specific products from being offered at SCO, follow this step.

- Go to **Released products**, and set **Blocked at self-checkout** to **Yes**.

## SCO device activation and kiosk sign-in

To enable only operations that are applicable to consumers on an SCO kiosk, create a new, generic user that has limited permissions and is used to sign in on the kiosk.

A new **SCO kiosk** permission group was created that has limited permissions. Assign this permission group to the new, generic user that you created. The user can then perform only consumer operations such as scan and pay.

### Sign-in process

Either the cashier or the store manager must use their permissions to activate SCO on the register. They must then turn on shifts for the SCO user. Finally, they must use the SCO user ID to sign in on the kiosk, so that consumers can use SCO throughout the day.

To enable shifts for SCO kiosks to be turned on or ended from cashier registers, be sure to set **Allow manage shared shift** to **Yes** for cashier user permissions.

To set up the kiosk and the hardware peripherals during initial setup, your admin can use their user credentials to sign in on the kiosk. Ensure that their screen layout is assigned to their user ID in Headquarters.

## Consumer-facing out-of-box layout

The shopper-facing layout is configured with limited operations and is available in the demo environment for export and import. Look for the SCO layout in **Screen layouts** under **Retail and Commerce**. Assign the screen layout to the **Registers** setup. 

> [!NOTE]
> In demo data, Houston - Register 49 is set up as an SCO register, and the SCO layout (**SCO\_POC1**) is assigned to it.
>
> Additionally, in demo data, user 000815 is configured as an SCO shopper/user, and user 000813 is configured as an SCO manager.

## Support for operations

The following consumer operations are supported.

| Operation | Action | Description |
|---|---|---|
| Scan and add item to cart | Product sale | This operation lets the customer scan items and add them to the transaction. If an item is restricted from SCO, an error message instructs the customer to ask a cashier for help. |
| Add rewards number | Add loyalty card | This operation invokes a numpad that the customer can use to enter their loyalty account number. In this way, the customer can be associated with the transaction. |
| Search item code | Product sale | This operation invokes a numpad that the customer can use to enter the item code of a product. In this way, the customer can add the product to the cart if the bar code is missing or can't be scanned. |
| Search | Search | This operation invokes a product browsing page where the customer can select products from product categories to add them to the cart. |
| Pay card | Pay card | This operation enables payment of the transaction by using a credit/debit card only. |

After payment is processed, there's an option to print a receipt.

## Assisted sale workflow

The **Call for assistance** operation provides support for cashier assistance during SCO. The **Allow request for assistance** action was created and associated with this operation. When a consumer selects this operation, a manager or store associate must sign in or swipe in to perform one of the following elevated operations:

- **Void** – This operation has two options:

    - **Void transaction** – Void the whole transaction.
    - **Void item** – Select a specific item to void. Only one item at a time can be selected for the operation.

- **Tax override** – This operation has two options:

    - **Override line tax** – Apply an exempt code and void the tax for a line.
    - **Override transaction** – Void the tax for the whole transaction.

- **Suspend transaction** – This operation lets the store associate suspend the transaction on the kiosk and resume it on a regular, non-SCO cashier register.
- **Price override** – This operation lets the store associate override the price of an item by selecting the item.
- **Add discount** – This operation has two options:

    - **Discount%** – Apply a discount percentage.
    - **Discount amount** – Apply a discount amount to the line item.

- **Logout** – This operation lets the store associate sign out of the kiosk.
- **Cancel** – This operation lets the store associate cancel out of the **Call for assistance** operation.
