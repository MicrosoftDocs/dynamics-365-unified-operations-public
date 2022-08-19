---
# required metadata

title: Shipping discount
description: This article describes the shipping discount capabilities within Microsoft Dynamics 365 Commerce and the corresponding setup steps required to start using these discount capabilities.
author: ShalabhjainMSFT
ms.date: 08/19/2020
ms.topic: overview
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2019-01-31
 
---

# Shipping discount

[!include [banner](includes/banner.md)]

This article describes the shipping discount capabilities within Microsoft Dynamics 365 Commerce and the corresponding setup steps required to start using these discount capabilities.

Free or discounted shipping is one of the influencing factors driving the customers' online purchase decisions. Many retailers also employ a free shipping benefit to motivate customers to increase their cart size, increasing the revenue per transaction. 

Commerce supports a shipping discount capability that allows retailers to configure a discount percentage on shipping charges for a specific shipping method when the total sales amount of qualified items in the transaction meet certain criteria. An example of this would be "Spend $50 or more to get free overnight shipping".

## Prerequisite

The shipping discount capability is supported by Commerce's [Omni-channel advanced auto charges](/dynamics365/unified-operations/retail/omni-auto-charges) features. For the shipping discount capability to work, in COmmerce headquarters you must enable the **Use advanced auto-charges** configuration on the **Commerce parameters \> Customer orders** tab. Retailers can use the advanced auto charges feature to set various types of charges such as handling, installation, and disposal. The shipping discount is only applied to the shipping charges, so the retailer must specify which of the charges are shipping charges. To specify a shipping charge, in Commerce headquarters go to **Channel setup \> Charges \> Charges code** and turn on the **Shipping charge** toggle for the desired charges. 

![Specify a charge as shipping charge.](./media/Specify_shipping_charge.png)

## Configuration

The shipping discount capability is tier-based, and only supports the **Percentage off** calculation type. To set up a shipping discount, in Commerce headquarters go to **Pricing and discounts \> Shipping threshold discount**. There you can specify the mode of delivery for which the discount applies, define one or more amount thresholds, and set the discount percentage for each threshold. You can also configure a list of categories or products as qualified items so that only the sales amount against those items in a transaction is counted when the pricing engine evaluates whether the transaction total meets the threshold.

> [!NOTE]
> Unlike other discount types, the shipping discount does not create discount lines. Instead, the shipping discount edits the shipping charge directly and appends the name of the discount to the charge description. 

[!INCLUDE[footer-include](../includes/footer-banner.md)]
