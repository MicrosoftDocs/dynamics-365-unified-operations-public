---
# required metadata

title: Configure a product to be purchased for free
description: This topic describes how to configure a product to be purchased for free in Microsoft Dynamics 365 Commerce. 
author:  anupamar-ms
ms.date: 05/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 
---

# Configure a product to be purchased for free

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes how to configure a product to be purchased for free in Microsoft Dynamics 365 Commerce. 

## Configure the Zero price valid setting

To sell a product for free in Dynamics 365 Commerce, in addition to setting up the free product with a price of "0", you must also configure the product's **Zero price valid** setting to **Yes**. 

To configure the **Zero price valid** setting in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Products and categories > Released products by category**.
1. Navigate to the product that you want to sell for free. 
1. In the **Commerce** section of the product form, set **Zero Price Valid** toggle to **Yes**.

The following example illustration shows a product with the **Zero price valid** toggle set to **Yes**. 

![An example of a product with the Zero price valid toggle set to Yes](./media/Zero-price.png)

## Configure the functionality profile for the online store

To allow free transactions to be processed, the functionality profile for your online store in Commerce headquarters should be updated to allow transactions with no payments. For information on creating functionality profiles, see [Create an online functionality profile](online-functionality-profile.md).

To configure the **Allow checkout with no payments** setting in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> Online store setup**.  
1. On your store's functionality profile page, under **CHECKOUT** set the **Allow checkout with no payments** toggle to **Yes**. 

The following example illustration shows an online store profile with the **Allow checkout with no payments** toggle set to **Yes**. 

![Example of allow checkout with no payments.](./media/Zero-price-profile.png)

## Additional resources

[Retail sales price management](price-management.md)

[Create an online functionality profile](online-functionality-profile.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
