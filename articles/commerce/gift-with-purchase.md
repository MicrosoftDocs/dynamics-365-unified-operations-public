---
# required metadata

title: Configure gift with purchase promotions
description: This topic describes how to configure "gift with purchase" promotions in Microsoft Dynamics 365 Commerce.
author: shalabh
ms.date: 04/23/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: shajain
ms.search.validFrom: 2020-10-31
ms.dyn365.ops.version: AX 7.0.1

---

# Configure gift with purchase promotions

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic describes how to configure "gift with purchase" promotions in Microsoft Dynamics 365 Commerce.

It is a common practice among retailers to run "gift with purchase" promotions to persuade customers to buy a product at full price with the bonus of getting an additional item  for free or at a discount. Such promotions can help sell slow-moving products and (if executed correctly) improve the overall customer experience. Retailers can use the Commerce threshold discount feature to configure such promotions starting with the Dynamics 365 Commerce version 10.0.19 release.

## Threshold discount feature

As of the Commerce version 10.0.19 release, the **Discount method** column on the **Threshold discount tiers** FastTab in Commerce headquarters at **Retail and Commerce \> Pricing and discounts \> Threshold discounts** shows a new value named **Discount lines**. If the **Discount lines** discount method is selected, a new FastTab named **Threshold discount lines** appears at the bottom of the **Threshold discounts** form. 

The items listed on the **Lines** FastTab should be considered as the qualification items, while the items listed on the **Threshold discount lines** FastTab should be considered as the discounted items. The threshold amount specified under **Lines** is checked against the qualifying lines to determine if the threshold has been met. If the threshold is met, then the items listed under the **Threshold discount lines** will get the discount. 

## Promotion configuration examples

You can also specify the quantity of items that should be discounted when the threshold is met. For example, if you wanted to run a promotion for customers to "spend $200 on dress shirts and get two ties for free," under **Threshold discount lines** you would create a new threshold discount tier with "$200" as the **Amount** and **Discount lines** as the **Discount method**. Next, you would select the **Dress Shirts** category on the **Lines** FastTab (qualifying items) and add the **Ties** category on the **Threshold discount lines** FastTab (discounted items). For the **Ties** category, you would then enter "100.00" under **Deal price/Discount percent** to take 100% off the price, and enter "2.00" under **Quantity limit** to restrict the discounted items to a maximum of two items. With this configuration, when dress shirts worth more than $200 are added to the transaction, and then some ties are added to the transaction, up to two ties will be provided to the customer for free. 

The following image shows the configuration for the "spend $200 on dress shirts and get two ties for free" promotion example in Commerce headquarters. 

![Gift with purchase example configuration in Commerce headquarters](./media/gift-with-purchase.png)

As mentioned above, the **Quantity limit** column on the **Threshold discount lines** FastTab allows you to restrict the number of items that should be discounted. But if this field is set to "0.00," there is no restriction on how many items can be discounted. Using the previous example, if the **Quantity limit** was instead set to "0.00," once customers met the qualifying threshold they could get any number of ties for free. 

Another thing to note is that you can add multiple items in the **Threshold discount lines** FastTab to indicate all of the items that should be discounted. For example, you could add one row for two ties and one row for two bow ties. This will be interpreted as "spend $200 on shirts and get 2 ties *and* 2 bow ties for free. 

If the requirement was to give two ties *or* two bow ties for free (or 1 tie and 1 bow tie for free), then you would need to create a new category for tie and bows so that the tie and bow tie discounts could be configured in a single row.

## View available discounts feature

Sales associates and customers can find out at the point of sale (POS) that a transaction has qualified for free or discounted items by using the "View available discounts" feature, which shows all applicable discounts for a given transaction. For more information about the "View available discounts" feature, see [Cross-sell and upsell by using discounts](discounts-pos.md#cross-sell-and-upsell-by-using-discounts).

## Additional resources

