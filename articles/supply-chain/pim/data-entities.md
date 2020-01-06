---
# required metadata

title: Use product data entities 
description: This topic provides information about the different entities that can be used to import and export product data. 
author: cvocph
manager: AnnBe
ms.date: 01/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: josaw
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

# Use product data entities

[!include [banner](../includes/banner.md)]

To import and export product data, you must use data entities. The table below details the product-related data entities and the pupose of each.

|    Entity                                                          |    AOT Name (type)                                              |    Notes/Final text.   Purpose                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |   |   |
|--------------------------------------------------------------------|-----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|
|    Products V2                                                     |    EcoResProductV2Entity                                        |    Import and export of shared products   - both distinct products and product masters.    Allow updates.   Does not support set based SQL   operations.    Enabled for Odata                                                                                                                                                                                                                                                                                                                                           |   |   |
|    Released products V2                                            |    EcoResReleasedProductV2Entity                                |    Import and export of released products   - both distinct products and product masters. Allow updates. Requires that shared product is already   created. When new released product is imported, a release of the shared   product is made behind the scenes.        Note that there are also separate entities for the import   and export of released product masters and released distinct variants.        Does not support set based SQL   operations.    Enabled for Odata.   Does not support deletes.         |   |   |
|    Released product creation V2                                    |    EcoResReleasedProductCreationV2Entity                        |    Import of shared product and released   product in one step. Export is supported (although it does not make a lot of   sense, as the purpose of the entity is the product creation). Update is not supported. Only a   limited set of fields are supported (those available in the product creation   form).       Does not support set based SQL   operations.    Not exposed through Odata.                                                                                                                        |   |   |
|    Product variants                                                |    EcoResProductVariantEntity                                   |    Import and export of shared product   variants. Allow updates. Requires that dimension values are already created.   The integration key is the product master + product dimensions.        Does not support set based SQL   operations.        Enabled for Odata. Support deletes.        This data entity is not extensible   with regards to adding new product dimensions.                                                                                                                                       |   |   |
|    Product variants by product number   identification             |    EcoResProductNumberIdentifiedProductVariantEntity            |    Import and export of shared product   variants. Allow updates. Requires that dimension values are already created.   The integration key is the product number (as a difference from the Product   variants entity where the integration key is the product master +   dimensions).                                                                                                                                                                                                                                  |   |   |
|    Released product variants                                       |    EcoResReleasedProductVariantEntity                           |    Import and   export of released product variants. Allow updates. Require that shared   product variant is already created.. When new released product variant is   imported, a release of the shared product variant is made behind the scenes.        Does not support set based SQL   operations.        Enabled for Odata. Support deletes   (but this causes data corruption due to platform bug).       This data entity is not extensible   wrt. Adding new product dimensions.                                |   |   |
|    Released product variants by product   number identification    |    EcoResProductNumberIdentifiedReleasedProductVariantEntity    |    Similar to the Released Product   Variants entity, but with product number as key instead of product master +   dimensions.        This data entity is extensible with   regards to adding new product dimensions.                                                                                                                                                                                                                                                                                                   |   |   |
|    Sellable released products                                      |    EcoResSellableReleasedProductEntity                          |    Use to export only the products that are sellable.   Sellable products are products that have the information that they require in   order to be used in a sales order. The same rules apply when a product is   validates using the Validate function on the Released products page.                                                                                                                                                                                                                                |   |   |
|    Released Distinct products V2                                   |    EcoResDistinctProductV2Entity                                |    It exports the distinct products: products subtype product   and the different product variants.                                                                                                                                                                                                                                                                                                                                                                                                                     |   |   |
|    Released products masters V2                                    |    EcoResProductMasterV2Entity                                  |    It imports and exports the product masters.    Not data management enabled.                                                                                                                                                                                                                                                                                                                                                                                                                                          |   |   |
|    Item - bar code                                                 |    EcoResProductBarcodeEntity                                   |    Use to export the product and its barcode                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |   |   |
|    Product lifecycle states                                        |    EcoResProductLifecycleSateEntity                             |    It exports and imports the different product lifecycle   states that can be assigned to a product.                                                                                                                                                                                                                                                                                                                                                                                                                   |   |   |

> [!NOTE]
> To import products into the system you must use the **Product creation** data entity. You can only use the Released Products V2 to import products if the shared product has already been created. 
