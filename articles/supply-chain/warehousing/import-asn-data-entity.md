---
title: Import inbound ASNs through the V3 and V5 data entity
description: This article explains how to manage the import of inbound advanced shipping notices (ASNs) through the Inbound ASN data entity.
author: GalynaFedorova
ms.date: 05/11/2022
ms.topic: article
ms.search.form: WHSInboundASNV3Entity, WHSInboundASNEntity, DMFEntity, WHSInboundShipmentOrder
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: gfedorova
ms.search.validFrom: 2021-06-04
ms.dyn365.ops.version: 10.0.19
---

# Import inbound ASNs through data entities

[!include [banner](../../includes/banner.md)]

Advanced shipping notices (ASNs) notify you about vendor deliveries. They help the sender describe the contents of a shipment and additional information about it, such as the items and packaging.

ASNs can help warehouse workers learn what is arriving when. Therefore, they can prepare. In addition, warehouse workers can use ASNs to match the details of a shipment to the related purchase order and/or [inbound shipment order](warehouse-management-only-mode.md#inbound-shipment-orders) that was previously created.

This article presents a collection of scenarios that show, through examples, how to work with ASN files.

> [!IMPORTANT]
> _Inbound ASN_ import applies only to items that are enabled for warehouse management processes (WMS). Before you receive an ASN, a purchase or inbound shipment order must be registered in the system.

## Inbound ASN

You import inbound ASNs by using the _Inbound ASN V3_ and/or _Inbound ASN V5_ composite data entities which takes advantage of the following child entities:

- Inbound load header
- Inbound shipment header
- Inbound load packing structures
- Inbound load packing structure cases
- Inbound load packing structure case lines
- Inbound load packing structure lines

The _Inbound ASN_ composite data entities are intended for asynchronous integration scenarios where for example XML file–based files imports can be used.
> [!NOTE]
> Only the _Inbound ASN V5_ data entity supports [inbound shipment orders](warehouse-management-only-mode.md#inbound-shipment-orders). In this version the type of order must be specified as part of the ASN data which can either be **InboundShipmentOrder** for inbound shipment orders, or **Purch** for purchase orders.

> [!WARNING]
> Please do not use the _Inbound ASN V5_ data entities - but use the **_Inbound ASN V5_**

## XML format for importing V3 ASNs

Microsoft Dynamics 365 Supply Chain Management supports the following XML format for importing ASNs. Each node in the XML file represents an attribute from an individual entity.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Document>
    <WHSInboundLoadHeaderEntity>
        <WHSInboundShipmentHeaderEntity>
            <WHSInboundLoadPackingStructureEntity>
                <WHSInboundLoadPackingStructureCaseEntity>
                    <WHSInboundPackingStructureCaseLineV3Entity>
                    </WHSInboundPackingStructureCaseLineV3Entity>
                </WHSInboundLoadPackingStructureCaseEntity>
                <WHSInboundLoadPackingStructureLineV3Entity>
                </WHSInboundLoadPackingStructureLineV3Entity>
            </WHSInboundLoadPackingStructureEntity>
        </WHSInboundShipmentHeaderEntity>
    </WHSInboundLoadHeaderEntity>
</Document>
```

## Inbound ASN V3 entity (Only for purchase orders) examples

The following subsections provide examples of ASN XML import files for purchase order vendor shipments for _Inbound ASN V3_.

### Example 1

The following example shows an XML file for importing vendor shipments for one purchase order when no case details are included.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Document>
    <WHSInboundLoadHeaderEntity TRACTORNUMBER="0000101">
        <WHSInboundShipmentHeaderEntity VENDORSHIPMENTID="VendASN_01" VENDORADDRESSCOUNTRYREGIONID = "USA" VENDORADDRESSSTREET = "123 Coffee Street" VENDORADDRESSSTATEID = "WA" VENDORADDRESSCITY = "Redmond" VENDORADDRESSZIPCODE = "98052">
            <WHSInboundLoadPackingStructureEntity LICENSEPLATENUMBER="LP_ASN_001">
                <WHSInboundLoadPackingStructureLineV3Entity PURCHASEORDERNUMBER="00000176" ITEMNUMBER="A0001" QUANTITY="1" UNITSYMBOL="pcs" />
            </WHSInboundLoadPackingStructureEntity>
        </WHSInboundShipmentHeaderEntity>
    </WHSInboundLoadHeaderEntity>
</Document>
```

### Example 2

The following example shows an XML file for importing vendor shipments for one purchase order when case details are included.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Document>
    <WHSInboundLoadHeaderEntity ESTIMATEDARRIVALDATETIME="2021-04-25T11:00:00+00:00">
        <WHSInboundShipmentHeaderEntity VENDORSHIPMENTID="MVR_SNN_0004">
            <WHSInboundLoadPackingStructureEntity LICENSEPLATENUMBER="MVR_SNN_0004" PACKEDTOTALQUANTITY="2.00">
                <WHSInboundLoadPackingStructureCaseEntity PARENTPACKINGSTRUCTURELICENSEPLATENUMBER="MVR_SNN_0004" LICENSEPLATENUMBER="MVR_SNN_0004A" PACKEDTOTALQUANTITY="2.00" />
                <WHSInboundLoadPackingStructureLineV3Entity PURCHASEORDERNUMBER="00000175" ITEMNUMBER="A0001" PURCHASEORDERLINENUMBER="1" QUANTITY="2.00" UNITSYMBOL="pcs" />
            </WHSInboundLoadPackingStructureEntity>
        </WHSInboundShipmentHeaderEntity>
    </WHSInboundLoadHeaderEntity>
</Document>
```

### Example 3

The following example shows an XML file for importing vendor shipments for multiple purchase orders when case details are included.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Document>
    <WHSInboundLoadHeaderEntity TRACTORNUMBER="0000101">
        <WHSInboundShipmentHeaderEntity VENDORSHIPMENTID="VendASN_01" VENDORADDRESSCOUNTRYREGIONID = "USA" VendorAddressStreet = "123 Coffee Street" VENDORADDRESSSTATEID = "WA" VENDORADDRESSCITY = "Redmond" VENDORADDRESSZIPCODE = "98052">
            <WHSInboundLoadPackingStructureEntity LICENSEPLATENUMBER="LP_ASN_001">
                <WHSInboundLoadPackingStructureLineV3Entity PURCHASEORDERNUMBER="00000176" ITEMNUMBER="A0001" QUANTITY="100" UNITSYMBOL="pcs" />
            </WHSInboundLoadPackingStructureEntity>
        </WHSInboundShipmentHeaderEntity>
        <WHSInboundShipmentHeaderEntity VENDORSHIPMENTID="VendASN_02" VENDORADDRESSCOUNTRYREGIONID = "USA" VendorAddressStreet = "123 Coffee Street" VENDORADDRESSSTATEID = "WA" VENDORADDRESSCITY = "Redmond" VENDORADDRESSZIPCODE = "98052">
            <WHSInboundLoadPackingStructureEntity LICENSEPLATENUMBER="LP_ASN_001">
                <WHSInboundLoadPackingStructureLineV3Entity PURCHASEORDERNUMBER="00000177" ITEMNUMBER="A0001" QUANTITY="200" UNITSYMBOL="pcs" />
                <WHSInboundLoadPackingStructureLineV3Entity PURCHASEORDERNUMBER="00000177" ITEMNUMBER="P0004" QUANTITY="300" UNITSYMBOL="pcs" ITEMBATCHNUMBER="BN0001" />
            </WHSInboundLoadPackingStructureEntity>
            <WHSInboundLoadPackingStructureEntity LICENSEPLATENUMBER="LP_ASN_002">
                <WHSInboundLoadPackingStructureCaseEntity LICENSEPLATENUMBER="LP_ASN_002_C01">
                    <WHSInboundLoadPackingStructureCaseLineV3Entity PURCHASEORDERNUMBER="00000177" ITEMNUMBER="A0001" QUANTITY="400" UNITSYMBOL="pcs" />
                </WHSInboundLoadPackingStructureCaseEntity>
            </WHSInboundLoadPackingStructureEntity>
        </WHSInboundShipmentHeaderEntity>
    </WHSInboundLoadHeaderEntity>
</Document>
```

## Inbound ASN V5 entity example

The following subsection provide an example of ASN XML import files for **Inbound shipment orders** for _Inbound ASN V5_.
> [!NOTE]
> The _Inbound ASN V5_ uses a _MODULE_ field as part of both the _WHSInboundLoadPackingStructureEntity_ and the _WHSInboundLoadPackingStructureLineV5Entity_, it can be used for both purchase order (MODULE="Purch") and Inbound shipment orders (MODULE="InboundShipmentOrder")

### Example 4

The following example shows an XML file for importing shipments for one inbound shipment order when no case details are included.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Document>
    <WHSInboundLoadHeaderEntity TRACTORNUMBER="0000104">
        <WHSInboundShipmentHeaderEntity VENDORSHIPMENTID="VendASN_04">
            <WHSInboundLoadPackingStructureEntity MODULE="InboundShipmentOrder" LICENSEPLATENUMBER="LP_ASN_004">
                <WHSInboundLoadPackingStructureLineV5Entity MODULE="InboundShipmentOrder" ORDERNUMBER="IO04" ORDERLINENUMBER="1" ITEMNUMBER="A0001" QUANTITY="2" UNITSYMBOL="pcs"/>
            </WHSInboundLoadPackingStructureEntity>
        </WHSInboundShipmentHeaderEntity>
    </WHSInboundLoadHeaderEntity>
</Document>
```

## Inspect the results of importing an ASN file

Follow these steps to inspect the results of importing an ASN file.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Find and open a load that was created as part of an ASN import.
1. On the **Load** FastTab, you should see values that are based on the XML file.
1. On the **Load lines** FastTab, you should see purchase order numbers and item details that are based on the XML file.
1. On the Action Pane, on the **Ship and receive** tab, in the **Receive** group, select **Packing structure** to review the packing structure of the load.
1. On the **Pallets** FastTab, you should see license plates that are based on the XML file.
1. On the **Cases** FastTab, you should see cases that are based on the XML file.
1. On the **Items** FastTab, you should see items and quantities that are based on the XML file.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
