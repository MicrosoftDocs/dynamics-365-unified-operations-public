---
title: Despatch advice for transfer orders to external shared warehouses
description: Learn how Supply Chain Management sends despatch advice for transfer orders that are shipped to external shared warehouses, enabling license plate receiving.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: WHSEWManagementSystem, WHSEWInboundShipmentOrderRequest, WHSDespatchAdviceMessage, WHSInboundShipmentOrder, WHSLoadTable, SysMessageProcessorMessage
ms.topic: overview
ms.date: 09/01/2026
ms.custom:
  - bap-template
---

# Despatch advice messages for transfer orders to external shared warehouses

[!include [banner](../includes/banner.md)]

When you ship a transfer order to an external shared warehouse, the system can automatically send a [despatch advice message](despatch-advice-notice.md) in addition to the inbound shipment order message. The despatch advice describes the physical structure of the shipment, including its pallets, license plates, quantities, batches, and serial numbers.

This capability extends the [transfer order received at an external warehouse](wms-only-mode-external-shared-warehouse.md#transfer-order-received-at-an-external-warehouse) process. It enables workers in the warehousing legal entity to use license plate receiving instead of receiving each inbound shipment order line or load item separately. It also preserves the packing and tracking-dimension details of the shipped inventory.

This article focuses on how Supply Chain Management automatically generates the message for transfer orders. For a detailed description of the despatch advice message structure, fields, processing, and replacement behavior, see [Import inbound ASNs as despatch advice messages](despatch-advice-notice.md).

## Prerequisites

For the system to automatically send despatch advice messages, you must be running Supply Chain Management version 10.0.50 or later.

## Information included in the despatch advice

The system creates a separate despatch advice for each external inbound shipment order that's represented on the shipped load.

| Document part | Information |
|---|---|
| Header | Source system, receiving warehouse, and the related inbound shipment order number. |
| Logistic units | License plates and their parent-child relationships, such as cases on a pallet. |
| Line items | Item number, shipped quantity and unit, batch or serial number, captured weight, and product dimensions. |

The generated message uses the same [despatch advice structure](despatch-advice-notice.md#message-structure) as an imported despatch advice. However, you don't have to import or construct the message. Supply Chain Management builds it from the packing structure and shipment item details that shipment confirmation creates for the transfer load.

### Transfer order header fields

To support transfer orders to external shared warehouses, the despatch advice message header includes the following fields. The system automatically populates both fields when it generates the message.

| Field | Meaning |
|---|---|
| `SourceSystemId` | The source system ID that's configured in the relation between the external warehouse management system and the warehousing legal entity. It identifies the source system that sent the transfer order information and enables source system item number mapping during despatch advice processing. |
| `SourceSystemOrderNumber` | The inbound shipment order origin ID that was generated for the transfer order shipment. It links the despatch advice to the corresponding inbound shipment order message and ensures that the inbound shipment order is processed before the despatch advice. |

When these fields are populated, the despatch advice is processed together with the related inbound shipment order messages in the *Shipment orders* message queue.

### Message identifiers

The system assigns the following values to the key fields on each generated despatch advice:

| Field | Value |
|---|---|
| `ShipperIdentification` | The source system ID that's configured in the relation between the external warehouse management system and the warehousing legal entity. This value identifies the order-processing legal entity as the shipper. |
| `DespatchAdviceIdentification` | The inbound shipment order origin ID that the system generates when it creates the external warehouse inbound shipment order request for the transfer order shipment. This value remains stable for the related inbound shipment order. |
| `MessageId` | The despatch advice identification followed by a period and a version number, such as `<DespatchAdviceIdentification>.1`. The version starts at 1 and increases each time the system sends another message for the same shipper and despatch advice identification. |

The combination of `ShipperIdentification` and `DespatchAdviceIdentification` identifies the despatch advice. A new `MessageId` identifies each version of that advice. Learn more in [Identify a despatch advice](despatch-advice-notice.md#identify-despatch-advice).

## How the messages are processed

When you ship-confirm a transfer order load to an external shared warehouse, the system processes the documents in the following sequence:

1. In the order-processing legal entity, shipment confirmation posts the transfer order shipping journal.
1. From the shipping journal, the system creates an *external warehouse inbound shipment order request*. As a result, an inbound shipment order message is sent to the warehousing legal entity.
1. The system builds a despatch advice from the license plate and item structure of the shipped load and sends it to the same legal entity.
1. The inbound shipment order message and despatch advice are placed in the *Shipment orders* message queue with the same order dependency. The [message processor](warehouse-message-processor-messages.md) processes the inbound shipment order message first and then processes the despatch advice.
1. The inbound shipment order message creates the inbound shipment order in the warehousing legal entity.
1. The despatch advice creates or updates the related inbound load, shipment, packing structure, and item details.

This ordering ensures that the inbound shipment order exists before the despatch advice tries to resolve its order lines.

## Receive the transfer order by license plate

After the inbound shipment order and despatch advice messages are accepted, follow these steps in the warehousing legal entity:

1. Go to **Warehouse management** \> **Loads** \> **All loads**, and open the load that was created for the inbound shipment order.
1. On the Action Pane, on the **Ship and receive** tab, in the **Receive** group, select **Packing structure**. Confirm that the expected license plates, cases, items, quantities, and tracking dimensions are present.
1. In the Warehouse Management mobile app, open a menu item that uses the *License plate receiving* or *License plate receiving and put away* process. Learn more in [License plate receiving via the Warehouse Management mobile app](warehousing-mobile-device-app-license-plate-receiving.md).
1. Scan the license plate that was shipped from the source warehouse, and complete the receiving steps.
1. Complete the [receiving completed process](wms-only-mode-shared-and-external-detail-use.md#receiving-completed) for the inbound load. The resulting external warehouse inbound shipment order update returns the received quantities to the order-processing legal entity and updates the transfer order.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
