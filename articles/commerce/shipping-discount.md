---
title: Shipping discount
description: This article provides an overview of shipping discount capabilities in Microsoft Dynamics 365 Commerce.
author: ShalabhjainMSFT
ms.date: 01/29/2026
ms.topic: overview
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2019-01-31
ms.custom: 
  - bap-template
---

# Shipping discount

[!include [banner](includes/banner.md)]

This article provides an overview of shipping discount capabilities in Microsoft Dynamics 365 Commerce.

Free or discounted shipping is one factor that influences customers' online purchase decisions. To increase their revenue per transaction, many retailers use a free shipping benefit to motivate customers to increase their cart size.

Commerce supports a shipping discount capability that lets retailers configure a discount percentage on the shipping charges for a specific shipping method when the total sales amount for qualified items in the transaction meets specific criteria. An example of a scenario that uses the shipping discount capability is "Spend $50 or more to get free overnight shipping."

## Prerequisites

Commerce's [omni-channel advanced autocharges](/dynamics365/unified-operations/retail/omni-auto-charges) features support the shipping discount capability. For the shipping discount capability to work, you must enable the **Use advanced auto-charges** configuration on the **Customer orders** tab of the **Commerce parameters** page in Commerce headquarters. Retailers can use the advanced auto charges feature to set up various types of charges, such as handling, installation, and disposal.

The shipping discount applies only to shipping charges. Therefore, a retailer must specify which charges are shipping charges. To specify shipping charges, in Commerce headquarters, go to **Channel setup \> Charges \> Charges code**, and set the **Shipping charge** option to **Yes** for the desired charges.

:::image type="content" source="./media/Specify_shipping_charge.png" alt-text="Screenshot of specifying a charge as a shipping charge.":::

## Configuration

The shipping discount capability is tier-based and supports only the **Percentage off** calculation type. To set up a shipping discount, in Commerce headquarters, go to **Pricing and discounts \> Shipping threshold discount**. You can then specify the mode of delivery that the discount applies to, define one or more amount thresholds, and set the discount percentage for each threshold. You can also configure a list of categories or products as qualified items. In that way, only the sales amount against those items in a transaction counts when the pricing engine evaluates whether the transaction total meets the threshold.

> [!NOTE]
> Unlike other discount types, the shipping discount doesn't create discount lines. Instead, it directly edits the shipping charge and appends the name of the discount to the charge description.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
