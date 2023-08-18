---
title: Example of using inbound and outbound shipment orders
description: This article provides an example scenario that shows how to create inbound and outbound shipment orders. 
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

<!-- KFM: Preview until further notice -->

This article provides an example scenario that shows how to create inbound and outbound shipment orders. It uses the standard sample data associated with the *USMF* example legal entity.

To create inbound and outbound shipment orders, a message must be posted using [OData](../../fin-ops-core/dev-itpro/data-entities/odata.md) requests. The [message processor](../supply-chain-dev/message-processor.md) in Supply Chain Management then processes the message, which creates the orders in the warehouse system.

The same message structure logic applies for both the inbound and outbound shipment order messages. The structure is as follows:

- Order header
    - Order line 1
    - Order line 2<br>
    ...
    - Order line *n*
- Complete

This example uses [Postman](../../fin-ops-core/dev-itpro/data-entities/third-party-service-test.md#query-odata-by-using-postman) to create simple orders with minimal payload.

The provided example data uses a process that doesn't depend on the default company for authorizing users, which means the messages must include a `dataAreaId` value.

> [!NOTE]
> To ease messages processing, [Postman](../../fin-ops-core/dev-itpro/data-entities/third-party-service-test.md#query-odata-by-using-postman) supports collections and environment variables that can be reused for all requests, including authorization. In this example, variables are indicated with "{{" and "}}".

## Prerequisites

Before you can work through this example using a Supply Chain Management environment, your system must be prepared as follows:

- Check the version requirements and enable the feature as described in [Enable and configure warehouse management only mode](wms-only-mode-setup.md).
- Work on a system where the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) is installed and select the *USMF* legal entity (company).
- Set up at least one record on the **Source systems** page. This example scenario assumes you have a source system set up with **Source system** set to *ERP*. See also [Configure you source systems](wms-only-mode-setup.md#source-systems).
- Set up the required number sequences, as described in [Set up number sequences](wms-only-mode-setup.md#number-sequences)

## Set up authentication for this example

On the **Microsoft Entra ID applications** page, assign the *Admin* user (or a user having authentication access to the integration messages, like the default *Warehouse System Integration Operator* role) to the client that is used for authentication while interacting with the Supply Chain Management environment from an external source. If you use the same user as part of the product master data import, you must add more privileges related to product master data entities to the *Warehouse System Integration Operator* role.

When posting entities via [OData](../../fin-ops-core/dev-itpro/data-entities/odata.md), you must ensure that either the user's default company matches the company to which the entity will be posted or that the company (`dataAreaId`) is specified in the request payload messages. Either way, the company (`dataAreId`) must be specified to complete shipment order messages.

## Create shipment order messages

### <a name="simple-inbound-shipment-order-example"></a>Simple inbound shipment order message example

For the inbound shipment order header message `InboundShipmentOrderMessages`, you must provide the following data as a minimum:

- `MessageId` = M1
- `dataAreaId` = USMF (optional, depending on the default authorization user company)
- `SourceSystemId` = ERP
- `OrderNumber` = IO1
- `ReceivingWarehouseId` = 51

When using [Postman](../../fin-ops-core/dev-itpro/data-entities/third-party-service-test.md#query-odata-by-using-postman) with variables, the `InboundShipmentOrderMessages` message looks like this:

``` JSON  example
POST {{EnvironmentUrl}}/data/InboundShipmentOrderMessages
{
"MessageId": "{{MessageId}}",
"dataAreaId": "{{dataAreaId}}",
"SourceSystemId": "{{SourceSystem}}",
"OrderNumber": "{{OrderNumber}}",
"ReceivingWarehouseId": "{{Warehouse}}"
}
```

And the `InboundShipmentOrderLineMessages` message will look like this:

``` JSON
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

Post a *complete* message for the header and lines to commit the messages. The complete message looks something like this:

``` JSON
POST {{EnvironmentUrl}}/data/InboundShipmentOrderMessages(MessageId='{{MessageId}}', dataAreaId='{{dataAreaId}}',SourceSystemId='{{SourceSystem}}', OrderNumber='{{OrderNumber}}')/Microsoft.Dynamics.DataEntities.Complete?cross-company=true
```

> [!NOTE]
> The `dataAreaId` value is used as part of the key to match up against the released header and line messages. Therefore, the `dataAreaId` value must be specified. The suffix `?cross-company=true` is only needed for messages where the company is different from the one used for the user default company set up on the the **Microsoft Entra ID applications** page.

### Simple outbound shipment order message example

For the outbound shipment order header message `OutboundShipmentOrderMessages`, you must provide the following data as a minimum:

- `MessageId` = M2
- `dataAreaId` = USMF  (optional, depending on the default authorization user company)
- `SourceSystemId` = ERP
- `OrderNumber` = OO1
- `ShipFromWarehouseId` = 51
- `ConsigneeName` or `ReceiverName` = Microsoft  
- `ConsigneeCountryRegionId` or `ReceiverCountryRegionId` = USA

When using [Postman](../../fin-ops-core/dev-itpro/data-entities/third-party-service-test.md#query-odata-by-using-postman) with variables, the `OutboundShipmentOrderMessages` message looks like this:

``` JSON
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

And the `OutboundShipmentOrderLineMessages` message will look like this:

``` JSON
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

Post a *complete* message for the header to commit the messages. The complete message looks something like this:

``` JSON
POST {{EnvironmentUrl}}/data/OutboundShipmentOrderMessages(MessageId='{{MessageId}}', dataAreaId='{{dataAreaId}}',SourceSystemId='{{SourceSystem}}', OrderNumber='{{OrderNumber}}')/Microsoft.Dynamics.DataEntities.Complete?cross-company=true
```

> [!NOTE]
> The `dataAreaId` value is used as part of the key to match up against the released header and line messages. Therefore, the `dataAreaId` value must be specified. The suffix `?cross-company=true` is only needed for messages where the company is different from the one used for the user default company set up on the the **Microsoft Entra ID applications** page.

## Message processor messages for shipment orders

After the two documents are imported into the [message queue](wms-only-mode-exchange-data.md#inbound-outbound-shipment-order-messages), you must then use the [message processor](warehouse-message-processor-messages.md) to process them and thereby create the actual inbound and outbound shipment orders.
