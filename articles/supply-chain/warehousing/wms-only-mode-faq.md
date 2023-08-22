---
title: Warehouse management only mode FAQ
description: This article provides answers to frequently asked questions about Warehouse management only mode.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form:
ms.topic: faq
ms.date: 08/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Warehouse management only mode FAQ

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

## What should I do when a message is shown as Failed in the message processor?

The [message processor](../supply-chain-dev/message-processor.md) retries three times before it fails. You can use [business events](../../fin-ops-core/dev-itpro/business-events/home-page.md) to be notified about this failure. Follow the [view log](../supply-chain-dev/message-processor.md#view-message-log) information for the **Message processor messages** page, and use that information to take the next appropriate action: queue the message (that is, move it back into the processing queue), cancel it, or [manually update it](wms-only-mode-using.md#maintain-messages).

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

For more information, see [Master and reference data](wms-only-mode-exchange-data.md#master-data).

## Why does Supply Chain Management show all the modules instead of just those that are related to warehouse management?

Warehouse management only mode is part of a larger deployment of Microsoft Dynamics 365 Supply Chain Management. Therefore, it lets you use all the integration points. To limit a user's access to other modules, assign only those [security roles](../../fin-ops-core/dev-itpro/sysadmin/role-based-security.md) that are related to warehouse management processes:

- *Warehouse manager* – Enable and review processes, maintain master data, and respond to inquiries.
- *Warehouse mobile device user* – Access the *Warehouse Mobile Devices Portal* service.
- *Warehouse planner* – Work with setup and planning processes.
- *Warehouse system integration operator* – Set up integration processes that are related to inbound and outbound shipment orders.
- *Receiving clerk* – Work with inbound processes.
- *Shipping clerk* – Work with outbound processes.
- *Warehouse worker* – Work with daily warehouse processes.

## Why do I receive the following error when I post a counting journal: "No fiscal calendar has been defined for the ledger. In general ledger setup, select a fiscal calendar for the ledger"?

Usually, Supply Chain Management requires that you configure several costing and general ledger settings, including [fiscal calendars](../../finance/budgeting/fiscal-calendars-fiscal-years-periods.md). However, you can remove this requirement by setting up item model groups that don't use these features and associating those item model groups with the relevant released products. For more information, see [Master and reference data](wms-only-mode-exchange-data.md#master-data).

## Why do I receive the following error when I process warehouse operations: "The accounting currency hasn't been defined for the ledger. You must define the currency in the Ledger form"?

Usually, Supply Chain Management requires that you configure several costing and general ledger settings, including a [ledger currency](../../finance/general-ledger/configure-ledger.md). However, you can remove this requirement by setting up item model groups that don't use these features and associating those item model groups with the relevant released products. For more information, see [Master and reference data](wms-only-mode-exchange-data.md#master-data).

## Why do I receive the following error when I process different order types: "The accounting currency hasn't been defined for the ledger. You must define the currency in the Ledger form"?

Warehouse management only mode uses just two types of documents: *inbound shipment orders* and *outbound shipment orders*. All other types of documents (such as *sales orders* or *purchase orders*) can be processed only if you've configured the required costing and general ledger options, regardless of your [item model group setup](wms-only-mode-exchange-data.md#master-data).

## Why can't I just Receive complete what I have partly inbound registered?

Depending on your setup, an inbound load is automatically created as part of the inbound shipment order import, via advanced shipping notice (ASN) import, or via a manual process. In the current version, the load line quantities must be fulfilled according to over-delivery and under-delivery settings, and *receiving completed* must be manually triggered.

## Why do I receive the following error for my existing Update product receipts process: "Unable to update product receipt for a load with inbound shipment order lines"?

If you enable Warehouse management only mode and are already running a periodic *Update product receipts* batch job for loads that are associated with purchase orders, you must update the query for the batch job to exclude inventory transaction updates for inbound shipment orders. To update the query, add the *Load details* entity, and specify a *NotExist* join to the *Loads* entity. Then add a range definition for the **Reference** field, where **Criteria** = *Inbound shipment order*.
