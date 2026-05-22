---
title: Price and discount extensibility
description: Learn about how to extend pricing functionality, including overviews of the PriceType and PriceGroupType enums and PriceDisc class.
author: smithanataraj
ms.author: smnatara
ms.topic: article
ms.date: 03/27/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-12-10
ms.dyn365.ops.version: Platform update 11
---

# Price and discount extensibility

[!include [banner](../includes/banner.md)]

In finance and operations, Enterprise edition 7.3 and later, you can extend the pricing area. Common customizations for price and discounts include:

- Adding new price group types and the corresponding price types (enum values for **PriceType** and **PriceGroupType**), along with search mechanisms for the new price types.
- Modifying the price and discount search, including passing in any additional parameters to the **PriceDisc** class.

## PriceType and PriceGroupType enums

Typically, you add a new type of price discount search by adding a new enum value in the two enums: **PriceType** and **PriceGroupType**. To support extensibility, the class hierarchies **PriceGroupTypeTradeAgreementMapping** and **PriceTypeTradeAgreementMapping** now encapsulate **PriceType** and **PriceGroupType** enum values, respectively. You can extend these classes for any new **PriceType** and **PriceGroupType** extended enum values.

The **PriceTypeTradeAgreementMapping** class defines the mapping of fields on the **Customer**, **Vendor**, and **InventTable** tables that correspond to the price types.

The following diagram highlights the implementation. The methods show only one of the sub-classes. The implementation needs to be on each sub-class.

:::image type="content" source="media/PricingFall20171.png" alt-text="Screenshot of PriceGroupTypeTradeAgreementMapping.":::

## PriceDisc class

The **PriceDisc** class is the search engine for price and discounts. This class uses a **PriceDiscParameters** object as a member for passing in the parameters that are used in the price and discount search. By using this approach, you can pass in the additional search parameters for the specific solutions. Only the parameters for a given **PriceGroupType** search are passed through the corresponding find methods on the **PriceDisc** class.

You can wrap and modify the instantiation of the **PriceDiscParameters** class for all price and discount search calls made throughout AppSuite.

In the following diagram, you can see how the **PriceDisc** class can be extended to modify existing searches or to add new search methods that correspond to the extended **PriceType** enum values.

:::image type="content" source="media/PricingFall20172.png" alt-text="Screenshot of PriceDisc class diagram.":::

## Add a new price search

In this scenario, you extend the **PriceGroupType** enum with a new value **PriceGroupTypeISVExtension**, and add two corresponding **PriceType** enum values - **ISVPurchPriceType** and **ISVSalesPriceType**.

:::image type="content" source="media/PricingFall20173.png" alt-text="Screenshot of walkthrough diagram showing extended PriceGroupType and PriceType enum values.":::

The following diagram illustrates how you can add a new price search for the **PriceType** and **PriceGroupType** values.

:::image type="content" source="media/PricingFall20174.png" alt-text="Screenshot of walkthrough diagram illustrating how a new price search can be added.":::

This example shows the following steps:

- For the newly created **PriceGroupType** value, create a **PriceGroupTypeTradeAgreementMappingISVPriceGroupType** class decorated with the attribute **ISVPriceGroupType** to define the behavior of the price group type.
- For the newly created **PriceType** value, create the **PriceTypeTradeAgreementMappingISVPurchPriceType** and **PriceTypeTradeAgreementMappingISVSalesPriceType** classes that correspond to Purchase and Sales.
- Augment the **PriceDiscParameters** class to add any generic parameters for the price discount search.
- Augment the **PriceDisc** class to create the new price discount search methods for the new price types.
- Since all classes related to price and discount search can access **PriceDiscParameters**, you can augment these classes based on your requirements.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
