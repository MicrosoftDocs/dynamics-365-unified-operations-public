---
title: Warehouse management only mode FAQ
description: Access answers to frequently asked questions about Warehouse management only mode, including questions about messages in the queued state.
author: Mirzaab
ms.author: mirzaab
ms.topic: conceptual
ms.date: 04/27/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Warehouse management only mode FAQ

[!include [banner](../includes/banner.md)]

This article provides answers to frequently asked questions about Warehouse management only mode.

## What should I do when a message is shown as Failed in the message processor?

The [message processor](../supply-chain-dev/message-processor.md) retries three times before it fails. You can use [business events](../../fin-ops-core/dev-itpro/business-events/home-page.md) to be notified about this failure. Follow the [view log](../supply-chain-dev/message-processor.md#view-message-log) information for the **Message processor messages** page, and use that information to take the next appropriate action: queue the message (that is, move it back into the processing queue), cancel it, or [manually update it](wms-only-mode-shared-and-external-detail-use.md#maintain-messages).

> [!NOTE]
> Usually, you must correct errors in the data before it makes sense to try to reprocess a failed message.

## Why does my message stay in the Queued state instead of being processed?

If multiple messages that have dependencies are in the *Failed* state (for example, for the same order number), you must either correct the data and move the message back to the *Queued* state, or cancel the dependent messages.

## Why do I have to provide a Country/Region field value for my outbound shipment order?

Outbound shipment orders must be able to create a shipping address. Therefore, you must specify at least two field values: [**Country/Region**](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup.md#set-up-countryregion-information) and **Name**. The **Country/Region** value must match existing data in the [address setup](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup.md#set-up-countryregion-information). You can use the following message fields to provide the data:

- `ConsigneeName`
- `ConsigneeCountryRegionId`
- `ReceiverName`
- `ReceiverCountryRegionId`

Learn more in [Master and reference data](wms-only-mode-exchange-data.md#master-data).

## Why does Supply Chain Management show all the modules instead of just those that are related to warehouse management?

Warehouse management only mode is part of a larger deployment of Microsoft Dynamics 365 Supply Chain Management. Therefore, it lets you use all the integration points. To limit a user's access to other modules, assign only those [security roles](../../fin-ops-core/dev-itpro/sysadmin/role-based-security.md) that are related to warehouse management processes:

- *Warehouse manager* – Enable and review processes, maintain master data, and respond to inquiries.
- *Warehouse mobile device user* – Access the *Warehouse Mobile Devices Portal* service.
- *Warehouse planner* – Work with setup and planning processes.
- *Warehouse system integration operator* – Set up integration processes that are related to inbound/outbound shipment orders and on-hand inventory synchronization.
- *Receiving clerk* – Work with inbound processes.
- *Shipping clerk* – Work with outbound processes.
- *Warehouse worker* – Work with daily warehouse processes.

## Why do I receive the following error when I post a counting journal: "No fiscal calendar has been defined for the ledger. In general ledger setup, select a fiscal calendar for the ledger"?

Usually, Supply Chain Management requires that you configure several costing and general ledger settings, including [fiscal calendars](../../finance/budgeting/fiscal-calendars-fiscal-years-periods.md). However, you can remove this requirement by setting up item model groups that don't use these features and associating those item model groups with the relevant released products. Learn more in [Master and reference data](wms-only-mode-exchange-data.md#master-data).

## Why do I receive the following error when I process warehouse operations: "The accounting currency hasn't been defined for the ledger. You must define the currency in the Ledger form"?

Usually, Supply Chain Management requires that you configure several costing and general ledger settings, including a [ledger currency](../../finance/general-ledger/configure-ledger.md). However, you can remove this requirement by setting up item model groups that don't use these features and associating those item model groups with the relevant released products. Learn more in [Master and reference data](wms-only-mode-exchange-data.md#master-data).

## Why do I receive the following error when I process different order types: "The accounting currency hasn't been defined for the ledger. You must define the currency in the Ledger form"?

Warehouse management only mode uses just two types of documents: *inbound shipment orders* and *outbound shipment orders*. All other types of documents (such as *sales orders* or *purchase orders*) can be processed only if you've configured the required costing and general ledger options, regardless of your [item model group setup](wms-only-mode-exchange-data.md#master-data).

## Why can't I just Receive complete what I have partly inbound registered?

Depending on your setup on the **Inbound shipment order policies** FastTab of the **Source systems** page (**Warehouse management** \> **Setup** \> **Warehouse management integration** \> **Source systems**), inbound loads might be created in any of the following ways:

- Automatically, when an inbound shipment order is imported
- Automatically, when an advanced shipping notice (ASN) is imported
- Via a manual process
- As part of the Warehouse Management mobile app receiving process
- As part of an *Order receiving completed* process

When the system creates load data as a result of processing an inbound shipment order message, the delivery policy controls whether load quantities are adjusted to the received quantities, or whether the received quantities must match the load line quantities, as part of the [*Receiving completed* process](inbound-load-handling.md#receive-complete-confirm).

## Why do I receive the following error for my existing Update product receipts process: "Unable to update product receipt for a load with inbound shipment order lines"?

If you enable Warehouse management only mode and are already running a periodic *Update product receipts* batch job for loads that are associated with purchase orders, you must update the query for the batch job to exclude inventory transaction updates for inbound shipment orders. To update the query, add the *Load details* entity, and specify a *NotExist* join to the *Loads* entity. Then add a range definition for the **Reference** field, where **Criteria** = *Inbound shipment order*.

## Why do I receive the following error when I process a transfer order: "The accounting currency has not been defined for the ledger. You must define the currency in the Ledger form"?

In addition to setting up item model groups that don't use costing and general ledger settings (see [Master and reference data](wms-only-mode-exchange-data.md#master-data)), you must enable [Warehouse-specific inventory transactions](warehouse-transactions.md) for the *Transfer issue* and *Transfer receipt* warehouse scenarios.

## Can I attach documents and notes to inbound and outbound shipment orders?

Yes. Both inbound and outbound shipment order messages support document attachments. For more information, see the descriptions of *Inbound shipment order messages composite entity* and *Outbound shipment order messages composite entity* in [Data management](../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md). These entities contain the child entities *Inbound shipment order document attachment messages* and *Outbound shipment order document attachment messages*.

## Why can't I see and search for page names that are related to Warehouse management only mode?

Even if the *Warehouse management only mode* feature is enabled, you must create a record on the **Source systems** page before the system can look up the related pages. In addition, the current user's default company must have a source system set up to search for the page names. Learn more in [Enable and configure Warehouse management only mode](wms-only-mode-setup.md).

## Why doesn't my registered inventory transaction have a load ID?

If you use the [item arrival journal](../inventory/arrival-overview.md) process to receive updated inbound shipment order line quantities, inventory transactions won't be associated with a load. To achieve this result, you must use the *Order receiving completed* process, which creates loads for registered inventory transactions that aren't associated with a load. This process can be triggered directly from an inbound shipment order or via the **Inbound shipment order receiving completed** background process (available at **Warehouse management** \> **Periodic tasks** \> **Inbound shipment order receiving completed**).

## Why do I receive the following error when processing shipment orders: "Not able to resolve released item/variant for external item ID [ItemId]"?

When processing shipment orders, you may receive the following error, even though a related item or variant exists:

> Not able to resolve released item/variant for external item ID [ItemId].

This error occurs because released products and variants must be linked to a source system through the [Source system items](wms-only-mode-exchange-data.md#master-data) data entity. This is crucial for recording how item and variant numbers must be handled for each external [source system](wms-only-mode-setup.md#source-systems).

## Why aren't any external inventory updates recorded after I run external shared warehouse processing?

In one typical case, you create a counting journal for an item, which adjusts the on-hand inventory for the selected warehouse. Before you proceed, make sure that the **Warehouse inventory update log** page shows the information that you need for this adjustment. If it doesn't, you must verify that all the required **Source system** and **Source system item** settings are in place.

Even if the warehouse inventory update log has the correct information, it sends the data to the **External inventory updates** page only for the warehouse inventory dimensions that are connected through the external warehouse management system and the relevant warehouses. For more information about how to configure this process, see [Warehouse management only mode with external shared warehouses](wms-only-mode-external-shared-warehouse.md).
