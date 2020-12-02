---
author: robinarh
ms.service: dynamics-ax-applications
ms.topic: include
ms.date: 11/17/2020
ms.author: rhaertle
---

## Product receipt line to msdyn_purchaseorderreceiptproducts

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement field | Default value
---|---|---|---
RECORDID | >> | `msdyn_recordid` | 
DELIVERYADDRESSCOUNTRYREGIONID | >> | `msdyn_deliveryaddresscountryregionid` | 
DELIVERYADDRESSCOUNTYID | >> | `msdyn_deliveryaddresscountyid` | 
DELIVERYADDRESSSTATEID | >> | `msdyn_deliveryaddressstateid` | 
EXPECTEDDELIVERYDATE | >> | `msdyn_expecteddeliverydate` | 
EXTERNALITEMNUMBER | >> | `msdyn_externalitemnumber` | 
ITEMBATCHNUMBER | >> | `msdyn_itembatchnumber` | 
ITEMSERIALNUMBER | >> | `msdyn_itemserialnumber` | 
LINEDESCRIPTION | >> | `msdyn_linedescription` | 
ORDEREDPURCHASEQUANTITY | >> | `msdyn_orderedpurchasequantity` | 
PROCUREMENTPRODUCTCATEGORYNAME | >> | `msdyn_procurementproductcategory.msdyn_name` | 
PROCUREMENTPRODUCTCATEGORYHIERARCHYNAME | >> | `msdyn_procurementproductcategory.msdyn_hierarchy.msdyn_name` | 
PRODUCTRECEIPTDATE | >> | `msdyn_productreceiptdate` | 
PRODUCTRECEIPTHEADERRECORDID | >> | `msdyn_purchaseorderreceipt.msdyn_recordid` | 
PRODUCTRECEIPTNUMBER | >> | `msdyn_productreceiptnumber` | 
PURCHASEORDERLINENUMBER | >> | `msdyn_purchaseorderproduct.msdyn_lineorder` | 
PURCHASEORDERNUMBER | >> | `msdyn_purchaseorderproduct.msdyn_purchaseorder.msdyn_name` | 
PURCHASEORDERNUMBER | >> | `msdyn_purchaseorder.msdyn_name` | 
PURCHASEUNITSYMBOL | >> | `msdyn_purchaseunitsymbol.msdyn_symbol` | 
RECEIVEDINVENTORYQUANTITY | >> | `msdyn_receivedinventoryquantity` | 
RECEIVEDINVENTORYSTATUSID | >> | `msdyn_receivedinventorystatusid` | 
RECEIVEDPURCHASEQUANTITY | >> | `msdyn_quantity` | 
RECEIVINGSITEID | >> | `msdyn_receivingsiteid.msdyn_siteid` | 
RECEIVINGWAREHOUSEID | >> | `msdyn_associatetowarehouse.msdyn_warehouseidentifier` | 
RECEIVINGWAREHOUSELOCATIONID | >> | `msdyn_receivingwarehouselocation.msdyn_warehouselocationid` | 
RECEIVINGWAREHOUSEID | >> | `msdyn_receivingwarehouselocation.msdyn_warehouse.msdyn_warehouseidentifier` | 
REMAININGINVENTORYQUANTITY | >> | `msdyn_remaininginventoryquantity` | 
REMAININGPURCHASEQUANTITY | >> | `msdyn_remainingpurchasequantity` | 
PRODUCTNUMBER | >> | `msdyn_product.msdyn_productnumber` | 
