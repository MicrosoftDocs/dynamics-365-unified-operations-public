---
title: Customer details V2 entity
description: Definition of the Customer details V2 data entity in finance and operations migration projects with Dynamics 365.
ms.date: 04/28/2023
ms.topic: article
author: edupont04
ms.author: katiehav
searchScope: dynamics-365-daf
ms.service: dynamics-365
ms.subservice: guidance
ms.collection: FastTrack
---

# Customer details V2 entity

The **Customer details V2** entity supports updating the specialized fields for a customer. It doesn't support creating customers.

## When to use this entity

Use the **Customer details V2** entity to supplement the **Customer definitions** entity. The **Customer details V2** entity is most often used to update the INVOICEACCOUNT and DEFAULTDIMENSIONDISPLAYVALUE fields. You can update any of the fields it supports independently of the fields being updated with the **Customer definitions** entity, especially if the fields from either entity are updated with different patterns.

## Summary

|Type|Name|
|----|----|
| **Data management entity name** | Customer details V2 |
| **OData public entity** | N/A |
| **OData public collection** | N/A |
| **Related menu items** | Accounts receivable / Customers / All customers |
| **Related entities** | Customers V3, Customer definitions |
| **Performance pattern** | Multiple threads supported – Recommendation is to set **Import threshold record count** to 1000 and set **Import task count** to 8. For more information, see [Parallel imports](/dynamics365/fin-ops-core/dev-itpro/data-entities/data-import-export-job#parallel-imports). |
| **Application Object Tree (AOT) name** | CustCustomerDetailV2Entity |

## Fields

| Field | Description |
|--|--|
| CUSTOMERACCOUNT | Specifies the primary key. it's a foreign key to the **Customer definitions** entity. |
| DEFAULTDIMENSIONDISPLAYVALUE | Updating this field requires configuring the **Default dimension format** using the **Financial dimension configuration for integrating applications** menu item**.** |
| INVOICEACCOUNT | Specifies a foreign key that is a self-relation to another customer. The customer referenced by **INVOICEACCOUNT** has to exist before this field can be updated. |

## Issues and considerations

You can use the **Customer details V2** entity to update the DEFAULTDIMENSIONDISPLAYVALUE field because it isn't supported by [cross-company data sharing](/dynamics365/fin-ops-core/dev-itpro/sysadmin/srs-overview).

The **Customer details V2** entity doesn't support creating customers. It's a common pattern to use it to update the INVOICEACCOUNT or DEFAULTDIMENSIONDISPLAYVALUE fields after the customer has been created using the **Customer definitions** entity.

## Example

Use the **Customer details V2** entity to update the DEFAULTDIMENSIONDISPLAYVALUE field after the customers are created using the **Customer definitions** entity, or when customers are being duplicated across the legal entities using cross-company data sharing. In these cases, the primary key and the fields being updated are the only fields that need to be included.

## Related resources

[Import customers in Dynamics 365 projects](/dynamics365/guidance/resources/import-customers)  
