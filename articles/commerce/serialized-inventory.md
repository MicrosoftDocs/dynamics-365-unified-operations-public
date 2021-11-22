---
# required metadata

title: Point of sale (POS) improvements for serialized products
description: This topic lists improvements that have been made to serialized products to help you save time and be more productive.
author: ShalabhjainMSFT
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: shajain
ms.search.validFrom: 2017-08-01
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
---

# Point of sale (POS) improvements for serialized products

[!include [banner](includes/banner.md)]

## Overview

Based on the settings in Commerce Headquarters, products can be classified as either serialized or non-serialized. When products are serialized, each item can be assigned a unique number that helps track warranties, trace items, and confirm ownership. Although, the ability to provide serial numbers for serialized products existed in our Modern/Cloud Point of Sale (POS), some improvements have been added to help cashiers save time and be more productive.

## POS improvements

- **Serial numbers aren't required until checkout** – Previously, a cashier who added a serialized product to the transaction was required to provide a serial number. This requirement became an issue in clienteling scenarios, if cashiers and sales associates had an opportunity to up-sell products. Until the payment step, the products were often updated in the cart. Therefore, every time that a cashier added a new product, the system prompted the cashier for the serial number. The serial number dialog box now includes an **Add later** button. Therefore, the sales associates can add the item to the transaction but can provide the serial number later. Sales associates can quickly add and replace serialized items in the cart, and then provide the serial number just before checkout. If the serial number isn't provided for any serialized product, a cashier who tries to complete the transaction receives an error message. This messages that states that the cashier must provide the missing serial numbers before the cashier can continue.

    For each serialized item where the serial number was skipped, a comment appears under the transaction line. This comment states that the serial number hasn't been provided for the item. Therefore, the cashier can quickly find items that are missing a serial number.

    A new **Add serial number** operation also provides the serial number for items that are missing a serial number. After the serial number is provided, it can't be edited. The cashier must void the line and add the product again.
	
- **Serial numbers aren't required in order to place customer orders** – Customer orders can be placed in one store and fulfilled from another. A cashier who places a customer order doesn't have to provide the serial number. The serial number will be provided during the picking or pickup step. However, a serial number must be provided for all line items that the **Carry out** delivery type is selected for. Otherwise, the transaction can't be completed.
- **Serialized products aren't aggregated on the transaction screen** – The **Aggregate products** setting in the **Terminal** field group on the **Functionality profile** page lets you aggregate the same non-serialized products on the transaction screen. When the same products are aggregated, they are easier to see in the transaction grid. However, because serial numbers are generally unique, and sales associates don't have to enter serial numbers until checkout, the **Aggregate products** setting doesn't apply to serialized products. Therefore, serialized products won't be aggregated on the transaction screen if the **Aggregate products** setting is selected.
- **Ability to search the journals by serial number** – The journals can now be additionally searched by serial numbers. To do so, open the "Journals" operation and press the "Advanced search" button in the app bar. Using the "Add filter" button, a filter can be applied to search for the serial numbers as well.


[!INCLUDE[footer-include](../includes/footer-banner.md)]