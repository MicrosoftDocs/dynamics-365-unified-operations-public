---
title: Define channel-specific discounts
description: Learn about the concepts you need to know to create a discount for a specific channel in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 01/22/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
ms.assetid: d807fd51-86aa-47a0-8e00-6c5ddd21ff6b
ms.search.form: RetailAffiliationPriceGroup, RetailCatalogPriceGroup, RetailChannelPriceGroup, RetailDiscountPriceGroup, RetailDiscountPricingWorkspace, RetailPeriodicDiscount, RetailStoreItemPriceList, RetailStoreTable
---

# Define channel-specific discounts

[!include [banner](includes/banner.md)]

This article reviews the concepts you need to know to create a discount for a specific channel in Microsoft Dynamics 365 Commerce.

## Channel-specific discounts

Retailers often offer different discounts in different channels, which might be done to address local market conditions or to deal with competing retailers.

Commerce uses price groups to define channel-specific discounts. You assign price groups to one or more of the following entities: channels, catalogs, affiliations, and loyalty programs. This article discusses channels, but the same concepts apply to catalog discounts, affiliations discounts, and loyalty discounts.

## Price groups

:::image type="content" source="./media/price-groups.png" alt-text="Screenshot of price groups diagram showing relationships between entities and discount types.":::

The preceding diagram illustrates the relationship between entities that can be on a transaction (channel, catalog, affiliation, customer, loyalty card) and the various discount types that you can configure. All transactions occur in a channel, so the channel is always present on a transaction. The remaining entities are optional. On each master data page, a link to a related price groups page lets you view and add price groups as needed. You use a price group to relate four different types of entities to discounts, price adjustments, and trade agreements. Plan a strategy for how you name your price groups to keep them organized. One option is to use a letter or number prefix or suffix to distinguish between the different types. For example, use 1-xxxxx for channel price groups and 2-xxxxx for catalog price groups. Four inquiry pages focus on each of the commerce entities that can have discounts associated to them.

- **Channel channel price groups** – This page shows a list of channels and discounts linked together for each price group.
- **Catalog price groups** – This page shows a list of catalogs and discounts linked together for each price group.
- **Loyalty price groups** – This page shows a list of loyalty programs and discounts linked together for each price group.
- **Affiliation price groups** – This page shows a list of affiliations and discounts linked together for each price group.

## Example channel discount setup

The following example illustrates the tasks involved in setting up a channel discount.

1. For this example, you have a channel called **Houston**, and you're going to create a new discount called **Back-to-School**.
1. Because the pricing and discount strategy includes the possibility of channel discounts, always create a channel-specific price group when you create a channel.
1. You have the price group **Houston-PG** and you assign it to the **Houston** channel.
1. After you create the new **Back-to-School** discount, select **Price groups** at the top of the **Discount** page. The **Discount price groups** page opens. Next, select **New**, and then select the **Houston-PG** price group.
1. Now you can enable the discount and push it to the channel.

## Additional resources

[Price adjustments and discounts](price-adjustments-discounts.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
