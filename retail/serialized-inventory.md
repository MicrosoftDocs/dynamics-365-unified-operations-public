---
# required metadata

title:
description: 
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
Based on the settings in the retail HQ, products can be classified as either serialized or non-serialized. When products are serialized, each item can be assigned its own unique number that helps track warranties, trace items, and confirm ownership. The ability to provide serial numbers for serialized products existed in POS, but we have made some improvements which saves time for the cashiers and thus make them more productive.  

## POS Improvements

1. **Serial numbers are not required until checkout** 
Previously, whenever the cashiers added a serialized product to the transaction, they were required to provide a serial number. This became a hindrance during clienteling scenarios, where the cashiers and sales associates have the opportunity to up-sell the products, because, until the payment step, the products are frequently updated in the cart and thus each time a cashier added a new product, the system prompted for the serial number. We have now updated the serial number dialog to add a new button named "Add later", which enables the sales associates to skip providing the serial number while adding the item to transaction. Thus, until the customer is satisfied, the associates can quickly add and replace serialized items in the cart, and provide the serial number just before checkout. If the serial number is not provided for any serialized product, and the cashier tries to complete the transaction, then the system will throw an error message indicating that the cashier must provide the missing serial numbers before proceeding.

    Each serialized item, for which the serial number was skipped, we display a comment under the transaction line, indicating that the serial number is not provided for this item. This helps the cashiers to quickly find the items which are missing the serial number.

    We have also introduced a new operation named "Add serial number", which can be used to provide the serial number for the items missing the serial number. Once the serial number is provided, then it cannot be edited and the cashiers must void the line and add the product again. 
	
2. **Serial numbers are not needed for placing the customer orders** 
The customer orders can be placed from one store and fulfilled from another. So at the time of placing customer orders, the cashiers will not have to provide the serial numbers anymore. The serial numbers will be provided at the picking or pickup step. However, all the line items, for which the delivery type is selected as 'Carry out', the serial number must be provided or else the transaction cannot be completed. 
	
3. **Serialized products do not aggregate on the transaction screen**	
The functionality profile currently provides a setting named "Aggregate products" to aggregate the same products on the transaction screen. This is great for the non-serialized products as the transaction grid becomes more readable. However, for the serialized products this becomes a problem as the serial number can be added once per transaction line. Thus, with the current release, the serialized products will never be aggregated on the transaction screen even if the ""Aggregate products" setting is turned on.
