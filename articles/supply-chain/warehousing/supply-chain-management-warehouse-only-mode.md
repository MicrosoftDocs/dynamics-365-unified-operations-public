---
# required metadata

title: Supply Chain Management warehouse-only mode
description: Run all supply chain warehouse operations in Microsoft Dynamics 365 Supply Chain Management as part of a dedicated ecosystem that easily integrates with other ERP and order management systems via inbound and outbound shipment orders.
author: perlynne
ms.date: 28/04/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
ms.search.form: WHSSourceSystem, WHSShipmentOrderIntegrationMonitoringWorkspace, SysMessageProcessorMessage, BusinessEventsWorkspace, WHSInboundShipmentOrder, WHSOutboundShipmentOrder, WHSInboundLoadPlanningWorkbench, WHSShipmentPackingSlipJournal, WHSShipmentReceiptJournal, WHSParameters, ExtCodeTable
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: perlynne
ms.search.validFrom: 2023-04-24
ms.dyn365.ops.version: 10.0.36
---
**_DRAFT DOCUMENTATION FOR:_**
# Supply Chain Management warehouse-only mode
Running your warehouse processes with the **Supply Chain Management warehouse-only mode** will provide several deployment options to support the actual business needs of running your [warehouse management](warehouse-management-overview.md) processes.

![High level integations](./media/high-level-integrations.png)

One example being a dedicated LCS D365 cloud deployment only handling the warehouse operations and all integrations related to orders and financial processing handled outside this deployment. With this implementation concept it will only be needed to configure the processes around warehouse management as part of the D365 SCM cloud deployment.  

![SCM warehouse-only mode to ERP/Order system](./media/scm-wom-2-erp.png)

Another example is a more SCM integrated implementation methodology, having the warehouses enabled for D365 SCM processes like sales, purchase, production orders, etc. and at the same time handling warehouse operations for other ERP/order processing systems. With this type of implementation, the same warehouse instance can handle all the logistic warehouse processes, internal as well as external integrations.

![SCM warehouse-only mode to ERP/Order system](./media/scm-wms-scm-2-erp.png)

And then everything between the two above example deployment options, which for example could be running a dedicated legal entity within an existing D365 SCM deployment which only handles the warehouse management processes for external systems. All-in-all you can use the **Supply Chain Management in warehouse-only mode** exactly as needed. 

## <a name = "feature-management"></a> Feature management
To use the **Supply Chain Management warehouse-only mode** capability, your system must meet the following requirements:
- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.35 or later.
-  The feature that's named **(Preview) Supply Chain Management warehouse-only mode** must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
   - In version 10.0.35 this will require enablement of the flight: **_WHSWarehouseOrdersConfigurationFeature_**
- With the feature enabled you can open the **Warehouse management > Setup > Warehouse management integration > Source systems** used to define the integration systems. To enable all the functionalities, you must at least insert one record into this entity.

## Data exchange
Running **Supply Chain Management in warehouse-only mode** requires integration to be defined between the ERP/Order systems and the Microsoft Dynamics 365 Supply Chain Management system.
Integration between systems is a widespread challenge, but nevertheless of huge importance getting to work seamlessly.
In general, three categories of interactions are needed for the **Supply Chain Management in warehouse-only mode**:
- Document data (like purchase and sales orders)
- Master data (like products)
- Progress data (like dispatch and receiving advice and inventory on-hand updates)

Many different integration methodologies can be used for the above, but the following is the recommended integration process.

### Document data
To inform the warehouse management system about what physical inventory to receive and ship you can easily use the inbound and outbound shipment order messages. These messages are designed with header and lines data.
With the introduction of these two new, lightweight inbound and outbound warehouse interface documents, it is no longer required to set up multiple documents for inbound and outbound operations (sales orders, purchase orders, transfer orders, etc.) that essentially serve the same purpose from a pure warehouse management perspective. This will, for example, simplify integration with ERP and order management systems and enable the use of the Dynamics 365 warehouse management functionality in an ERP agnostic manner.

#### <a name="inbound-outbound-shipment-order-messages"></a>Inbound and outbound shipment order messages
The **inbound shipment order** and the **outbound shipment order** messages can be imported via a [**Dataverse integration**](../../../../power-platform/admin/data-integrator.md) or directly integrated with the [Odata](../../fin-ops-core/dev-itpro/data-entities/odata.md) shipment order message entities in a optimal manner.
A following [**message processing**](warehouse-message-processor-messages.md) will validate the import process by ensuing consistent data between the systems, both when it comes to the master data like products, but also the order progress status alignments, making the D365 SCM inbound/outbound shipment orders actionable for the warehouse management processes, by not allowing creation or updating of invalid/unsupported order data. It is recommended to process the messages as part of a periodic batch job triggered by the  **Message processor** page where you must use the **Shipment Orders** *Message queue*.

![SCM warehouse-only mode to ERP/Order system](./media/shipment-order-integrations.png)

Having the shipment order line field data related to the released products in the [**D365 SCM product information management module**](../pim/product-information.md) requires the products to be created before the system can accept the shipment order messages.
### Master data
Different master data will need to be recorded to be able to run your warehouse management system, here the [**data entities**](../../fin-ops-core/dev-itpro/data-entities/data-entities.md) can be used to easily import the data.
You can read more about the support of importing product master data via the [**product data entities**](../pim/data-entities.md) and get an overview of the [**Product information management entities**](../../../../../common-data-model/schema/core/operationscommon/entities/supplychain/productinformationmanagement/overview.md).
Besides the product master data you must at least have defined the [countries/regions](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup#set-up-countryregion-information) which will be used for the outbound shipment order import process, to create an address.

### Progress data
External systems will have many different business process requests for the warehouse management system. One example being the progress of a sales order. Now, the external systems can of course keep polling for this kind of information, but to honor this process the D365 SCM warehouse management system can be set up to provide [**Business events**](../../fin-ops-core/dev-itpro/business-events/home-page.md).

#### <a name="business-events"></a>Business events
The D365 SCM warehouse management system can be setup to provide [**Business events**](../../fin-ops-core/dev-itpro/business-events/home-page.md) to keep the external systems informed about the progress and actions going on. With this setup the external systems don’t need to keep polling for information which might not have changed since the last request of information, but instead only need to act when getting informed.
Several out-of-the-box [**Business events**](../../fin-ops-core/dev-itpro/business-events/home-page.md) are supported for warehouse integration:
Non-exhaustive list:
| Business event ID                                 | Description                              |
|---------------------------------------------------|------------------------------------------|
| InventCountingJournalPostedBusinessEvent          | Counting journal posted                  |
| WHSOutboundNotificationCreatedBusinessEvent       | Outbound warehouse notification created  |
| WHSShipmentOrderMessageChangedStatusBusinessEvent | Status update for shipment order message |
| WHSShipmentPackingSlipJournalModifiedBusinessEvent| Shipment packing slips updated           |
| WHSShipmentReceivingJournalModifiedBusinessEvent  | Shipment receipts updated                |
| WhsWaveExecutedBusinessEvent                      | Wave executed                            |

As a minimum it is recommended to use the following  [**Business events**](../../fin-ops-core/dev-itpro/business-events/home-page.md):
- *InventCountingJournalPostedBusinessEvent* - To be informed about an inventory on-hand adjustment has happened and where to look up the detailed information about the update.

- *WHSShipmentPackingSlipJournalModifiedBusinessEvent* - To be informed about an outbound shipment confirmation process has happened and where to look up the detailed dispatch advice data, which for example can be used for a sales invoicing process.

- *WHSShipmentReceivingJournalModifiedBusinessEvent* - To be informed about an inbound receiving completion process has happened and where to look up the detailed receiving advice data, which for example can be used for a purchase order invoicing process.

## <a name = "source-systems"></a> Source systems
The **Supply Chain Management in warehouse-only mode** shipment order integration must be configured with information about the source systems going to provide inbound and outbound order messages. This gets defined in the **Warehouse management > Setup > Warehouse management integration > Source systems** page and is a prerequisite to be able to view the **Inbound shipment orders** and **Outbound shipment orders** and the related processes around the integration.
The **Source system** name must be identical with the name in the provided message before a message can be accepted getting imported into D365 SCM.
Additional policy settings can be used as part of the **Source systems** page to control the shipment order import processes, for example it is possible to define **Message value mapping** for item and warehouse identifications and define if loads for inbound shipment orders automatically gets created as part of the **Inbound shipment order policies** definition.
> [!NOTE]
> When mapping the items to [**Bar codes**](../pim/tasks/create-bar-code-product.md) remember to enable the *Scanning* setting for the bar codes. For product variants it is only the "ItemNumber" field being used from the order line messages when using **Message value mapping**.

## Warehouse integration monitoring
The **Warehouse management > Workspaces > Warehouse integration monitoring** page provides an overview of the warehouse integration messages and an easy way to navigate to the related areas, for example to the [**System administration > Message processor > Message processor messages**](warehouse-message-processor-messages.md) page.

# Inbound shipment orders
**Warehouse management > Inquiries and reports > Inbound shipment orders** are documents that represents information about the expected product receipts. The **Inbound shipment orders** page contains an ‘internal SCM warehouse representation’ of the available shipment orders in a **Header** and **Lines** view. For each of the lines it is possible to view detailed **inventory transactions** as well as any associated **warehouse work**.
In case you are already knowledgeable about D365 SCM, you might find this document comparable with a minimal purchase order document. No financial postings as part of the [**General ledger**](../../finance/general-ledger/general-ledger.md) will be used for this source document.
> [!NOTE]
> The internal inbound shipment order number must be unique. You can define using the external order numbers as internal numbers and thereby not needing to use a [number sequence](#number-sequences) for the order.

# Outbound shipment orders
**Warehouse management > Inquiries and reports > Outbound shipment orders** are documents that represents information about the requested product dispatch. The **Outbound shipment orders** page contains an ‘internal SCM warehouse representation’ of the available shipment orders in a **Header** and **Lines** view. For each of the lines it is possible to view detailed **inventory transactions** as well as any associated **warehouse work**.
> [!NOTE]
> The internal outbound shipment order number must be unique. You can define using the external order numbers as internal numbers and thereby not needing to use a [number sequence](#number-sequences) for the order.

In case you are already knowledgeable about D365 SCM, you might find this document comparable with a minimal sales order document having some of the same **Reservation** and [**Release to warehouse**](release-to-warehouse-process.md) processes. As part of the [**Source systems**](#source-systems) definitions you can trigger the reservation as part of the document import and even define to reject a shipment order which cannot get reserved partly or fully.

In the first release of the **Supply Chain Management warehouse-only mode** the outbound shipment order lines do not out-of-the-box support getting associated with loads before the [**Release to warehouse**](release-to-warehouse-process.md) process, this can only happen as part of the processing of the warehouse waving.

## Automatic release of outbound shipment orders
To enable automatically release to warehouse you can use the **Warehouse management > Release to warehouse > Automatic release of outbound shipment orders** batch job process. Please refer to the [Release to warehouse](release-to-warehouse-process.md) topic to learn more.


# Inbound process
![SCM warehouse-only mode inbound process](./media/inbound-wom-process.png)
The high-level process for inbound processing is as following:
- External systems provides *Inbound shipment order* messages
- The messages get processed in *Supply Chain Warehouse-only mode* and orders get created
- Inbound loads gets created manually via **Inbound load planning workbench**, via [**ASN**](import-asn-data-entity), or automatically during message processing based on the [**Source systems** - **Inbound shipment order policy**](#source-systems) definition.
- Inventory receiving gets processed and the inbound shipment order transactions get *Registered* via one of the currently supported [**Warehouse management mobile app**](configure-mobile-devices-warehouse#configure-menu-items-to-create-work-for-another-worker-or-process) processes:
    - *License plate receiving (and put away)*
    - *Load item receiving (and put away)*
    - *Mixed license plate receiving (and put away)* for source document line identification method *Load item receiving*
- **Receiving completed** processes will follow related to a load which will update the load status to *Received* and generate [**Shipment receipts**](#shipment-receipts) and trigger **Business event** for the external systems.
- The external systems read and uses the [**Shipment receipts**](#shipment-receipts) data for further processing, like for example purchase order invoicing in case of having purchase orders associated to the *inbound shipment orders*.
- The *Inbound shipment orders* get finalized by running the periodic back-ground process **Post shipment receipts**.

> [!NOTE]
> The **Receiving completed** process requires load lines being fully received in 10.0.35. Future plans exists for having automated process handling based on policy settings.

## <a name="shipment-receipts"></a> Shipment Receipts
In the **Warehouse management > Inquiries and reports > Shipment receipts** page you can view the detailed line transactions related to the received inventory. The data is version controlled and you can follow the **Posting status** on the header data.
The header will get from *Ready for posting* into *Posted* by processing the **Warehouse management > Periodic tasks > Post shipment receipts** batch job which will ensure the related inbound shipment order line transactions get into a finalized transaction state for the the warehouse management module.

# Outbound process
![SCM warehouse-only mode outbound process](./media/outbound-wom-process.png)
The high-level process for outbound processing is as following:
- External system provides *Outbound shipment order* messages
- The messages gets processed in *Supply Chain Warehouse-only mode* and orders gets created. Based on the [**Source system**](#source-systems) policies reservations will automatically be handled as part of the message processing or will need to get processed manually or as part of the release process.
- The orders gets released for further warehouse processing, either manually or automatically via the batch job **Automatic release of outbound shipment orders** and based on the [wave template](wave-templates.md) definitions warehouse work can get created and released immediately.
- The outbound warehouse work get processed and the related outbound shipment order line transactions get updated to status *Picked*.
- The loads get outbound ship confirmed which will create **Business events** and [**Shipment packing slip**](#shipment-packing-slips) data for the external systems.
- The external systems read and uses the [**Shipment packing slip**](#shipment-packing-slips) data for further processing, like for example sales order invoicing in case of having sales orders associated to *outbound shipment orders*.
- The *Outbound shipment orders* get finalized by running the periodic back-ground process **Post shipment packing slips**.

> [!NOTE]
> Reversal of shipment packing slips will be supported as long as the related outbound shipment order line transactions have not been finalized.

## <a name="shipment-packing-slips"></a>Shipment packing slips
In the **Warehouse management > Inquiries and reports > Shipment packing slips** page you can view the detailed line transactions related to the shipped inventory and print out a report of the data via the **Preview/Print** option. You can control the printed inventory dimension values as part of the **Warehouse management > Setup > Warehouse management parameters - Reports - Shipment packing slip**.

The **Shipment packing slip** data is version controlled and you can follow the **Posting status** on the header data.
The header will get from *Ready for posting* into *Posted* by processing the **Warehouse management > Periodic tasks > Post shipment packing slips** batch job which will ensure the related outbound shipment order line transactions get into a finalized transaction state for the the warehouse management module.

> [!NOTE]
> In case of not having defined a language for the order the report will fall back to use the company specific language settings.


# Inventory on-hand updates between the systems
The warehouse management module supports multiple inventory on-hand update processes using the [Counting journal](../inventory/inventory-journals.md#counting), you can read more about the cycle counting process [here](cycle-counting.md).
As part of a journal posting process a [business event](#business-events) gets triggered and the integrated systems can read about the updates as part of the [counting journal entities](https://learn.microsoft.com/en-us/common-data-model/schema/core/operationscommon/entities/supplychain/inventoryandwarehousemanagement/inventinventorycountingjournallineentity). Here it is important only to act on the updated quantities not to get out of sync as part of the updates. Please refer to the scenario below related to this:

**PREREQUSITE:**

The external system and the D365 SCM WMS on-hand is in sync:
|Item number |ERP on-hand |WMS on-hand |
|------------|------------|------------|
|A0001       |0 pcs       |0 pcs       |

**WHEN1:**

D365 SCM WMS receives item number A0001 10 pcs against an inbound shipment order without *Receiving completed* processing and thereby not informing the external system about this yet!

**THEN1:**

The external system and D365 SCM WMS is out of sync:
|Item number |ERP on-hand |WMS on-hand |
|------------|------------|------------|
|A0001       |0 pcs       |10 pcs      |

**WHEN2:**

In D365 SCM WMS an on-hand adjustment (Counting journal) get posted for A0001 adding 1 pcs more on-hand:
|Item number |ERP on-hand |WMS on-hand |
|------------|------------|------------|
|A0001       |0 pcs       |11 pcs      |

**THEN2:**

The external system will get informed via business event that an adjustment has happened and as part of this process the reading of the journal posting going from 10 pcs. to 11 pcs. in the WMS, it is important the external system only consider the updated quantity of 1 pcs:
|Item number |ERP on-hand |WMS on-hand |
|------------|------------|------------|
|A0001       |1 pcs       |11 pcs      |

**WHEN3:**

D365 SCM WMS will process a **Receiving completed** process related to the received 10 pcs. of A0001

**THEN3:**

The external system will get informed via business event and can read the shipment receipts information and update on-hand with an additional 10 pcs.
|Item number |ERP on-hand |WMS on-hand |
|------------|------------|------------|
|A0001       |11 pcs      |11 pcs      |

> [!WARNING]
> In 10.0.35 it is not possible to run **Supply Chain Management in warehouse-only mode** without using the [**General ledger**](../../finance/general-ledger/general-ledger.md) and thereby for example not needing to configure the [*inventory postings*](../../finance/general-ledger/inventory-posting.md) and [*fiscal calendars*](../../finance/budgeting/fiscal-calendars-fiscal-years-periods.md).
>
> It is planned to have [**counting journal**](../inventory/tasks/define-inventory-counting-processes.md) processes for **Released products** associated with an **Item model group** indicated with *Inventory model* as **Unvalued**. For now simply use posting with cost values as zero.

# Example of using inbound and outbound shipment orders

This section provides an example scenario that shows how to create inbound and outbound shipment orders. To ease a tryout the examples are running on the standard [demo data](../../../fin-ops-core/fin-ops/get-started/demo-data.md) for the **USMF** legal entity.

To create inbound and outbound shipment orders, a message entity needs to be posted using [Odata](../../fin-ops-core/dev-itpro/data-entities/odata.md) requests. That message then needs to be processed by the [**Message processor**](message-processor.md) in D365 SCM which will create the orders in the warehouse system.
The same message structure logic applies for both the inbound and outbound shipment order messages which are:
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
Make sure having the **Supply Chain Management in warehouse-only mode** enabled as described in the [Feature management](#feature-management) section.

### Azure Active Directory
In the **Azure Active Directory** page, assign the *Admin* user, or a user having authentication access to the integration messages, like the default **_Warehouse System Integration Operator_** role to the client that will be utilized for authentication while interacting with the D365 SCM environment from an external source.

When posting entities via [Odata](../../fin-ops-core/dev-itpro/data-entities/odata.md), it's important to ensure that either the user's default company matches the company in which the entity will be posted or to specify the company (dataAreaId), in the request payload messages. In any case the company (dataAreId) must get specified to complete the messages for the shipment orders.

### Source systems example
Make sure a record is created in the **Source systems** page, this will enable the full use of the capability.
For this example define *Source system* as **_ERP_**.

### <a name=”number-sequences”></a>Number sequences
For the order import process the [number sequences](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview) for *Outbound shipment orders* and *Inbound shipment orders* must be defined when not using the same order numbers as the external system provides in D365 SCM WMS. In general, make sure to define all the number sequences associated with the **Warehouse management > Setup > Warehouse management parameters > Number sequences** which includes the following additional number sequences:
- Outbound shipment order
- Inbound shipment order
- Shipment packing slip
- Shipment receipt
- Warehouse outbound notification id
- Load line inventory pick

> [!TIP]
> You can quickly enable all number sequences by using the **_Generate_** option on the [**Number sequences**](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview) page.

## Create shipment order messages

### Simple inbound shipment order message example
For the inbound shipment order header message **InboundShipmentOrderMessages**, you must provide the following data as a minimum:
- MessageId = M1
- dataAreaId = USMF  (optional depending on default authorization user company)
- SourceSystemId = ERP
- OrderNumber = IO1
- ReceivingWarehouseId = 51

Using the [Postman](../../fin-ops-core/dev-itpro/data-entities/third-party-service-test#query-odata-by-using-postman) with variables the message will look like:
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
> The dataAreaId is used as part of the key to match up against the released header and line messages and must be specified. The suffix *?cross-company=true* is only needed when having messages for a different company than the used **Azure Active Directory applications** user default company.

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
> The dataAreaId is used as part of the key to match up against the released header and line messages and must be specified. The suffix *?cross-company=true* is only needed when having messages for a different company than the used **Azure Active Directory applications** user default company.

## Message processor messages for shipment orders
Having the two documents imported into the [message queue](#inbound-outbound-shipment-order-messages) you now need to get them [processed](warehouse-message-processor-messages.md) and thereby getting the actual **Inbound and outbound shipment orders** created in the **Supply Chain Management warehouse-only mode** system.

# Troubleshooting guides

###### What to do when a message processing is **Failed**?
The message processing will retry three times before failing. Note that you can use [**Business events**](../../fin-ops-core/dev-itpro/business-events/home-page.md) to be notified about this. Follow the [view log](../supply-chain-dev/message-processor.md#view-message-log) information for the **Message processor messages** page and use the information to take the next appropriate action of either moving the message back into  reprocessing (**Queue** option) or **Cancel** the message. Typically, data updated must happen before it make sense trying to reprocess the *Failed* message.

###### Why does my message not get processed, but stays in the *Queued* state?
In case you have multiple messages with dependencies (e.g. for same order number) which has **_Failed_**, you need to either correct the data and move the message back into **_Queued_** state for reprocessing or **_Cancel_** the depending messages beforehand.

######  Why do I need to provide a **Country/Region** field value for my outbound shipment order?
The *Outbound shipment order* requires to create an address. For this to happen you must specify at least two field values the [countries/regions](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup#set-up-countryregion-information) and a *Name*. The *Country/Region* value must match existing data in the [**Address setup**](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup#set-up-countryregion-information). You can use the following message fields to provide the data:
- ConsigneeName
- ConsigneeCountryRegionId
- ReceiverName 
- ReceiverCountryRegionId

<!-- perlynne
### Warehouse management initiation wizard
### Outbound configuration wizard
### Inbound configuration wizard
## Security roles
-->