---
title: Released products V2 entity
description: Definition of theReleased products V2 data entity in finance and operations migration projects with Dynamics 365.
ms.date: 04/28/2023
ms.topic: article
author: edupont04
ms.author: katiehav
searchScope: dynamics-365-daf
ms.service: dynamics-365
ms.subservice: guidance
ms.collection: FastTrack
---

# Released products V2 entity

The **Released products V2** entity imports and updates released distinct products and product masters. It requires that the shared product has already been created.

## When to use this entity

Use the **Released products V2** entity to create and update released distinct products and product masters in a specific legal entity. The shared products must already exist.

When importing released product variants, use the **Released product variants** entity instead. This entity requires that shared product variants already exist.

## Summary

|Type|Name|
|----|----|
| **Data management entity name** | Released products V2 |
| **OData public entity** | ReleasedProductV2 |
| **OData public collection** | ReleasedProductsV2 |
| **Related menu items** | Product information management/ Products/ Released products |
| **Related entities** | Release products V2, Released product creation V2 |
| **Performance pattern** | Multiple threads supported – Recommendation is to set **Import threshold record count** to 1000 and set **Import task count** to 8. For more information, see [Parallel imports](/dynamics365/fin-ops-core/dev-itpro/data-entities/data-import-export-job#parallel-imports). |
| **Application Object Tree (AOT) name** | EcoResReleasedProductV2Entity |

### Fields

| Field | Description |
|--|--|
| ItemNumber | Specifies the primary key. This field is required. |
| COSTCALCULATIONGROUPID | Cost calculation group. Using this field requires creating calculation groups in **Cost management/Predetermined cost policies setup/Calculation groups**. |
| INVENTORYUNITSYMBOL | Inventory unit. Using this field requires configuration for units in **Organization administration/Setup/Units**. |
| ITEMGROUP | Item group. Using this field requires configuration for item groups in **Cost management/Inventory accounting policies setup/Item groups**. |
| ITEMMODELGROUPID | Item model group. Using this field requires configuration for item model groups in **Inventory management/Setup/Inventory/Item model groups.** |
| PRIMARYVENDORACCOUNTNUMBER | Primary vendor account number. Using this field requires vendor accounts created **Accounts payable/Vendors/All vendors**. |
| PRODUCTNUMBER | Shared product-distinct or product master number. This is a foreign key that relates to **Products V2** entity. This field is required. |
| PRODUCTSUBTYPE | Product sub type. The allowed values are **Product** and **ProductMaster**, default value is **Product**. |
| PURCHASEPRICE | Purchase price. |
| PURCHASEPRICEQUANTITY | Purchase price quantity. |
| PURCHUNITSYMBOL | Purchase unit. Using this field requires configuration for units in **Organization administration/Setup/Units**. |
| SALESPRICE | Sales price. |
| SALESPRICEQUANTITY | Sales price quantity. |
| SALESUNITSYMBOL | Sales unit. Using this field requires configuration for units in **Organization administration/Setup/Units**. |
| SEARCHNAME | Name Alias for searching. |
| UNITCOST | Cost. |

### Issues and considerations

The **Released products V2** entity supports creating and updating released distinct products and product masters. There are separate entities to import released distinct variants.

When importing shared products and released products in one step, use the **Released product creation V2** entity.

## Related resources

[Import products](/dynamics365/guidance/resources/import-products)  
