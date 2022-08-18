---
# required metadata

title: Shipping discount
description: This article describes the shipping discount capabilities within Dynamics 365 Commerce and the corresponding setup steps required to start using these discounts.
author: ShalabhjainMSFT
ms.date: 01/22/2020
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailShippingThresholdDiscounts, RetailPriceDiscGroup
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 

ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: shajain
ms.search.validFrom: 2019-01-31
ms.dyn365.ops.version: 


---

# Shipping discount

[!include [banner](includes/banner.md)]

This article provides an overview of the shipping discount capability available within Dynamics 365 Commerce. 

Free or discounted shipping is one of the highly influencing factors driving the customers' online purchase decisions. Many retailers also leverage the free shipping benefit to motivate the customers to increase their basket size, thus increasing the revenue per transaction. 

Commerce supports shipping discount that lets retailers configure a discount percentage that is applied to the shipping charge for specific shipping method when qualified items in the transaction meet certain amount threshold. For example, spend $50 or more to get free "Overnight shipping".

## Prerequisite

Shipping discount leverages the [Omni-channel advanced auto charges](/dynamics365/unified-operations/retail/omni-auto-charges) capability. Therefore, the **Use advanced auto-charges** configuration on the **Commerce parameters \> Customer orders** tab must be enabled for shipping discount to work. Retailers can use the advanced auto charges feature to set various types of charges such as handling, installation, and disposal. However, the shipping discount is only applied to the shipping charges. Thus, the retailer needs to specify which of the charges are shipping charges. To specify a shipping charge, in Commerce headquarters go to **Channel setup \> Charges \> Charges code**. Turn on the **Shipping charge** toggle for the desired charges. This is the only prerequisite for using the shipping discount 

![Specify a charge as shipping charge.](./media/Specify_shipping_charge.png " Specify a charge as shipping charge ")

## Configuration

Shipping discount only supports **Percentage off** calculation type, and is tier-based. To set up a shipping discount, in Commerce headquarters, go to **Pricing and discounts \> Shipping threshold discount**, and **New** a discount there. You can specify the mode of delivery (such as "Standard overnight" or "Two-day shipping") for which this discount applies, define one or more amount thresholds, and set the discount percentage for each threshold. You can also configure a list of categories or products as qualified items, so that only sales amount against those items in a transaction are counted when the pricing engine evaluates whether the transaction total meets the threshold.

Like other discount types, shipping discount honors all the existing standard discount capabilities, such as allowing the retailer to restrict the discounts with coupons so that only the customers with coupons can get the discounts. Also, these discounts leverage the Price groups capability to determine the eligibility of the discount. For example, the retailer can choose to run these promotions only in the online channels and/or across channels for certain customer groups such as loyalty customers. Lastly, to view the charges applied on the sales lines and the applied promotion, you need to add **Manage charges** on the POS screen. Run the **1020**, **1040**, **1090**, and **1110** distribution schedules to send the charges, shipping discount, and screen layout information to the channels. 

> [!NOTE]
> Unlike other discount types, the shipping discount does not create discount lines. Instead, the shipping discount edits the shipping charge directly and appends the name of the discount to the charge description. 

[!INCLUDE[footer-include](../includes/footer-banner.md)]
