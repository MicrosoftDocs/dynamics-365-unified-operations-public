---
title: Sales order lines V2 entity
description: Definition of the Sales order lines V2 data entity in finance and operations migration projects with Dynamics 365.
ms.date: 04/28/2023
ms.topic: article
author: edupont04
ms.author: katiehav
searchScope: dynamics-365-daf
ms.service: dynamics-365
ms.subservice: guidance
ms.collection: FastTrack
---

# Sales order lines V2

The **Sales order lines V2** entity supports importing and updating sales order lines.

## When to use this entity

Use the **Sales order lines V2** entity after the sales order header has already been created.

## Summary

|Type|Name|
|----|----|
| **Data management entity name** | **Sales order lines V2** |
| **OData public entity** | SalesOrderLine |
| **OData public collection** | SalesOrderLines |
| **Related menu items** | Accounts receivable/ Orders/ All sales orders</br>Sales and marketing/ Sales orders/ All sales orders |
| **Related entities** | Sales order headers V2 |
| **Performance pattern** | Single thread recommended |
| **Application Object Tree (AOT) name** | SalesOrderLineV2Entity |

## Fields

| Field | Description |
|--|--|
| INVENTORYLOTID | Specifies a unique identifier assigned to a specific lot of inventory items. The INVENTORYLOTID field requires that the inventory number sequence is previously configured. Otherwise, you can change the entity mapping and select Auto-generated. This field is the primary key. |
| DELIVERYADDRESSLOCATIONID | Specifies the delivery address location. This field requires that customers' delivery addresses are configured. This field is required. |
| ITEMNUMBER | Specifies a foreign key to a **Product**. This field is required. |
| LINEAMOUNT | Specifies the line amount. |
| ORDEREDSALESQUANTITY | Specifies the quantity of the sales item for this line. |
| REQUESTEDSHIPPINGDATE | Specifies the requested shipping date. This field is required. |
| SALESORDERNUMBER | Specifies a foreign key to a **Sales order header**. This field is required. |
| SALESPRICE | Specifies the sales price. |
| SALESUNITSYMBOL | Specifies a foreign key to a **Unit**. |

### Issues and considerations

The **Sales order lines V2** entity requires that sales order headers are created beforehand. All sales lines are related to a sales order header. The INVENTORYLOTID number sequence needs to already be configured and if set to manual can include specific values while importing, otherwise this field can be auto generated.

## Related resources

[Import sales orders in Dynamics 365 projects](/dynamics365/guidance/resources/import-sales-orders)  
