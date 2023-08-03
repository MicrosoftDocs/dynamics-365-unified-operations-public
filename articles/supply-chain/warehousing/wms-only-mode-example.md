---
title: Example of using inbound and outbound shipment orders
description: XXXX
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WHSSourceSystem, WHSShipmentOrderIntegrationMonitoringWorkspace, SysMessageProcessorMessage, BusinessEventsWorkspace, WHSInboundShipmentOrder, WHSOutboundShipmentOrder, WHSInboundLoadPlanningWorkbench, WHSShipmentPackingSlipJournal, WHSShipmentReceiptJournal, WHSParameters, ExtCodeTable, WHSOutboundShipmentOrderMessage, WHSInboundShipmentOrderMessage
ms.topic: how-to
ms.date: 08/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Example of using inbound and outbound shipment orders

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

This section provides an example scenario that shows how to create inbound and outbound shipment orders. To ease a tryout, the examples are running on the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) for the **USMF** legal entity.

To create inbound and outbound shipment orders, a message entity needs to be posted using [OData](../../fin-ops-core/dev-itpro/data-entities/odata.md) requests. That message then needs to be processed by the [**Message processor**](../supply-chain-dev/message-processor.md) in Supply Chain Management, which will create the orders in the warehouse system.

The same message structure logic applies for both the inbound and outbound shipment order messages, which are:

``` Message structure:
- Order header
   - Order line 1
   - Order line 2
   - Order line … 
- Complete
```

To showcase basic examples, [Postman](../../fin-ops-core/dev-itpro/data-entities/third-party-service-test#query-odata-by-using-postman) is used in the following to create simple orders with minimal payload.
The provided example data uses the process of not being depending on the default company for the authorization user and the messages are therefore containing a *dataAreaId* value.

> [!NOTE]
> To ease the messages processing [Postman](../../fin-ops-core/dev-itpro/data-entities/third-party-service-test#query-odata-by-using-postman) supports collections and environment variables that can be reused for all the requests, including the *Authorization*. You will in the following see the used variables within "{{" "}}" indications.

## Prerequisites

### Feature enablement

Make sure having the **Warehouse management only mode** enabled as described in the [Feature management](#feature-management) section.

### Microsoft Entra ID applications

In the **Microsoft Entra ID applications** page, assign the *Admin* user, or a user having authentication access to the integration messages, like the default ***Warehouse System Integration Operator*** role to the client that is used for authentication while interacting with the Supply Chain Management environment from an external source. In case you use the same user as part of the product master data import you must add more privileges related to product master data entities to the ***Warehouse System Integration Operator*** role.

When posting entities via [OData](../../fin-ops-core/dev-itpro/data-entities/odata.md), it's important to ensure that either the user's default company matches the company in which the entity will be posted or to specify the company (dataAreaId), in the request payload messages. In any case, the company (dataAreId) must get specified to complete the messages for the shipment orders.

### Source systems example

Make sure a record is created in the **Source systems** page, this enables the full use of the capability.

For this example, define *Source system* as ***ERP***.

### <a name=”number-sequences”></a>Number sequences

For the order import process, the [number sequences](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview) for *Outbound shipment orders* and *Inbound shipment orders* must be defined when not using the same order numbers as the external system provides in Supply Chain Management WMS. In general, make sure to define all the number sequences associated with the **Warehouse management > Setup > Warehouse management parameters > Number sequences** which includes the following extra number sequences:

- Outbound shipment order
- Inbound shipment order
- Shipment packing slip
- Shipment receipt
- Warehouse outbound notification ID
- Load line inventory pick

> [!TIP]
> You can quickly enable all number sequences by using the ***Generate*** option on the [**Number sequences**](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview) page.

## Create shipment order messages

### <a name="simple-inbound-shipment-order-example"></a>Simple inbound shipment order message example

For the inbound shipment order header message **InboundShipmentOrderMessages**, you must provide the following data as a minimum:

- MessageId = M1
- dataAreaId = USMF (optional depending on default authorization user company)
- SourceSystemId = ERP
- OrderNumber = IO1
- ReceivingWarehouseId = 51

Using the [Postman](../../fin-ops-core/dev-itpro/data-entities/third-party-service-test#query-odata-by-using-postman) with variables, the message will look like:

``` JSON InboundShipmentOrderMessages example
POST {{EnvironmentUrl}}/data/InboundShipmentOrderMessages
{
"MessageId": "{{MessageId}}",
"dataAreaId": "{{dataAreaId}}",
"SourceSystemId": "{{SourceSystem}}",
"OrderNumber": "{{OrderNumber}}",
"ReceivingWarehouseId": "{{Warehouse}}"
}
```

and post **Inbound shipment order line** message:

``` JSON InboundShipmentOrderLineMessages example
POST {{EnvironmentUrl}}/data/InboundShipmentOrderLineMessages
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

Post **Complete** message for the header and lines to commit the messages

``` JSON InboundShipmentOrderMessages Complete example
POST {{EnvironmentUrl}}/data/InboundShipmentOrderMessages(MessageId='{{MessageId}}', dataAreaId='{{dataAreaId}}',SourceSystemId='{{SourceSystem}}', OrderNumber='{{OrderNumber}}')/Microsoft.Dynamics.DataEntities.Complete?cross-company=true
```

> [!NOTE]
> The dataAreaId is used as part of the key to match up against the released header and line messages and must be specified. The suffix *?cross-company=true* is only needed when having messages for a different company than the used **Microsoft Entra ID applications** user default company.

### Simple outbound shipment order message example

For the outbound shipment order header message **OutboundShipmentOrderMessages**, you must provide the following data as a minimum:

- MessageId = M2
- dataAreaId = USMF  (optional depending on default authorization user company)
- SourceSystemId = ERP
- OrderNumber = OO1
- ShipFromWarehouseId = 51
- ConsigneeName or ReceiverName = Microsoft  
- ConsigneeCountryRegionId or ReceiverCountryRegionId = USA

Using the [Postman](../../fin-ops-core/dev-itpro/data-entities/third-party-service-test#query-odata-by-using-postman) with variables the message will look like:

``` JSON OutboundShipmentOrderMessages example
POST {{EnvironmentUrl}}/data/OutboundShipmentOrderMessages
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

and post **Outbound shipment order line** message:

``` JSON OutboundShipmentOrderLineMessages example
POST {{EnvironmentUrl}}/data/OutboundShipmentOrderLineMessages
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

Post *Complete* message for the header and lines to commit the messages

``` JSON OutboundShipmentOrderMessages Complete example
POST {{EnvironmentUrl}}/data/OutboundShipmentOrderMessages(MessageId='{{MessageId}}', dataAreaId='{{dataAreaId}}',SourceSystemId='{{SourceSystem}}', OrderNumber='{{OrderNumber}}')/Microsoft.Dynamics.DataEntities.Complete?cross-company=true
```

> [!NOTE]
> The dataAreaId is used as part of the key to match up against the released header and line messages and must be specified. The suffix *?cross-company=true* is only needed when having messages for a different company than the used **Microsoft Entra ID applications** user default company.

## Message processor messages for shipment orders

Having the two documents imported into the [message queue](#inbound-outbound-shipment-order-messages) you now need to get them [processed](warehouse-message-processor-messages.md) and thereby getting the actual **Inbound and outbound shipment orders** created in the **Warehouse management only mode** system.
