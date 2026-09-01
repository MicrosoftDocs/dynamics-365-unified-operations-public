---
title: Import inbound ASNs as despatch advice messages
description: Learn how to import inbound advanced shipping notices (ASNs) as despatch advice messages that support processing dependencies and full-document updates.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 07/23/2026
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form: WHSDespatchAdviceMessage, WHSDespatchAdviceMessageEntity, WHSDespatchAdviceCompositeEntity, WHSInboundShipmentOrder, SysMessageProcessorMessage
---

# Import inbound ASNs as despatch advice messages

[!INCLUDE [banner](../../includes/banner.md)]

Advanced shipping notices (ASNs) notify you about vendor deliveries. They help the sender describe the contents of a shipment—such as the items, quantities, and packaging—so that warehouse workers can prepare to receive it.

A *despatch advice* is an inbound ASN that you import as a *despatch advice message*. Instead of creating warehouse records directly through data entities, the system queues the message and handles it asynchronously by using the [message processor](warehouse-message-processor-messages.md). This approach supports integrations where related documents must be processed in sequence, and it provides the following capabilities:

- **Message dependencies** – A despatch advice can depend on a prior message so that a source order is guaranteed to be imported *before* the ASN that references it.
- **Full-document updates** – You can correct a previously imported despatch advice by resubmitting the whole document. The document is replaced in full, and records that are no longer part of the shipment are cleaned up automatically. Learn more in [Update or correct a despatch advice](#update-or-correct-a-despatch-advice).

> [!IMPORTANT]
> Despatch advice messages apply only to items that are enabled for warehouse management processes (WMS). Before you can process a despatch advice, the referenced purchase order or [inbound shipment order](wms-only-mode-overview.md) must already be registered in the system.

> [!NOTE]
> The *Inbound ASN* data entities remain available for importing ASNs directly, without the message processor. Learn more in [Import inbound ASNs through data entities](import-asn-data-entity.md).

## Despatch advice message structure

A despatch advice message is a composite document that maps shipment details to warehouse records. It uses three entities that you import together through the *Despatch advice composite* entity (`WHSDespatchAdviceCompositeEntity`).

| Document part | Entity | What it represents |
|---|---|---|
| Header | `WHSDespatchAdviceMessageEntity` | The shipment notification, including carrier, weights, and shipper address. Becomes an inbound load and shipment. |
| Logistic unit | `WHSDespatchAdviceLogisticUnitMessageEntity` | A physical container that's identified by a serial shipping container code (SSCC) or license plate—for example, a pallet, case, or carton. |
| Line item | `WHSDespatchAdviceLineItemMessageEntity` | A product inside a logistic unit, with its quantity and inventory dimensions. |

### Identify a despatch advice

Each despatch advice is identified by the combination of two fields on the header:

- `ShipperIdentification` – The vendor (shipper) account that the shipment comes from.
- `DespatchAdviceIdentification` – The stable business ID of the despatch advice.

Because the identification is scoped to the shipper, different vendors can independently use the same `DespatchAdviceIdentification` value. The load and shipment IDs are generated automatically during processing—you don't provide them.

### Provide header, transport, and address details

Besides the required identification fields, the header (`WHSDespatchAdviceMessageEntity`) carries optional information about the shipment. Use `ReceivingWarehouseId` to specify the warehouse that receives the load, and populate any of the following groups of fields as needed.

| Group | Fields |
|---|---|
| Transport and carrier | `ShippingCarrierCode`, `ShippingCarrierGroupId`, `ShippingCarrierServiceId`, `TractorNumber`, `TrailerNumber`, `BrokerId`, `CarNumber`, `TransportationBookingNumber`, `MasterBillOfLadingId`, `ProNumber`, `SealNumber`, `InspectionSealNumber`, `VesselName`, `VoyageNumber`, `EstimatedArrivalDateTime` |
| Weights | `ActualGrossWeight`, `ActualNetWeight`, `ActualTareWeight`, `ActualWeightUnitSymbol` |
| Shipment | `DeliveryTermsCode`, `ShipperReference`, `ShipperDeliveryNoteId`, `ShipperDeliveryNoteDocumentDate` |
| Shipper address | `ShipperAddressCountryRegionId`, `ShipperAddressStreet`, `ShipperAddressCity`, `ShipperAddressStateId`, `ShipperAddressZipCode` |

### Nest logistic units by using a flat list

Logistic units are provided as a *flat list* under the header rather than as nested XML elements. You express the container hierarchy (for example, cases on a pallet) by using two fields on each logistic unit:

- `LogisticUnitIdentification` – The SSCC or license plate of this container.
- `ParentLogisticUnitIdentification` – The SSCC of the container that this unit sits inside. Leave it empty for a top-level unit.

This model supports any nesting depth (pallet → case → carton) while keeping the document flat. Line items are attached to the logistic unit that physically holds them.

### Provide item details for batches, catch weight, and product variants

Use the following optional fields on each line item (`WHSDespatchAdviceLineItemMessageEntity`) to describe the goods in more detail.

| Detail | Fields |
|---|---|
| Batch | `ItemBatchNumber`, `ItemBatchExpirationDate` |
| Catch weight | `CapturedWeight`, `CapturedWeightUnitSymbol` |
| Product variant dimensions | `ProductColorId`, `ProductSizeId`, `ProductStyleId`, `ProductConfigurationId`, `ProductVersionId` |
| Serial number | `ItemSerialNumber` |

For example, the following line reports a batch-tracked item that has a batch number, an expiration date, and a color variant.

```xml
<WHSDespatchAdviceLineItemMessageEntity ITEMNUMBER="A0001" DESPATCHEDQUANTITY="40" DESPATCHEDQUANTITYUNITSYMBOL="ea" ITEMBATCHNUMBER="BN0001" ITEMBATCHEXPIRATIONDATE="2027-11-11" PRODUCTCOLORID="Blue" ORDERNUMBER="00000055" ORDERLINENUMBER="1" />
```

> [!NOTE]
> For a catch-weight item, if `CapturedWeightUnitSymbol` differs from the item's catch-weight unit, the weight is converted during processing.

### Integrate with a source system

When you integrate an external system with [Warehouse management only mode](wms-only-mode-overview.md), the despatch advice can reference the [source system](wms-only-mode-setup.md#source-systems) that sent it. In this case, the external system uses its own item numbers, which differ from the item numbers in the receiving company. The following header field enables the translation:

- `SourceSystemId` – The source system that the despatch advice comes from.

When `SourceSystemId` is specified and the logistic unit belongs to the *Inbound shipment order* module, the `ItemNumber` on each line item is treated as a *source system item number*. During processing, it's translated into the receiving company's item number through the [source system item](wms-only-mode-exchange-data.md#master-data) mapping (as seen on the **Source system items** page). The original source system item number is preserved on the message, and the resolved local item number is stored on the ASN item.

> [!NOTE]
> If the specified `SourceSystemId` has no item mapping for a line's item number, processing fails with an error. If `SourceSystemId` is empty, the `ItemNumber` value is used as-is, with no translation.

## Import a despatch advice message

Import despatch advice messages by using the *Despatch advice composite* entity through any of the following methods:

- [Data management](../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md) import (for example, an XML file–based import), using the *Despatch advice composite* entity
- [Open Data Protocol (OData)](../../fin-ops-core/dev-itpro/data-entities/odata.md), using the individual message entities (see [Import a despatch advice by using OData](#odata))
- [Dataverse](/power-platform/admin/data-integrator)

The following sections show XML import files for the composite entity. Each XML element represents an entity, and each attribute represents a field.

The overall structure nests line items inside logistic units, and logistic units inside the header:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Document>
    <WHSDespatchAdviceMessageEntity>
        <WHSDespatchAdviceLogisticUnitMessageEntity>
            <WHSDespatchAdviceLineItemMessageEntity />
        </WHSDespatchAdviceLogisticUnitMessageEntity>
    </WHSDespatchAdviceMessageEntity>
</Document>
```

> [!TIP]
> For more example XML files, see the despatch advice test resources in the **SCMTestCommon** model.

### Example 1: One pallet for a purchase order

This example imports a single license plate that contains one purchase order line. Because no module is specified, the line defaults to the *Purchase order* module, and `ORDERNUMBER` refers to a purchase order.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Document>
    <WHSDespatchAdviceMessageEntity MESSAGEID="DA-MSG-0001" DESPATCHADVICEIDENTIFICATION="DA-1001" SHIPPERIDENTIFICATION="US-101" RECEIVINGWAREHOUSEID="24" ESTIMATEDARRIVALDATETIME="2026-07-20T10:00:00Z">
        <WHSDespatchAdviceLogisticUnitMessageEntity LOGISTICUNITIDENTIFICATION="LP-0001">
            <WHSDespatchAdviceLineItemMessageEntity ITEMNUMBER="A0001" DESPATCHEDQUANTITY="10" DESPATCHEDQUANTITYUNITSYMBOL="pcs" ORDERNUMBER="00000176" ORDERLINENUMBER="1" />
        </WHSDespatchAdviceLogisticUnitMessageEntity>
    </WHSDespatchAdviceMessageEntity>
</Document>
```

### Example 2: Two cases on a pallet

This example nests two cases inside a pallet. The pallet is a top-level logistic unit, and each case references the pallet through `PARENTLOGISTICUNITIDENTIFICATION`. Items are attached to the cases that hold them, and one line specifies a batch number.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Document>
    <WHSDespatchAdviceMessageEntity MESSAGEID="DA-MSG-0002" DESPATCHADVICEIDENTIFICATION="DA-1002" SHIPPERIDENTIFICATION="US-101" RECEIVINGWAREHOUSEID="24">
        <WHSDespatchAdviceLogisticUnitMessageEntity LOGISTICUNITIDENTIFICATION="PAL-001" />
        <WHSDespatchAdviceLogisticUnitMessageEntity LOGISTICUNITIDENTIFICATION="CASE-001" PARENTLOGISTICUNITIDENTIFICATION="PAL-001">
            <WHSDespatchAdviceLineItemMessageEntity ITEMNUMBER="A0001" DESPATCHEDQUANTITY="12" DESPATCHEDQUANTITYUNITSYMBOL="pcs" ORDERNUMBER="00000177" ORDERLINENUMBER="1" />
        </WHSDespatchAdviceLogisticUnitMessageEntity>
        <WHSDespatchAdviceLogisticUnitMessageEntity LOGISTICUNITIDENTIFICATION="CASE-002" PARENTLOGISTICUNITIDENTIFICATION="PAL-001">
            <WHSDespatchAdviceLineItemMessageEntity ITEMNUMBER="P0004" DESPATCHEDQUANTITY="20" DESPATCHEDQUANTITYUNITSYMBOL="pcs" ITEMBATCHNUMBER="BN0001" ORDERNUMBER="00000177" ORDERLINENUMBER="2" />
        </WHSDespatchAdviceLogisticUnitMessageEntity>
    </WHSDespatchAdviceMessageEntity>
</Document>
```

### Example 3: An inbound shipment order

To import a despatch advice for an [inbound shipment order](wms-only-mode-overview.md), set the `MODULE` attribute on the logistic unit to `InboundShipmentOrder`. In this case, `ORDERNUMBER` must be the external (source system) order number, which is mapped to the matching inbound shipment order during processing.

This example also specifies `SOURCESYSTEMID` on the header. As a result, the `ITEMNUMBER` value (`ERP-A0001`) is the source system item number and is translated into the receiving company's item number.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Document>
    <WHSDespatchAdviceMessageEntity MESSAGEID="DA-MSG-0003" DESPATCHADVICEIDENTIFICATION="DA-1003" SHIPPERIDENTIFICATION="EXT-VENDOR-1" SOURCESYSTEMID="ERP" RECEIVINGWAREHOUSEID="24">
        <WHSDespatchAdviceLogisticUnitMessageEntity LOGISTICUNITIDENTIFICATION="LP-9001" MODULE="InboundShipmentOrder">
            <WHSDespatchAdviceLineItemMessageEntity ITEMNUMBER="ERP-A0001" DESPATCHEDQUANTITY="5" DESPATCHEDQUANTITYUNITSYMBOL="pcs" ORDERNUMBER="IO04" ORDERLINENUMBER="1" />
        </WHSDespatchAdviceLogisticUnitMessageEntity>
    </WHSDespatchAdviceMessageEntity>
</Document>
```

## <a name="odata"></a>Import a despatch advice by using OData

Instead of importing the composite XML file, you can post a despatch advice through [OData](../../fin-ops-core/dev-itpro/data-entities/odata.md). You post to the individual message entities—first the header, then each logistic unit, and then each line item—and finally post a *Complete* action to queue the message for processing. The [message processor](../message-processor/message-processor.md) then processes the message just as it does for an imported XML file.

Use the following entity collections:

- `DespatchAdviceMessages` – The despatch advice header.
- `DespatchAdviceLogisticUnitMessages` – The logistic units.
- `DespatchAdviceLineItemMessages` – The line items.

Each child message carries the parent keys (`ShipperIdentification`, `DespatchAdviceIdentification`, and `MessageId`, plus `LogisticUnitIdentification` for line items) so that it's linked to the correct header and logistic unit.

The following example posts the header message:

```json
POST {{resource}}/data/DespatchAdviceMessages
{
    "ShipperIdentification": "US-101",
    "DespatchAdviceIdentification": "DA-1001",
    "MessageId": "DA-MSG-0001",
    "dataAreaId": "USMF",
    "ReceivingWarehouseId": "24"
}
```

The following example posts a logistic unit that belongs to the header:

```json
POST {{resource}}/data/DespatchAdviceLogisticUnitMessages
{
    "ShipperIdentification": "US-101",
    "DespatchAdviceIdentification": "DA-1001",
    "MessageId": "DA-MSG-0001",
    "dataAreaId": "USMF",
    "LogisticUnitIdentification": "LP-0001"
}
```

The following example posts a line item that belongs to the logistic unit:

```json
POST {{resource}}/data/DespatchAdviceLineItemMessages
{
    "ShipperIdentification": "US-101",
    "DespatchAdviceIdentification": "DA-1001",
    "MessageId": "DA-MSG-0001",
    "LogisticUnitIdentification": "LP-0001",
    "dataAreaId": "USMF",
    "ItemNumber": "A0001",
    "DespatchedQuantity": 10,
    "DespatchedQuantityUnitSymbol": "pcs",
    "OrderNumber": "00000176",
    "OrderLineNumber": 1
}
```

To queue the message for processing, post the *Complete* action for the header.

```json
POST {{resource}}/data/DespatchAdviceMessages(ShipperIdentification='US-101',DespatchAdviceIdentification='DA-1001',MessageId='DA-MSG-0001',dataAreaId='USMF')/Microsoft.Dynamics.DataEntities.Complete?cross-company=true
```

> [!NOTE]
> The `dataAreaId` value is part of the key that matches the line messages to the header. Therefore, specify it in each message. Add the `?cross-company=true` suffix only when the company differs from the user's default company that's set up on the **Microsoft Entra ID applications** page.

## Update or correct a despatch advice

Despatch advice messages use *replace by new message* semantics. To update a shipment, resubmit the complete, authoritative document with the same `SHIPPERIDENTIFICATION` and `DESPATCHADVICEIDENTIFICATION`, but a new `MESSAGEID`.

When the update is processed, the header and all child records are overwritten from the new message—including empty values—and any logistic units and line items that are no longer part of the shipment are removed. There's no partial or delta update mode, so always send the full document.

## Process despatch advice messages

Imported messages are queued and then handled by the message processor. To process them, schedule a batch job by following these steps:

1. Go to **System administration** > **Message processor** > **Message processor**.
1. In the **Message queue** field, select **Despatch advice messages**.
1. Specify a processing interval, and then schedule the batch job.

During processing, each message resolves or creates the inbound load and shipment, rebuilds the logistic unit hierarchy as license plates and packing structures, and creates the ASN item lines. The message status is then set to *Accepted*, or to *Failed* if a validation error occurs. For more information, see [Schedule message processing by using the message processor batch job](../message-processor/message-processor.md#processor-batch-job).

## Monitor processing results

You can monitor despatch advice processing in the following ways:

- **Message processor messages** – Go to **System administration** > **Message processor** > **Message processor messages** to review message content, find failed messages, and reprocess them. For more information, see [Message processor messages for warehouse management processes](warehouse-message-processor-messages.md).
- **Business events** – Set up the *Despatch advice message changed status* [business event](../../fin-ops-core/dev-itpro/business-events/home-page.md) so that downstream systems are alerted when a message succeeds or fails.

## Inspect the results of processing a despatch advice

After a despatch advice message is accepted, follow these steps to inspect the load that it created:

1. Go to **Warehouse management** > **Loads** > **All loads**.
1. Find and open the load that was created for the despatch advice.
1. On the **Load lines** FastTab, review the order numbers, items, and quantities.
1. On the Action Pane, on the **Ship and receive** tab, in the **Receive** group, select **Packing structure** to review the license plates, cases, and items that were built from the logistic units.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
