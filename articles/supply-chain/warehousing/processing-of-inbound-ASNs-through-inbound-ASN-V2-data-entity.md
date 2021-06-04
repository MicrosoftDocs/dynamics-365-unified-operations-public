---
title: Import inbound ASNs through the V2 data entity
description: This topic explains how to manage import of the inbound advanced shipping notices (ASNs) through the Inbound ASN V2 data entity.
author: GalynaFedorova
ms.date: 05/31/2021
ms.topic: article
ms.search.form: WHSInboundASNV2Entity, WHSInboundASNEntity
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: v-gfedorova
ms.search.validFrom: 2021-06-04
ms.dyn365.ops.version: 10.0.19
---

# Import inbound ASNs through the V2 data entity

[!include [banner](../../includes/banner.md)]

Advanced shipping notices (ASNs) notify you about vendor deliveries. With the help of the ASN, the sender is able to describe the content of the shipment as well as the additional information of the shipment including, but not limited to, the items, packaging and so on.

This feature can help warehouse workers know what is arriving when, which lets them prepare in advance. In addition, ASNs allow warehouse workers match the details of a shipments against the related purchase order created beforehand.

This topic presents a collection of scenarios that show, through examples, how to work with ASN files.

> [!IMPORTANT]
> The *Inbound ASN* import applies only to the items that are enabled for advanced warehouse management (WMS). A purchase order must be registered in the system against the vendor who is sending the ASN before you receive the ASN.

## Overview

You import inbound ASNs using the *Inbound ASN V2* composite data entity. *Inbound ASN V2* leverages the following entities:

- Inbound load header
- Inbound shipment header
- Inbound load packing structures
- Inbound load packing structure case lines
- Inbound load packing structure cases
- Inbound load packing structure lines

The *Inbound ASN V2* composite data entity is intended to work in asynchronous integration scenarios with the help of XML-file based imports.  

## The XML format for importing ASNs

Supply Chain management supports the following XML format for importing ASNs, where each node in the XML file represents an attribute from an individual entity:

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

## ASN XML import file example 1

The following example shows an XML file for importing vendor shipments for one purchase order without case details.

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

## ASN XML import file example 2

The following example shows an XML file for importing vendor shipments for one purchase order with case details.

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

## ASN XML import file example 3

The following example shows an XML file for importing vendor shipments for several purchase orders with case details.

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

## Inspect the result of importing ASN

Follow these steps to create and manage user settings for your mobile devices: <!-- KFM: Is this really the correct intro for this procedure? I suspect it should be something like "Follow these steps to inspect the results of importing an ASN file:" -->

<!-- KFM: I was a little unsure about what the user should do and notice in the following procedure. Please confirm my version. -->

1. Go to **Warehouse management \> Loads \> All loads**.
1. Find and open a load that was created as part of an ASN import.
1. On the **Load** FastTab, you should see values based on the XML file.
1. On the **Load lines** FastTab, you should see the purchase order numbers and item details based on the XML file.
1. On the Action Pane, open the **Ship and receive** tab and, in the **Receive** group, select **Packing structure**.
1. On the **Pallets** FastTab, you should see license plates based on the XML file.
1. On the **Cases** FastTab, you should see cases based on the XML file.
1. On the **Items** FastTab, you should see items and quantities based on the XML file.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
