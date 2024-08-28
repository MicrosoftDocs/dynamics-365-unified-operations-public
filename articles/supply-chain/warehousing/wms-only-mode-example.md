---
title: Example of using inbound and outbound shipment orders
description: This article provides an example scenario that shows how to create inbound and outbound shipment orders, including an outline on testing the creation process. 
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 01/29/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: WHSSourceSystem, WHSShipmentOrderIntegrationMonitoringWorkspace, SysMessageProcessorMessage, BusinessEventsWorkspace, WHSInboundShipmentOrder, WHSOutboundShipmentOrder, WHSInboundLoadPlanningWorkbench, WHSShipmentPackingSlipJournal, WHSShipmentReceiptJournal, WHSParameters, ExtCodeTable, WHSOutboundShipmentOrderMessage, WHSInboundShipmentOrderMessage
---

# Example of using inbound and outbound shipment orders

[!include [banner](../includes/banner.md)]
[!INCLUDE [azure-ad-to-microsoft-entra-id](../../includes/azure-ad-to-microsoft-entra-id.md)]

<!-- KFM: Preview until further notice -->

This article provides an example scenario that shows how to create inbound and outbound shipment orders via message processing. It uses the standard sample data that's associated with the *USMF* example legal entity (company).

## How to test the creation process

To try out the creation process for inbound and outbound shipment orders via messages, set the **Enable manual outbound shipment order message creation** and **Enable manual inbound shipment order message creation** options to *Yes* for a **Source system** record. You can then create shipment order messages directly on the [**Outbound shipment order messages** and **Inbound shipment order messages**](wms-only-mode-shared-and-external-detail-use.md#maintain-messages) pages.

Another quick way to post example messages is to use [Open Data Protocol (OData)](../../fin-ops-core/dev-itpro/data-entities/odata.md) requests.

In both example cases, the [message processor](../supply-chain-dev/message-processor.md) in Microsoft Dynamics 365 Supply Chain Management processes the messages and creates the orders in the warehouse system.

> [!TIP]
> To completely skip the shipment order creation processes via messages, you can create the inbound shipment orders and outbound shipment orders directly on the order pages by allowing the *Enable manual inbound shipment order creation* and *Enable manual outbound shipment order creation* settings for a source system.

The same message structure logic applies to both the inbound and outbound shipment order messages:

- Order header

    - Order line 1
    - Order line 2

        &hellip;

    - Order line *n*

- Complete

> [!TIP]
> For more examples of HTTP requests for creating messages and integrating inventory and product master data, go to the [dynamics365scm-warehouse repository on GitHub](https://github.com/microsoft/dynamics365scm-warehouse/tree/main/wom-http).

## Prerequisites

Before you can work through this example by using a Supply Chain Management environment, you must prepare your system in the following way:

- Check the version requirements, and enable the feature as described in [Enable and configure warehouse management only mode](wms-only-mode-setup.md).
- Work in a system where the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) is installed, and select the *USMF* legal entity.
- Set up at least one record on the **Source systems** page. This example scenario assumes that you've set up a source system where the **Source system** field is set to *ERP*. Learn more in [Configure your source systems](wms-only-mode-setup.md#source-systems).
- Set up the required number sequences as described in [Set up number sequences](wms-only-mode-setup.md#number-sequences).

## Set up authentication for the example

On the **Microsoft Entra ID applications** page, assign the *Admin* user to the client that's used for authentication during interaction with the Supply Chain Management environment from an external source. Alternatively, assign another user who has authentication access to the integration messages, such as the default *Warehouse System Integration Operator* role. If you use the same user as part of the product master data import, more privileges that are related to product master data entities must be added to the *Warehouse System Integration Operator* role.

When you post entities via [OData](../../fin-ops-core/dev-itpro/data-entities/odata.md), you must ensure either that the user's default company matches the company that the entity will be posted to, or that the company (`dataAreaId` value) is specified in the request payload messages. Either way, shipment order messages can be completed only if the company (`dataAreaId` value) is specified.

## Create shipment order messages

### <a name="simple-inbound-shipment-order-example"></a>Example of a simple inbound shipment order message

For the `InboundShipmentOrderMessages` inbound shipment order header message, you must provide the following data at a minimum:

- `MessageId`: *M1*
- `dataAreaId`: *USMF* (Optional, depending on the default authorization user company)
- `SourceSystemId`: *ERP*
- `OrderNumber`: *IO1*
- `ReceivingWarehouseId`: *51*

When you use variables, the `InboundShipmentOrderMessages` message looks like the following example.

``` JSON example
POST {{resource}}/data/InboundShipmentOrderMessages
{
"MessageId": "{{MessageId}}",
"dataAreaId": "{{dataAreaId}}",
"SourceSystemId": "{{SourceSystem}}",
"OrderNumber": "{{OrderNumber}}",
"ReceivingWarehouseId": "{{Warehouse}}"
}
```

The `InboundShipmentOrderLineMessages` message looks like the following example.

``` JSON
POST {{resource}}/data/InboundShipmentOrderLineMessages
{
"MessageId": "{{MessageId}}",
"dataAreaId": "{{dataAreaId}}",
"SourceSystemId": "{{SourceSystem}}",
"OrderNumber": "{{OrderNumber}}",
"OrderLineNumber": 1,
"ItemNumber": "A0001",
"ExpectedQuantity": 10,
"ExpectedUnitSymbol": "Pcs"
}
```

To commit the messages, post a *complete* message for the header and lines. The complete message looks something like the following example.

``` JSON
POST {{resource}}/data/InboundShipmentOrderMessages(MessageId='{{MessageId}}', dataAreaId='{{dataAreaId}}',SourceSystemId='{{SourceSystem}}', OrderNumber='{{OrderNumber}}')/Microsoft.Dynamics.DataEntities.Complete?cross-company=true
```

> [!NOTE]
> The `dataAreaId` value is used as part of the key to match against the released header and line messages. Therefore, the `dataAreaId` value must be specified. The suffix `?cross-company=true` is required only for messages where the company differs from the user's default company that's set up on the **Microsoft Entra ID applications** page.

### Example of a simple outbound shipment order message

For the `OutboundShipmentOrderMessages` outbound shipment order header message, you must provide the following data at a minimum:

- `MessageId`: *M2*
- `dataAreaId`: *USMF* (Optional, depending on the default authorization user company)
- `SourceSystemId`: *ERP*
- `OrderNumber`: *OO1*
- `ShipFromWarehouseId`: *51*
- `ConsigneeName` or `ReceiverName`: *Microsoft*
- `ConsigneeCountryRegionId` or `ReceiverCountryRegionId`: *USA*

When you use variables, the `OutboundShipmentOrderMessages` message looks like the following example.

``` JSON
POST {{resource}}/data/OutboundShipmentOrderMessages
{
"MessageId": "{{MessageId}}",
"dataAreaId": "{{dataAreaId}}",
"SourceSystemId": "{{SourceSystem}}",
"OrderNumber": "{{OrderNumber}}",
"ShipFromWarehouseId": "{{Warehouse}}",
"ConsigneeName": "{{ConsigneeName}}",
"ConsigneeCountryRegionId": "{{ConsigneeCountryRegionId}}"
}
```

The `OutboundShipmentOrderLineMessages` message looks like the following example.

``` JSON
POST {{resource}}/data/OutboundShipmentOrderLineMessages
{
"MessageId": "{{MessageId}}",
"dataAreaId": "{{dataAreaId}}",
"SourceSystemId": "{{SourceSystem}}",
"OrderNumber": "{{OrderNumber}}",
"OrderLineNumber": 1,
"ItemNumber": "A0001",
"OrderedQuantity": 10,
"OrderedUnitSymbol": "Pcs"
}
```

To commit the messages, post a *complete* message for the header. The complete message looks something like the following example.

``` JSON
POST {{resource}}/data/OutboundShipmentOrderMessages(MessageId='{{MessageId}}', dataAreaId='{{dataAreaId}}',SourceSystemId='{{SourceSystem}}', OrderNumber='{{OrderNumber}}')/Microsoft.Dynamics.DataEntities.Complete?cross-company=true
```

> [!NOTE]
> The `dataAreaId` value is used as part of the key to match against the released header and line messages. Therefore, the `dataAreaId` value must be specified. The suffix `?cross-company=true` is required only for messages where the company differs from the user's default company that's set up on the **Microsoft Entra ID applications** page.

## Message processor messages for shipment orders

After the two documents are imported into the [message queue](wms-only-mode-exchange-data.md#inbound-outbound-shipment-order-messages), you must use the [message processor](warehouse-message-processor-messages.md) to process them and create the actual inbound and outbound shipment orders.
