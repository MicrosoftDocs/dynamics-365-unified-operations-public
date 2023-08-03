---
title: Warehouse management only mode frequently asked questions
description: XXXX
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WHSSourceSystem, WHSShipmentOrderIntegrationMonitoringWorkspace, SysMessageProcessorMessage, BusinessEventsWorkspace, WHSInboundShipmentOrder, WHSOutboundShipmentOrder, WHSInboundLoadPlanningWorkbench, WHSShipmentPackingSlipJournal, WHSShipmentReceiptJournal, WHSParameters, ExtCodeTable, WHSOutboundShipmentOrderMessage, WHSInboundShipmentOrderMessage
ms.topic: faq
ms.date: 08/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Warehouse management only mode frequently asked questions

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

## What to do when a message processing is **Failed**?

The [message processing](../supply-chain-dev/message-processor.md) will retry three times before failing. You can use [**Business events**](../../fin-ops-core/dev-itpro/business-events/home-page.md) to be notified about this. Follow the [view log](../supply-chain-dev/message-processor.md#view-message-log) information for the **Message processor messages** page and use the information to take the next appropriate action of either moving the message back into reprocessing (**Queue** option), **Cancel** the message, or manually [update the message](#viewing-and-maintaining-shipment-order-messages).
> [!NOTE]
> Typically, data updated must happen before it make sense trying to reprocess the *Failed* message.

## Why does my message not get processed, but stays in the *Queued* state?

If you have multiple messages with dependencies (for example, for same order number) in the *Failed* state, you must either correct the data and move the message back into *Queued* state for reprocessing or *Cancel* the dependent messages beforehand.

## Why do I need to provide a **Country/Region** field value for my outbound shipment order?

The *Outbound shipment order* requires to create an address. For this to happen you must specify at least two field values the [countries/regions](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup#set-up-countryregion-information) and a *Name*. The *Country/Region* value must match existing data in the [**Address setup**](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup#set-up-countryregion-information). You can use the following message fields to provide the data:

- ConsigneeName
- ConsigneeCountryRegionId
- ReceiverName
- ReceiverCountryRegionId

## Why do I see all the modules and not only the ones that are needed for warehouse management processes?

The **Warehouse management only mode** is part of the larger Microsoft Dynamics Supply Chain Management deployment and thereby enabling you to use all the integration points being part of this. To limit the access to processes you must assign [**roles**](../../fin-ops-core/dev-itpro/sysadmin/role-based-security) only related to warehouse management processes, which will limit the access to other areas of the product.

- *Warehouse manager* – Enables and reviews processes, maintains master data, and responds to inquiries
- *Warehouse mobile device user* – Used to access the Warehouse Mobile Devices Portal service
- *Warehouse planner* – Setup and planning processes
- *Warehouse system integration operator* – Setup integration processes related to inbound and outbound shipment orders
- *Receiving clerk* – Working with inbound processes
- *Shipping clerk* – Working with outbound processes
- *Warehouse worker* – Working with daily warehouse processes

## Why do I get the error "No fiscal calendar has been defined for the ledger. In general ledger setup, select a fiscal calendar for the ledger." when posting a counting journal?

Unless you set up the *Released products* with an **Item model group** enabled with an *Inventory model* as **Non-valuated** with cleared *Post physical inventory* and *Post financial inventory* you'll need to set up all the costing and general ledger setup data like the [*fiscal calendars*](../../finance/budgeting/fiscal-calendars-fiscal-years-periods.md).

## Why do I get the error "The accounting currency hasn't been defined for the ledger. You must define the currency in the Ledger form." when processing warehouse operations?

Unless you set up the *Released products* with an **Item model group** enabled with an *Inventory model* as **Non-valuated** with cleared *Post physical inventory* and *Post financial inventory* you'll need to set up all the costing and general ledger setup data like the [*the currency in the ledger*](../../finance/general-ledger/configure-ledger.md).

## Why do I get the error "The accounting currency has not been defined for the ledger. You must define the currency in the Ledger form." when processing different order types?

Even though using *Released products* with an **Item model group** enabled with an *Inventory model* as **Non-valuated** with cleared *Post physical inventory* and *Post financial inventory* you'll need to setup costing data for orders currently not supported by the *Warehouse management only mode*.

## Why can't I just **Receive complete** what I have partly inbound registered

Depending on your setup an inbound load will either automatically get created as part of the *Inbound shipment order* import, via *ASN* import or via a manual process. In the current version the load line quantities must be fulfilled according to over-/under-delivery settings and the **Receiving completed** must be triggered manually.
<!-- Delivery policy -->

## Why do I see the error "Unable to update product receipt for a load with inbound shipment order lines" for my existing **Update product receipts** process?

In case of enabling the *Warehouse management only mode* capability and already running a periodic **Update product receipts** batch job for loads associated with purchase orders, you'll need to update the query for the batch job to exclude the inventory transaction updates for the *inbound shipment orders*. This can easily be done by adding the *Load details* entity with a *NotExist* join to the *Loads* entity followed by a range definition for the *Reference* field with *Criteria* = Inbound shipment order.
