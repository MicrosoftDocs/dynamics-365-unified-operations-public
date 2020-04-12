---
# required metadata

title: Product data entities 
description: This topic provides information about the different entities that can be used to import and export product data. 
author: cvocph
manager: tfehr
ms.date: 01/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: conradv
ms.dyn365.ops.version: 7.3 
ms.search.validFrom: 2019-12-1

---

# Product data entities

[!include [banner](../includes/banner.md)]

To import and export product data, you must use data entities. The following table provides details about the product-related data entities and describes the purpose of each.

| Entity | Application Object Tree (AOT) name (type) | Notes |
|--------|-------------------------------------------|-------|
| Products V2 | EcoResProductV2Entity | This entity is used to import and export shared products-distinct products and product masters. It allows for updates. It doesn't support set-based SQL operations. It's enabled for Open Data Protocol (OData). |
| Released products V2 | EcoResReleasedProductV2Entity | This entity is used to import and export released products-distinct products and product masters. It allows for updates. It requires that the shared product already be created. When a new released product is imported, a release of the shared product occurs. There are also separate entities that can be used to import and export released product masters and released distinct variants. This entity doesn't support set-based SQL operations or delete operations. It's enabled for OData. |
| Released product creation V2 | EcoResReleasedProductCreationV2Entity | This entity is used to import shared products and released products in one step. Although it supports exports, that use isn't recommended, because the purpose of the entity is product creation. It doesn't support updates. It supports a limited set of fields (fields that are available in the product creation dialog box). It doesn't support set-based SQL operations. It isn't exposed through OData. |
| Product variants | EcoResProductVariantEntity | This entity is used to import and export shared product variants. It allows for updates. It requires that dimension values already be created. The integration key is the product master plus product dimensions. This entity doesn't support set-based SQL operations. It's enabled for OData. It supports delete operations. It can't be extended through the addition of new product dimensions. |
| Product variants by product number identification | EcoResProductNumberIdentifiedProductVariantEntity | This entity is used to import and export shared product variants. It allows for updates. It requires that dimension values already be created. The integration key is the product number (whereas the integration key for the **Product variants** entity is the product master plus product dimensions). |
| Released product variants | EcoResReleasedProductVariantEntity | This entity is used to import and export released product variants. It allows for updates. It requires that shared product variants already be created. When a new released product variant is imported, a release of the shared product variant occurs. This entity doesn't support set-based SQL operations. It's enabled for OData. Although it supports delete operations, that use currently causes data corruption because of a bug in the current platform. This entity can't be extended through the addition of new product dimensions. |
| Released product variants by product number identification | EcoResProductNumberIdentifiedReleasedProductVariantEntity | This entity resembles the **Released product variants** entity, but the integration key is the product number instead of the product master plus product dimensions. It can be extended through the addition of new product dimensions. |
| Sellable released products | EcoResSellableReleasedProductEntity | This entity is used to export only sellable products. Sellable products are products that have the information that they require in order to be used in a sales order. The same rules apply when a product is validated by using the **Validate** function on the **Released products** page. |
| Released Distinct products V2 | EcoResDistinctProductV2Entity | This entity is used to export distinct products. Those distinct products can be products, subtype products, and product variants. |
| Released products masters V2 | EcoResProductMasterV2Entity | This entity is used to import and export product masters. It isn't enabled for data management. |
| Item - bar code | EcoResProductBarcodeEntity | This entity is used to export products and bar codes. |
| Product lifecycle states | EcoResProductLifecycleSateEntity | This entity is used to import and export the different product lifecycle states that can be assigned to a product. |

> [!NOTE]
> You can use the **Released Products V2** data entity to import products into the system only if the shared product has already been created. Otherwise, to import products into the system, you must use the **Product creation** data entity.
