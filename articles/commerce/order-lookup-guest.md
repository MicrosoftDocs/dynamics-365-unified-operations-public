---
# required metadata

title: Enable order lookup for guest checkouts 
description: This topic describes how to enable order lookup for guest checkouts in Microsoft Dynamics 365 Commerce.
author: stuharg
ms.date: 09/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: stuharg
ms.search.validFrom: 2021-08-15
ms.dyn365.ops.version: Release 10.0.22

---


# Enable order lookup for guest checkouts

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes how to enable order lookup for guest checkouts in Microsoft Dynamics 365 Commerce.

The order lookup for guest checkouts feature allows customers who make purchases as guest users to be able to look up their orders. This order lookup capability is useful for customers who want perform actions such as checking the fulfillment status of products in an order, verifying the address that an order was shipped to, reordering a product, or confirming which store to pick up an order from. 

Customers who make purchases as registered users can already see their order details when they are signed in, but this is not possible for customers who place orders using guest checkouts. When the order lookup for guest checkouts feature is enabled, customers who want to look up orders they placed as guests fill can out a form to provide the order confirmation ID and (optionally) the email address they specified at checkout.

A link or button that takes the customer directly to the order details page for their order can also be included in any order-related transactional emails. This link or button will work for orders placed by both registered and guest users. 

## Enable order lookup for guest checkouts

To enable order lookup for guest checkouts, the following feature management switches must be turned on in Commerce headquarters at **Workspaces \> Feature management**.

| Feature management switch                           | Purpose                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Retail anonymous user search order details opting feature**   | This switch exposes the user interface under Commerce parameters that allows you to enable the order lookup API for unauthenticated users and configure how personal data is displayed. |
| **Enable generation  of a stronger channel reference ID**        | This switch generates a more secure 12 character channel reference ID (order confirmation  ID) which allows it to be passed in the query string when looking up an  order. |
| **Generate a  consistent channel reference ID format across channels** | This switch generates a secure channel reference ID for orders placed through e-commerce, point of sale and call center orders. To enable this switch, the Enable generation of a stronger channel reference ID switch must also be enabled. |

To enable order lookup for guest checkouts, after turning on the **Retail anonymous user search order details opting feature** switch you must also enable the API that supports unauthenticated order lookup in Commerce headquarters by going to the **Order search** FastTab at **Retail and Commerce \> Headquarters setup \> Parameters \> Customer orders** and setting **Enable unauthenticated order lookup** to **Yes**, as shown in the following illustration. 

![Enable unauthenticated order lookup property set to Yes in headquarters](./media/OrderLookup_enable.PNG)

## Manage the display of personal data

Dynamics 365 Commerce provides options for controlling whether personal information such as the customer's shipping address and the last 4 digits of their credit card are displayed to customers. By default, personal information is not displayed to customers when unauthenticated order lookup is enabled. When unauthenticated order lookup is enabled, you can choose from one of three options in the table below.

| **Option**        | **Result**                                                   |
| ----------------- | ------------------------------------------------------------ |
| **Never** (default)   | Personal information is not displayed in order lookups. Registered users who are signed in and looking up an order they created while signed in will be able to see their personal information. |
| **Guest orders only** | Personal information is displayed in order lookups for orders created as a guest. If the order was created by a registered user, that user must sign in to see their personal information. |
| **All orders**        | Personal information is included in all order lookups.       |

> [!NOTE]
> These options determine when personal data such as customer address and the last four digits of the customer credit card are shown to anonymous guest users. To protect registered customer privacy, it is advised to only set this configuration to **Guest orders only**. The most secure option is to set this configuration to **Never**.

Once you have made any changes to the **Include personal data in guest order lookup** setting, you must run job 1070 (Channel configuration) in headquarters at **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.

## Configure the order lookup module

The form that guest users will use to look up their order is rendered using the Commerce module library order lookup module. The order lookup module can be included in the body slot of any page that does not customer sign-in. For instructions on configuring the module, see [Order lookup module](order-lookup-module.md).

## Additional resources

[Order lookup module](order-lookup-module.md)

[Set up an email notification profile](email-notification-profiles.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
