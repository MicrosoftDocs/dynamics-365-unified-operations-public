---
title: Configure gift with purchase promotions
description: Learn how to configure gift with purchase promotions in Microsoft Dynamics 365 Commerce.
author: ShalabhjainMSFT
ms.date: 02/17/2026
ms.topic: how-to
ms.author: shajain
ms.reviewer: v-griffinc
ms.search.region: Global
ms.search.validFrom: 2020-10-31
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.custom: 
  - bap-template
---

# Configure gift with purchase promotions

[!include [banner](../../finance/includes/banner.md)]

This article describes how to configure "gift with purchase" promotions in Microsoft Dynamics 365 Commerce.

Retailers often run "gift with purchase" promotions. The goal is to persuade customers to buy a product at full price by offering a bonus of an extra item for free or at a discount. These promotions can help sell slow-moving products and (if they're run correctly) can also help improve the overall customer experience. As of the Dynamics 365 Commerce version 10.0.19 release, retailers can use the "Threshold discount" feature to configure these promotions.

## Threshold discount feature

As of the Commerce version 10.0.19 release, a new **Discount lines** value is available for selection in the **Discount method** field on the **Threshold discount tiers** FastTab of the **Threshold discounts** page in Commerce headquarters (**Retail and Commerce \> Pricing and discounts \> Threshold discounts**). If you select the **Discount lines** discount method, a new FastTab named **Threshold discount lines** appears at the bottom of the page.

Consider the items listed on the **Lines** FastTab of the **Threshold discounts** page as the qualifying items for a promotion. Consider the items listed on the **Threshold discount lines** FastTab as the discounted items. The threshold amount that you specify on the **Lines** FastTab is checked against the qualifying lines to determine whether the threshold is met. If the threshold is met, the discount is applied to the items listed on the **Threshold discount lines** FastTab.

> [!NOTE]
> Don't include the discounted items in the qualifying items. If you do, from discount calculation perspective, those items aren't considered as gifts.

## Promotion configuration examples

Use the **Quantity limit** field on the **Threshold discount lines** FastTab to specify (and therefore limit) the number of items that are discounted when the threshold is met. For example, you want to run a promotion where customers who spend $200 on dress shirts get two ties for free. On the **Threshold discount lines** FastTab, you create a new threshold discount tier. You enter **200.00** in the **Amount** field and select **Discount lines** in the **Discount method** field. Next, on the **Lines** FastTab, you select the **Dress Shirts** category to specify the qualifying items. On the **Threshold discount lines** FastTab, you select the **Ties** category to specify the discounted items. Finally, for the **Ties** category, you enter **100.00** in the **Deal price/Discount percent** field to take 100 percent off the price, and you enter **2.00** in the **Quantity limit** field to limit the number of discounted items to a maximum of two items. Now, when dress shirts that total more than $200 are added to a transaction, and some ties are also added to the transaction, up to two ties are provided to the customer for free.

The following illustration shows the configuration for the "spend $200 on dress shirts and get two ties for free" promotion example in Commerce headquarters.

:::image type="content" source="../media/gift-with-purchase.png" alt-text="Screenshot of the gift with purchase example configuration in Commerce headquarters.":::

As mentioned, the **Quantity limit** field on the **Threshold discount lines** FastTab lets you limit the number of items that are discounted. If you set this field to **0.00**, there's no limit on the number of items that can be discounted. Therefore, for the previous example, if you set the **Quantity limit** field for the **Ties** category to **0.00**, customers who meet the qualifying threshold can get any number of ties for free.

Add multiple items to the **Threshold discount lines** FastTab to indicate the items that are discounted. For the previous example, if you add one row for two ties and another row for two bow ties, the system interprets this configuration as "spend $200 on dress shirts, and get two ties *and* two bow ties for free." If the promotion should instead involve giving two ties *or* two bow ties for free (or one tie and one bow tie), create a new category for ties and bow ties, so that the tie and bow tie discounts can be configured on a single row.

## View available discounts feature

The **View available discounts** feature helps sales associates and customers learn, at the point of sale (POS), that a transaction qualifies for free or discounted items. This feature shows all applicable discounts for a given transaction. For more information about the **View available discounts** feature, see [Cross-sell and upsell by using discounts](../discounts-pos.md#cross-sell-and-upsell-by-using-discounts).

## Additional resources

[Cross-sell and upsell by using discounts](../discounts-pos.md#cross-sell-and-upsell-by-using-discounts)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]