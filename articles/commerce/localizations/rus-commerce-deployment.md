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
1. In the POS functionality profile of every store that is located in Brazil, set the **ISO code** field to **RU** (Russia).
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

## Set up sales tax for POS

To set up sales tax for POS in Commerce headquarters, follow these steps.

1. Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax codes**.
1. Create the required sales tax codes for different tax types and taxation codes. Include sales tax codes for returns.
1. Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax group**.
1. Create sales tax groups for retail sales and returns, and add the sales tax codes that you just created.
1. Go to **Retail and Commerce \> Channels \> Stores \> All stores**.
1. In the **Sales tax group** and **Sales tax group for returns** fields, select the sales tax groups that you just created.
1. Go to **Tax \> Indirect taxes \> Sales tax \> Item sales tax groups**.
1. Create item sales tax groups for retail, and add the sales tax codes that you created earlier.
1. Go to **Retail and Commerce \> Products and categories \> Released products by category**.
1. Select the desired products, and set the following fields:

    - On the **Sell** tab:

        - Item sales tax group

## Set up a retail store

To set up a retail store in Commerce headquarters, follow these steps.

1. Go to **Inventory management \> Setup \> Inventory breakdown \> Warehouses**.
1. Create warehouses for the stores, and specify addresses.
1. Go to **Retail and Commerce \> Channels \> Stores \> All stores**.
1. Create the stores, and set the following Brazil-specific fields:

    - Prices include sales tax
    - Sales tax group
    - Sales tax group for returns
    - Default customer

        > [!NOTE]
        > The default customer should be included in the same address book as the store.

1. Set up payment methods for the stores that you created in the previous step.
1. Go to **Retail and Commerce \> Headquarters setup \> Commerce scheduler**.
1. Add the stores that you created earlier to the channel database that is used.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> Registers**.
1. Create POS registers
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> Devices**.
1. Create and configure devices for the POS registers that you just created.
1. Go to **Organization administration \> Organizations \> Organization hierarchies**.
1. Select **Retail Stores by Business Unit** organization hierarchy, select **View**, select **Edit \> Insert retail channel**, and add the stores that you created earlier to the appropriate business units in the hierarchy. Then publish the changes.
1. Assign the **Retail POS posting** purpose to the **Retail Stores by Business Unit** organization hierarchy.
1. Go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes**.
1. Publish the channel updates.
1. Go to **Retail and Commerce \> Channel setup \> POS profiles \> Receipt profiles**.

## Customer information management

**(Russia) Customer information management in Retail POS** feature impacts the Retail POS functionality for Russia. It enables the inquiry of customer information (such as email address or phone number) in sales transactions.

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
