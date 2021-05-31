---
# required metadata
title: Processing of inbound ASNs through Inbound ASN V2 data entity
description: This topic explains how to manage import of the inbound ASNs.
author: v-gfedorova
ms.date: 05/31/2021
ms.topic: article
ms.prod: 
ms.technology: 
# optional metadata
ms.search.form: WHSInboundASNV2Entity, WHSInboundASNEntity
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
# ms.search.industry: 
ms.author: kamaybac
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.19
---
# Processing of inbound ASNs through Inbound ASN V2 data entity
[!include [banner](../../includes/banner.md)]

The *ASN* stands for the *Advanced Shipping Notice* and enables notifying companies about their deliveries from the vendor. With the help of the ASN, the sender is able to describe the content of the shipment as well as the additional information of the shipment including but not limited to the items, packaging and so on. 

This feature can help warehouse workers know when and what is arriving allowing to prepare for it in advance. In addition it allows warehouse workers match the details of the shipments against the specific purchase order created beforehand. 

This topic presents a collection of scenarios that show, through examples, how to work with the ASN files. 
 
> [!IMPORTANT]
> The *Inbound ASN* import applies only to the items that are activated to the Advanced Warehouse Management. Purchase order must be registered in the system against the vendor who is sending the ASN before receiving the ASN. 

## Overview
Import of the inbound ASN in Dynamics 365 Supply Chain management is introduced as *Inbound ASN V2* composite data entity. The *Inbound ASN V2* is leveraging multiple entities:
- Inbound load header
- Inbound shipment header
- Inbound load packing structures
- Inbound load packing structure case lines
- Inbound load packing structure cases
- Inbound load packing structure lines

*Inbound ASN V2* composite data entity is supposed to work in asynchronous integration scenarios with the help of XML file based imports.  

## ASN file, XML format to import

Dynamics 365 Supply Chain management supports the following ASN format, where each node in the XML file represents the attributes from an individual entity:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Document>
  <WHSInboundLoadHeaderEntity>
      <WHSInboundShipmentHeaderEntity>
          <WHSInboundLoadPackingStructureEntity>
	              <WHSInboundLoadPackingStructureCaseEntity>
	                     <WHSInboundPackingStructureCaseLineV2Entity>
	                      </WHSInboundPackingStructureCaseLineV2Entity>
	                </WHSInboundLoadPackingStructureCaseEntity>
		   <WHSInboundLoadPackingStructureLineV2Entity>
		   </WHSInboundLoadPackingStructureLineV2Entity>
          </WHSInboundLoadPackingStructureEntity>
      </WHSInboundShipmentHeaderEntity>
  </WHSInboundLoadHeaderEntity>
</Document>
```
 
## Sample 1 of the ASN xml file to import through Inbound ASN V2 data entity 

Sample file for importing vendor shipments for one purchase order without case details 

```xml
<?xml version="1.0" encoding="utf-8"?>
<Document>
	<WHSInboundLoadHeaderEntity TRACTORNUMBER="0000101">
		<WHSInboundShipmentHeaderEntity VENDORSHIPMENTID="VendASN_01" VENDORADDRESSCOUNTRYREGIONID = "USA" VENDORADDRESSSTREET = "123 Coffee Street" VENDORADDRESSSTATEID = "WA" VENDORADDRESSCITY = "Redmond" VENDORADDRESSZIPCODE = "98052">
			<WHSInboundLoadPackingStructureEntity LICENSEPLATENUMBER="LP_ASN_001">
				<WHSInboundLoadPackingStructureLineV2Entity PURCHASEORDERNUMBER="00000176" ITEMNUMBER="A0001" QUANTITY="1" UNITSYMBOL="ea" />
			</WHSInboundLoadPackingStructureEntity>
		</WHSInboundShipmentHeaderEntity>
	</WHSInboundLoadHeaderEntity>
</Document>
```

## Sample 2 of the ASN xml file to import through Inbound ASN V2 data entity

Sample file for importing vendor shipments for one purchase order with case details 


```xml
<?xml version="1.0" encoding="utf-8"?>
<Document>
	<WHSInboundLoadHeaderEntity ESTIMATEDARRIVALDATETIME="2021-04-25T11:00:00+00:00">
		<WHSInboundShipmentHeaderEntity VENDORSHIPMENTID="MVR_SNN_0004">
			<WHSInboundLoadPackingStructureEntity LICENSEPLATENUMBER="MVR_SNN_0004" PACKEDTOTALQUANTITY="2.00">
				<WHSInboundLoadPackingStructureCaseEntity PARENTPACKINGSTRUCTURELICENSEPLATENUMBER="MVR_SNN_0004" LICENSEPLATENUMBER="MVR_SNN_0004A" PACKEDTOTALQUANTITY="2.00" />
				<WHSInboundLoadPackingStructureLineV2Entity PURCHASEORDERNUMBER="00000175" ITEMNUMBER="A0001" PURCHASEORDERLINENUMBER="1" QUANTITY="2.00" UNITSYMBOL="ea" />
			</WHSInboundLoadPackingStructureEntity>
		</WHSInboundShipmentHeaderEntity>
	</WHSInboundLoadHeaderEntity>
</Document>
```


## Sample 3 of the ASN xml file to import through Inbound ASN V2 data entity

Sample file for importing vendor shipments for several purchase orders with case details 


```xml
<?xml version="1.0" encoding="utf-8"?>
<Document>
	<WHSInboundLoadHeaderEntity TRACTORNUMBER="0000101">
		<WHSInboundShipmentHeaderEntity VENDORSHIPMENTID="VendASN_01" VENDORADDRESSCOUNTRYREGIONID = "USA" VendorAddressStreet = "123 Coffee Street" VENDORADDRESSSTATEID = "WA" VENDORADDRESSCITY = "Redmond" VENDORADDRESSZIPCODE = "98052">
			<WHSInboundLoadPackingStructureEntity LICENSEPLATENUMBER="LP_ASN_001">
				<WHSInboundLoadPackingStructureLineV2Entity PURCHASEORDERNUMBER="00000176" ITEMNUMBER="A0001" QUANTITY="100" UNITSYMBOL="ea" />
			</WHSInboundLoadPackingStructureEntity>
		</WHSInboundShipmentHeaderEntity>
		<WHSInboundShipmentHeaderEntity VENDORSHIPMENTID="VendASN_02" VENDORADDRESSCOUNTRYREGIONID = "USA" VendorAddressStreet = "123 Coffee Street" VENDORADDRESSSTATEID = "WA" VENDORADDRESSCITY = "Redmond" VENDORADDRESSZIPCODE = "98052">
			<WHSInboundLoadPackingStructureEntity LICENSEPLATENUMBER="LP_ASN_001">
				<WHSInboundLoadPackingStructureLineV2Entity PURCHASEORDERNUMBER="00000177" ITEMNUMBER="A0001" QUANTITY="200" UNITSYMBOL="ea" />
				<WHSInboundLoadPackingStructureLineV2Entity PURCHASEORDERNUMBER="00000177" ITEMNUMBER="P0004" QUANTITY="300" UNITSYMBOL="ea" ITEMBATCHNUMBER="BN0001" />
			</WHSInboundLoadPackingStructureEntity>
			<WHSInboundLoadPackingStructureEntity LICENSEPLATENUMBER="LP_ASN_002">
				<WHSInboundLoadPackingStructureCaseEntity LICENSEPLATENUMBER="LP_ASN_002_C01">
					<WHSInboundLoadPackingStructureCaseLineV2Entity PURCHASEORDERNUMBER="00000177" ITEMNUMBER="A0001" QUANTITY="400" UNITSYMBOL="ea" />
				</WHSInboundLoadPackingStructureCaseEntity>
			</WHSInboundLoadPackingStructureEntity>
		</WHSInboundShipmentHeaderEntity>
	</WHSInboundLoadHeaderEntity>
</Document>
```

## Result of importing ASN
Follow these steps to create and manage user settings for your mobile devices.
1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that has been created as part of the import. Make a note of all values that were presented in the XML file.
1. On the **Load lines** FastTab, make a note of the purchase order numbers and item details based on the XML file.
1. On the Action Pane, on the **Ship and receive** tab, in the **Receive** group, select **Packing structure**.
1. On the **Pallets** FastTab, make a note of the license plates based on the XML file.
1. On the **Cases** FastTab, make a note of the cases based on the XML file.
1. On the **Items** FastTab, make a note of the items and their quantities based on the XML file.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

