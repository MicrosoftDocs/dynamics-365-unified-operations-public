---

# required metadata

title: Changes to price and discount extensibility for Dynamics 365 for Finance and Operations, Enterprise edition 7.3
description: This topic describes the changes to price and discount extensibility for Dynamics 365 for Finance and Operations, Enterprise edition 7.3.
author: smithanataraj
manager: AnnBe
ms.date: 12/10/2017
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

# Changes to price and discount extensibility for Dynamics 365 for Finance and Operations, Enterprise edition 7.3

In Dynamics 365 for Finance and Operations, Enterprise edition 7.3 and later, the pricing area is extensible. Some common seen customization in the pricing area are:
- Adding new price group types and the corresponding price types (enum values for PriceType and PriceGroupType) and adding search mechanisms for the new price types.
- Modifying the price and discount search, including passing in any additional parameters to the PriceDisc class. 

The solution here is targeting to address the above.

## PriceType and PriceGroupType enums:

Typically, adding a new type of price discount search would start with adding a new enum value in the two enums - PriceGroupType and PriceType. To enable these for extensibility, the behavior around the PriceGroupType  and PriceType enum values are now encapsulated in the class hierarchies PriceGroupTypeTradeAgreementMapping and PriceTypeTradeAgreementMapping respectively. These should be extended for any new PriceGroupType and PriceType extended enum values.

PriceTypeTradeAgreementMapping would also be where the mapping of fields on the Customer/Vendor tables or InventTable table corresponding to the price types, is defined. 

NOTE: In the diagram below, the methods are only shown on one of the sub-classes (only for the purpose of illustration), though the implementation needs to be on each. 

![PriceGroupTypeTradeAgreementMapping](media/PricingFall20171.png)

## PriceDisc class: 

The PriceDisc class is the search engine for price and discounts. This class will now use a PriceDiscParameters object as a member for passing in the parameters, used in the price and discount search. This should enable passing in the additional search parameters for the specific solutions.

Only the parameters specific for a given PriceGroupType search are passed through the corresponding find methods on the PriceDisc class. 

The possibility to wrap and modify the instantiation of the PriceDiscParameters class is enabled for all price and discount search calls made throughout AppSuite.

Below you can see how the PriceDisc class can be extended to modify existing searches or to add a new search method corresponding to the new extended PriceType enum values.

![PriceDiscClass](media/PricingFall20172.png)

## Walkthrough: Add a new price search

Let's say we have extended the PriceGroupType enum with a new value  PriceGroupTypeISVExtension, and two corresponding PriceType enum values - ISVPurchPriceType and ISVSalesPriceType. 

![WalkThrough1](media/PricingFall20173.png)

The below diagram illustrates how a new price search can be added for the above PriceGroupType and PriceType values added:

![WalkThrough2](media/PricingFall20174.png)

In this example:

1. For the newly created PriceGroupType value, a PriceGroupTypeTradeAgreementMappingISVPriceGroupType class decorated with the attribute ISVPriceGroupType should define the behavior of the price group type.
2. For the newly created PriceType value, the PriceTypeTradeAgreementMappingISVPurchPriceType and PriceTypeTradeAgreementMappingISVSalesPriceType classes corresponding to Purchase and Sales would be implemented.
3. The PriceDiscParameters class should be augmented to add any generic parameters for the price discount search.
4. The PriceDisc class should be augmented to create the new price discount search methods for the new price types.

The PriceDiscParameters is accessible from all classes related to price and discount search and these could be augmented, based on the requirements. 
