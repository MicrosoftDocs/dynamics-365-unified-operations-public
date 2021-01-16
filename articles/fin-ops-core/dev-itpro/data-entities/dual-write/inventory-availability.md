---
# required metadata

title: Inventory availability in dual-write
description: This topic provides information about how to check inventory availability in dual-write.
author: yijialuan
manager: AnnBe
ms.date: 05/26/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: riluan
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-05-26

---

# Inventory availability in dual-write

[!include [banner](../../includes/banner.md)]

By using inventory availability, you can check your inventory before you add a product to the **Quotations**, **Orders**, or **Invoices** page in Microsoft Dynamics 365 Sales. For example, you check inventory and determine a fulfillment date as one key task in the [prospect-to-cash](dual-write-prospect-to-cash.md) process.

If you don't have enough inventory, you can estimate a delivery date, based on projected inventory receipts and issues. You can also check the product's available-to-promise (ATP) information, where you can find the ATP quantity in the predefined time fence.

## On-hand inventory

In Dynamics 365 Sales, a new **On-hand Inventory** button has been added to the header of the **Quotes**, **Orders**, and **Invoices** pages. When you select this button, a dialog box appears, where you can specify the company and the product that you want to check the on-hand inventory for. This dialog box shows the same information as [On-hand inventory](../../../../supply-chain/inventory/tasks/check-availability-stock.md).

The dialog box returns the inventory information from Dynamics 365 Supply Chain Management. This information includes the following quantities:

- On-hand quantity
- Reserved on-hand quantity
- Available on-hand quantity
- Ordered quantity
- On-order quantity
- Reserved ordered quantity
- Total available quantity

## ATP information

In Sales, a new **ATP Information** button has been added to line items on the **Quotes**, **Orders**, and **Invoices** pages. When you select this button, a dialog box appears, where you can specify the company, product, inventory site, inventory warehouse, and order quantity. This dialog box has the same settings that are described in [Order promising](../../../../supply-chain/sales-marketing/delivery-dates-available-promise-calculations.md#atp-calculations).

The dialog box returns the ATP information from Supply Chain Management. This information includes the following quantities:

- ATP quantity
- Receipt quantity
- Issue quantity
- On-hand quantity

## How it works

When you select the **On-hand Inventory** button on the **Quotes**, **Orders**, or **Invoices** page, a live dual-write call is made to the **Onhand inventory** API. The API calculates the on-hand inventory for the given product. The result is stored in the **InventCDSInventoryOnHandRequestEntity** and **InventCDSInventoryOnHandEntryEntity** tables, and then is written to Dataverse by dual-write. To use this functionality, you need to run the following dual-write maps. Skip initial synchronization when you run the maps.

- CDS inventory on-hand entries (msdyn_inventoryonhandentries)
- CDS inventory on-hand requests (msdyn_inventoryonhandrequests)

## Templates
The following templates are available for the exposing the onhand inventory data.

Finance and Operations apps | Customer engagement app | Description 
---|---|---
[CDS inventory on-hand entries](#145) | msdyn_inventoryonhandentries |
[CDS inventory on-hand requests](#147) | msdyn_inventoryonhandrequests |

[!include [banner](../../includes/dual-write-symbols.md)]

###  <a name="145"></a>CDS inventory on-hand entries (msdyn_inventoryonhandentries)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement field | Default value
---|---|---|---
`REQUESTID` | = | `msdyn_request.msdyn_requestid` |
`INVENTORYSITEID` | = | `msdyn_inventorysite.msdyn_siteid` |
`INVENTORYWAREHOUSEID` | = | `msdyn_inventorywarehouse.msdyn_warehouseidentifier` |
`AVAILABLEONHANDQUANTITY` | > | `msdyn_availableonhandquantity` |
`AVAILABLEORDEREDQUANTITY` | > | `msdyn_availableorderedquantity` |
`ONHANDQUANTITY` | > | `msdyn_onhandquantity` |
`ONORDERQUANTITY` | > | `msdyn_onorderquantity` |
`ORDEREDQUANTITY` | > | `msdyn_orderedquantity` |
`RESERVEDONHANDQUANTITY` | > | `msdyn_reservedonhandquantity` |
`RESERVEDORDEREDQUANTITY` | > | `msdyn_reservedorderedquantity` |
`TOTALAVAILABLEQUANTITY` | > | `msdyn_totalavailablequantity` |
`ATPDATE` | = | `msdyn_atpdate` |
`ATPQUANTITY` | > | `msdyn_atpquantity` |
`PROJECTEDISSUEQUANTITY` | > | `msdyn_projectedissuequantity` |
`PROJECTEDONHANDQUANTITY` | > | `msdyn_projectedonhandquantity` |
`PROJECTEDRECEIPTQUANTITY` | > | `msdyn_projectedreceiptquantity` |
`ORDERQUANTITY` | > | `msdyn_orderquantity` |
`UNAVAILABLEONHANDQUANTITY` | > | `msdyn_unavailableonhandquantity` |

###  <a name="147"></a>CDS inventory on-hand requests (msdyn_inventoryonhandrequests)

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement field | Default value
---|---|---|---
`REQUESTID` | = | `msdyn_requestid` |
`PRODUCTNUMBER` | < | `msdyn_product.msdyn_productnumber` |
`ISATPCALCULATION` | << | `msdyn_isatpcalculation` |
`ORDERQUANTITY` | < | `msdyn_orderquantity` |
`INVENTORYSITEID` | < | `msdyn_inventorysite.msdyn_siteid` |
`INVENTORYWAREHOUSEID` | < | `msdyn_inventorywarehouse.msdyn_warehouseidentifier` |
`REFERENCENUMBER` | < | `msdyn_referencenumber` |
`LINECREATIONSEQUENCENUMBER` | < | `msdyn_linecreationsequencenumber` |




