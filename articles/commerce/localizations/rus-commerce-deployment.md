---
# required metadata

title: Set up and deploy the Dynamics 365 Commerce localization for Russia
description: This topic covers how to set up and deploy the Microsoft Dynamics 365 Commerce localization for Russia.
author: akviklis@microsoft.com
ms.date: 07/02/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer
# ms.devlang: 
ms.reviewer:
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
ms.search.industry: Retail
ms.author: akviklis
ms.search.validFrom: 07/01/2021
ms.dyn365.ops.version: 

---
# Set up and deploy the Dynamics 365 Commerce localization for Russia

[!include[banner](../includes/banner.md)]

This topic covers how to set up and deploy the Microsoft Dynamics 365 Commerce localization for Russia.

For more information about the Commerce localization for Russia, see [Russian localization scope](../../finance/localizations/russia.md) and [Commerce localization for Russia](rus-commerce-localization.md).

## Enable Russia-specific Commerce functionality

This section describes how to configure Commerce headquarters settings that are specific to and recommended for Russia. For more information, see the [Commerce home page](../index.md).

To enable and use the Russia-specific functionality, you must configure the following settings in Commerce headquarters.

1. In the primary address of the legal entity, set the **Country/region** field to **RUS** (Russia).
1. In the POS functionality profile of every store that is located in Russia, set the **ISO** field to **RU** (Russia).
1. Go to **System administration \> Workspaces \> Feature management**, and then, on the **All** tab, enable the following feature keys:

    - (Russia) Customer information management in Retail POS
    - Enable Russian simplified customer address format

## Set up address books

To add the same address book for Russian customers, stores, and workers in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Customers \> All customers**.
1. On the **General** tab, in the **Address books** field, add retail address books for customers as required.
1. Go to **Retail and Commerce \> Channels \> Stores \> All stores**.
1. On the **General** tab, in the **Customer address book** and **Employee address book** fields, add the address books for the stores.
1. Go to **Retail and Commerce \> Employees \> Workers**.
1. On the **Worker summary** tab, in the **Address books** field, add the address books for workers.

## Customer information management

**(Russia) Customer information management in Retail POS** feature impacts the Retail POS functionality for Russia. It enables the inquiry of customer information (such as email address or phone number) in sales transactions.

## Customer account deposit

The **Customer account deposit** feature can be used to make prepayments at the Retail point of sale (POS). for more information see [Prepaymants in Retail for Russia](rus-commerce-prepayments.md).

To configure the **Customer account deposit** operation in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS \> Button grids**.
1. Select the button grid where the operation should appear, and then open **Button grid designer**.
1. Add a button, and then, in the **Action** field, select **Customer account deposit**.

For more information about how to work with screen layouts and button grids, see [Screen layouts for the point of sale (POS)](../pos-screen-layouts.md).

## Set up parameters for statements

1. Go to **Organization administration \> Number sequences**.
1. Create and set up number sequences for retail statements for each store (operating unit).
1. On the **References** FastTab, add two references for the **Retail store** area: one where the **Reference** value is set to **Statement number** and one where it's set to **Voucher**.
1. Go to **Retail and Commerce \> Catalog and assortments**.
1. Create an assortment that includes appropriate products.
1. On the **Commerce channels** tab, add the stores that you created earlier. Then select **Publish**.
1. Go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes**, and publish channel updates.
1. Go to **Sales and marketing \> Setup > Returns \> Disposition codes**, and add a disposition code.
1. Go to **Retail and commerce \> Products and categories \> Released products by category**.
1. Select a product for the gift card, and then select the **Blocked at register** check box.
1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
1. On the **Customer orders** tab, enter the disposition code that you added earlier.
1. On the **Posting** tab, set up the parameters for the gift card. These parameters include the **Gift card company** and **Gift card product** fields.

## Additional resources

[Commerce localization for Russia](rus-commerce-localization.md) 

[Prepaymants in Retail for Russia](rus-commerce-prepayments.md)
