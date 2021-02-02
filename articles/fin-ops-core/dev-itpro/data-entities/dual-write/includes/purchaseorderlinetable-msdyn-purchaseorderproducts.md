---
author: robinarh
ms.service: dynamics-ax-applications
ms.topic: include
ms.date: 11/17/2020
ms.author: rhaertle
---

### purchase order line table to msdyn_purchaseorderproducts

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement field | Default value
---|---|---|---
REQUESTEDDELIVERYDATE |  | `msdyn_dateexpected` | 
LINEDESCRIPTION |  | `msdyn_description` | 
LINENUMBER |  | `msdyn_lineorder` | 
PRODUCTNUMBER |  | `msdyn_product.msdyn_productnumber` | 
PURCHASEORDERNUMBER |  | `msdyn_purchaseorder.msdyn_name` | 
ORDEREDPURCHASEQUANTITY |  | `msdyn_quantity` | 
LINEAMOUNT |  | `msdyn_lineamount` | 
PURCHASEPRICE |  | `msdyn_unitcost` | 
BARCODE |  | `msdyn_barcode` | 
CATCHWEIGHTUNITSYMBOL |  | `msdyn_catchweightunitsymbol.msdyn_symbol` | 
CONFIRMEDSHIPPINGDATE |  | `msdyn_confirmedshippingdate` | 
CUSTOMERREFERENCE |  | `msdyn_customerreference` | 
CUSTOMERREQUISITIONNUMBER |  | `msdyn_customerrequisitionnumber` | 
EXTERNALITEMNUMBER |  | `msdyn_externalitemnumber` | 
ISPARTIALDELIVERYPREVENTED |  | `msdyn_ispartialdeliveryprevented` | 
LINEDISCOUNTAMOUNT |  | `msdyn_linediscountamount` | 
LINEDISCOUNTPERCENTAGE |  | `msdyn_linediscountpercentage` | 
ORDEREDCATCHWEIGHTQUANTITY |  | `msdyn_orderedcatchweightquantity` | 
PURCHASEORDERLINESTATUS |  | `msdyn_purchaseorderlinestatus` | 
PURCHASEPRICEQUANTITY |  | `msdyn_purchasepricequantity` | 
RECEIVINGSITEID |  | `msdyn_receivingsiteid.msdyn_siteid` | 
REQUESTEDSHIPPINGDATE |  | `msdyn_requestedshippingdate` | 
REQUESTERPERSONNELNUMBER |  | `msdyn_requesterpersonnelnumber.cdm_workernumber` | 
PROCUREMENTPRODUCTCATEGORYNAME |  | `msdyn_procurementproductcategory.msdyn_name` | 
PROCUREMENTPRODUCTCATEGORYHIERACHYNAME |  | `msdyn_procurementproductcategory.msdyn_hierarchy.msdyn_name` | 
CURRENCYCODE |  | `transactioncurrencyid.isocurrencycode` | 
CONFIRMEDDELIVERYDATE |  | `msdyn_confirmeddeliverydate` | 
DELIVERYADDRESSCITY |  | `msdyn_deliveryaddresscity` | 
DELIVERYADDRESSCOUNTRYREGIONID |  | `msdyn_deliveryaddresscountryregionid` | 
DELIVERYADDRESSSTATEID |  | `msdyn_deliveryaddressstate` | 
DELIVERYADDRESSSTREET |  | `msdyn_deliveryaddressstreet` | 
DELIVERYADDRESSSTREETNUMBER |  | `msdyn_deliveryaddressstreetnumber` | 
DELIVERYADDRESSZIPCODE |  | `msdyn_deliveryaddresszipcode` | 
FORMATTEDDELVERYADDRESS |  | `msdyn_formatteddeliveryaddress` | 
PURCHASEUNITSYMBOL |  | `msdyn_unit.msdyn_symbol` | 
RECEIVINGWAREHOUSEID |  | `msdyn_associatetowarehouse.msdyn_warehouseidentifier` | 
DELIVERYADDRESSDESCRIPTION | > | `msdyn_deliveryaddressdescription` | 
DELIVERYADDRESSNAME | > | `msdyn_deliveryaddressname` | 
