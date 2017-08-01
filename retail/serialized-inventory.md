---
# required metadata

title:
description: This topic lists improvements that have been made to serialized products to help you save time and be more productive.
author: 
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
# ms.reviewer: josaw
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: Retail
ms.author: shajain
ms.search.validFrom: 2017-08-01
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
---

# POS improvements for serialized products

[!include[banner](includes/banner.md)]

## Overview 
Based on the settings in the retail headquarters (HQ), products can be classified as either serialized or non-serialized. When products are serialized, each item can be assigned its own unique number that helps track warranties, trace items, and confirm ownership. The ability to provide serial numbers for serialized products existed in point of sale (POS), but some improvements have been added to help cashiers save time and be more productive.  

## POS improvements

-  **Serial numbers are not required until checkout** - Previously, when a cashier added a serialized product to the transaction, the cashier was required to provide a serial number. This became an issue during clienteling scenarios if cashiers and sales associates had the opportunity to up-sell the products. Until the payment step, the products were frequently updated in the cart, which meant that each time a cashier added a new product the system prompted for the serial number. The serial number dialog box now includes an **Add later** button, which allows the sales associates to add the item to the transaction and provide the serial number at a later point in time. Sales associates can quickly add and replace serialized items in the cart, and provide the serial number just before checkout. If the serial number is not provided for any serialized product, and the cashier tries to complete the transaction, the system will display an error message, which indicates that the cashier must provide the missing serial numbers before proceeding.

    For each serialized item where the serial number was skipped, a comment will display under the transaction line. This indicates that the serial number is not provided for this item. This helps the cashier to quickly find the items that are missing a serial number.

    A new **Add serial number** operation also provides the serial number for the items that are missing a serial number. After the serial number is provided, it cannot be edited. The cashier must void the line and add the product again. 
	
-  **Serial numbers are not needed for placing the customer orders** - Customer orders can be placed in one store and fulfilled from another. When placing customer orders, the cashier will not need to provide the serial number. The serial number will be provided at the picking or pickup step. However, for all the line items for which the **Carry out** delivery type is selected, the serial number must be provided or the transaction cannot be completed. 
	
-  **Serialized products do not aggregate on the transaction screen** - The **Aggregate products** setting (**Functionality profile** > **Aggregate products** (**Terminal** group) allows you to aggregate the same non-serialized products on the transaction screen. When the same products are aggregated it’s easier to see them on the transaction grid. However, because serial numbers are generally unique and you do not need to enter serial numbers until checkout, the **Aggregate products** setting does not apply to serialized products. This means that serialized products will not be aggregated on the transaction screen if the **Aggregate products** setting is selected.
