---

# required metadata

title: Price and discounts changes in the Fall Release 2017
description: This topic describes the changes in the price and discount area in the Fall Release 2017.
author: smithanataraj
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 89563
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: smnatara
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 11
---

# Price and discounts changes in the Fall Release 2017

This is an overview of the changes being done to make the pricing area extensible. Pricing is a heavily customized area and modifying the price search is currently impossible without overlayering. This article outlines the changes part of the Fall Release 2017 in the pricing area.

You would be interested to read this if you currently have any customizations around the price and discount search in Dynamics 365. 

Some of the most commonly seen customizations in the pricing area are:

	1. Adding new price group types and the corresponding price types (enum values for PriceType and PriceGroupType) and adding search mechanisms for the new price types.
	2. Modifying the price and discount search, including passing in any additional parameters to the PriceDisc class. 

The proposed solution here is targeting to address the above.

## PriceType and PriceGroupType enums:

Typically, adding a new type of price discount search would start with adding a new enum value in the two enums - PriceGroupType and PriceType. To enable these for extensibility, the behavior around the PriceGroupType  and PriceType enum values are now encapsulated in the class hierarchies PriceGroupTypeTradeAgreementMapping and PriceTypeTradeAgreementMapping respectively. These should be extended for any new PriceGroupType and PriceType extended enum values.

PriceTypeTradeAgreementMapping would also be where the mapping of fields on the Customer/Vendor tables or InventTable table corresponding to the price types, is defined. 

NOTE: In the diagram below, the methods are only shown on one of the sub-classes (only for the purpose of illustration), though the implementation needs to be on each. 


![PriceGroupTypeTradeAgreementMapping](media/PricingFall20171.png)
