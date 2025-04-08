---
title: Dual-write mapping reference
description: Learn about the column mappings for each dual-write mapping, including a table that defines the map type and customer engagement column for finance and operations fields.
author: josaw
ms.author: josaw
ms.topic: reference
ms.date: 10/06/2022
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2020-12-22
---

# Dual-write mapping reference

[!include [banner](../../includes/banner.md)]

[!include [banner](includes/dual-write-symbols.md)]

## Templates

[!include[source-destination](includes/source-destination.md)]

[!include[mapping-list](includes/mapping-tables.md)]

## Transfer order headers

|**Finance and operations field** | **Map type** | **Customer engagement column** | **Default value** |
|------------------------------------|-------------|----------------------------------|-----------------|
|SHIPPINGADDRESSNAME | > | msdyn_shippingaddressname |
|FORMATTEDSHIPPINGADDRESS | > | msdyn_formattedshippingaddress |
|SHIPPINGADDRESSCITY | > | msdyn_shippingaddresscity |
|SHIPPINGADDRESSCOUNTRYREGIONID | > | msdyn_shippingaddresscountryregionid |
|SHIPPINGADDRESSCOUNTYID | > | msdyn_shippingaddresscountyid |
|SHIPPINGADDRESSDESCRIPTION | > | msdyn_shippingaddressdescription |
|SHIPPINGADDRESSDISTRICTNAME | > | msdyn_shippingaddressdistrictname |
|SHIPPINGADDRESSDUNSNUMBER | > | msdyn_shippingaddressdunsnumber |
|SHIPPINGADDRESSLATITUDE | > | msdyn_shippingaddresslatitude |
|SHIPPINGADDRESSLOCATIONID | > | msdyn_shippingaddresslocationid |
|SHIPPINGADDRESSLONGITUDE | > | msdyn_shippingaddresslongitude |
|SHIPPINGADDRESSPOSTBOX | > |  msdyn_shippingaddresspostbox |
|SHIPPINGADDRESSSTATEID | > | msdyn_shippingaddressstateorprovince |
|SHIPPINGADDRESSSTREET | > | msdyn_shippingaddress1 |
|SHIPPINGADDRESSSTREETNUMBER | > | msdyn_shippingaddress2 |
|SHIPPINGADDRESSTIMEZONE | > | msdyn_shippingaddresstimezone |
|SHIPPINGADDRESSZIPCODE | > | msdyn_shippingaddresspostalcode |
|SHIPPINGCONTACTPERSONNELNUMBER | > | msdyn_shippingcontactpersonnelnumber |
|DELIVERYMODECODE | = | msdyn_shipvia |
|DELIVERYTERMSCODE | = | msdyn_deliveryterm |
|SHIPPINGWAREHOUSEID | = | msdyn_fromwarehouse.msdyn_warehouseidentifier |
|RECEIVINGWAREHOUSEID | = | msdyn_towarehouse.msdyn_warehouseidentifier |
|TRANSITWAREHOUSEID | > | msdyn_transitwarehouse.msdyn_warehouseidentifier |
|REQUESTEDRECEIPTDATE | = | msdyn_receivedate |
|REQUESTEDSHIPPINGDATE | = | msdyn_shipdate |
|RECEIVINGADDRESSNAME | > | msdyn_receivingaddressname |
|TRANSFERORDERNUMBER | = | msdyn_name |
|TRANSFERORDERSTATUS | >> | msdyn_transferstatus |
|RECEIVINGCONTACTPERSONNELNUMBER | > | msdyn_receivingcontactpersonnelnumber |
|FORMATTEDRECEIVINGADDRESS | > | msdyn_formattedreceivingaddress |
|RECEIVINGADDRESSCITY | > | msdyn_receivingaddresscity |
|RECEIVINGADDRESSCOUNTRYREGIONID | > | msdyn_receivingaddresscountryregionid |
|RECEIVINGADDRESSCOUNTYID | > | msdyn_receivingaddresscountyid |
|RECEIVINGADDRESSDESCRIPTION | > | msdyn_receivingaddressdescription |
|RECEIVINGADDRESSDISTRICTNAME | > | msdyn_receivingaddressdistrictname |
|RECEIVINGADDRESSDUNSNUMBER | > | msdyn_receivingaddressdunsnumber |
|RECEIVINGADDRESSLATITUDE | > | msdyn_receivingaddresslatitude |
|RECEIVINGADDRESSLOCATIONID | > | msdyn_receivingaddresslocationid |
|RECEIVINGADDRESSLONGITUDE | > | msdyn_receivingaddresslongitude |
|RECEIVINGADDRESSPOSTBOX | > | msdyn_receivingaddresspostbox |
|RECEIVINGADDRESSSTATEID | > | msdyn_receivingaddressstateorprovince |
|RECEIVINGADDRESSSTREET | > | msdyn_receivingaddresss1 |
|RECEIVINGADDRESSSTREETNUMBER | > | msdyn_receivingaddresss2 |
|RECEIVINGADDRESSTIMEZONE | > | msdyn_receivingaddresstimezone |
|RECEIVINGADDRESSZIPCODE | > | msdyn_receivingaddresspostalcode |

## Transfer order products

|**Finance and operations field** | **Map type** | **Customer engagement column** | **Default value** |
|------------------------------------|-------------|----------------------------------|-----------------|
| ITEMNUMBER | = | msdyn_product.msdyn_productnumber |
| LINENUMBER | = | msdyn_lineorder | 
| ALLOWEDOVERDELIVERYPERCENTAGE | = | msdyn_allowedoverdeliverypercentage |
| RECEIVEDCATCHWEIGHTQUANTITY | > | msdyn_catchweightquantityreceived |
| SCRAPPEDCATCHWEIGHTQUANTITY | > | msdyn_catchweightquantityscrapped |
| SHIPPEDCATCHWEIGHTQUANTITY | > | msdyn_catchweightquantityshipped |
| TRANSFERCATCHWEIGHTQUANTITY | = | msdyn_catchweightquantity |
| RECEIVEDQUANTITY | > | msdyn_quantityreceived |
| SCRAPPEDQUANTITY | > | msdyn_quantityscrapped |
| SHIPPEDQUANTITY | > | msdyn_quantityshipped |
| TRANSFERQUANTITY | > | msdyn_quantity |
| REQUESTEDRECEIPTDATE | = | msdyn_receivedate |
| LINESTATUS | >> | msdyn_linestatus |
| REQUESTEDSHIPPINGDATE | = | msdyn_shipdate | 
| TRANSFERORDERNUMBER | = | msdyn_transferorder.msdyn_name | 
| ALLOWEDUNDERDELIVERYPERCENTAGE | = | msdyn_allowedunderdeliverypercentage |
| INVENTORYUNITSYMBOL | > | msdyn_unit |
| SHIPPINGWAREHOUSEID | = | msdyn_shippingwarehouse |
| SHIPPINGSITEID | = | msdyn_shippingsite |
| SHIPPINGWAREHOUSELOCATIONID | = | msdyn_shippinglocation |
