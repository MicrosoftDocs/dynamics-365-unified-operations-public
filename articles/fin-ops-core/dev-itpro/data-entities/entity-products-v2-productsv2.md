---
title: Products V2 entity
description: Definition of the Products V2 data entity in finance and operations migration projects with Dynamics 365.
ms.date: 04/28/2023
ms.topic: article
author: edupont04
ms.author: katiehav
searchScope: dynamics-365-daf
ms.service: dynamics-365
ms.subservice: guidance
ms.collection: FastTrack
---

# Products V2 entity

The **Products V2** entity imports and updates shared distinct products and product masters.  

## When to use this entity

Use the **Products V2** entity when creating or updating shared distinct products and product masters without them being released to a specific legal entity.  

When importing shared product variants, use the **Product Variants** entity instead. The product master should already exist.  

## Summary

|Type|Name|
|----|----|
| **Data management entity name** | Products V2 |
| **OData public entity** | ProductV2 |
| **OData public collection** | ProductsV2 |
| **Related menu items** | Product information management/ Products/ All products and product masters</br>Product information management/ Products/ Products</br>Product information management/ Products/ Product masters |
| **Related entities** | Release products V2, Released product creation V2 |
| **Performance pattern** | Multiple threads supported – Recommendation is to set **Import threshold record count** to 1000 and set **Import task count** to 8. For more information, see [Parallel imports](/dynamics365/fin-ops-core/dev-itpro/data-entities/data-import-export-job#parallel-imports). |
| **Application Object Tree (AOT) name** | EcoResProductV2Entity |

## Fields

| Field | Description |
|--|--|
| ProductNumber | Specifies the primary key. This field is required. |
| ProductType | The allowed values are **Item** and **Service**, default value is **Item**. This field is required. |
| ProductSearchName | The product name to be used for searching. This name can't exceed 20 characters. |
| ProductName | Product name in a specific language, based on the current user language. |
| ProductDescription | Product description in a specific language, the language is determined by the current user language. |
| ProductSubType | Product sub type. The allowed values are **Product** and **ProductMaster**, default value is **Product**. This field is required. |
| StorageDimensionGroupName | Name of the storage dimension group. Using this field requires creating storage dimension groups in **Dimension and variant groups**. |
| TrackingDimensionGroupName | Name of the tracking dimension group. Using this field requires creating tracking dimension groups in **Dimension and variant groups**. |

### Issues and considerations

The **Products V2** entity supports creating and updating shared distinct products and product masters.

- To create product variants, use the **Product variants** entity  

  Variants can only be created if the product master already exists as they're child records of the product master.

- To import released products, use the **Released products V2** entity  

  This entity requires that the shared product is already created.

## Related resources

[Import products](/dynamics365/guidance/resources/import-products)  
