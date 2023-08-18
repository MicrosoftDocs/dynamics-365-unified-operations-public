---
title: Warehouse management only mode frequently asked questions
description: This article provides answers to frequently asked questions about warehouse management only mode.
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

# Warehouse management only mode frequently asked questions

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

## What should I do when a message is shown as "Failed" in the message processor?

The [message processor](../supply-chain-dev/message-processor.md) will retry three times before failing. You can use [business events](../../fin-ops-core/dev-itpro/business-events/home-page.md) to be notified about this. Follow the [view log](../supply-chain-dev/message-processor.md#view-message-log) information for the **Message processor messages** page and use that information to take the next appropriate action to either **Queue** the message (move it back into processing queue), **Cancel** it, or [update the message manually](wms-only-mode-using.md#maintain-messages).

> [!NOTE]
> Usually you'll need to correct errors the data before it makes sense to attempt to reprocess a failed message.

## Why does my message stay in the queued state instead of getting processed?

If you have multiple messages with dependencies that are in the *Failed* state (for example, for same order number), you must either correct the data and move the message back into the *Queued* state or *Cancel* the dependent messages.

## Why do I need to provide a Country/Region field value for my outbound shipment order?

Outbound shipment orders need to be able to create a shipping address. For this to happen, you must specify at least two field values: the [**Country/Region**](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup.md#set-up-countryregion-information) and a **Name**. The **Country/Region** value must match existing data in the [address setup](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup.md#set-up-countryregion-information). You can use the following message fields to provide the data:

- `ConsigneeName`
- `ConsigneeCountryRegionId`
- `ReceiverName`
- `ReceiverCountryRegionId`

See also [Master and reference data](wms-only-mode-exchange-data.md#master-data).

## Why does Supply Chain Management show all the modules instead of just those related to warehouse management?

Warehouse management only mode is part of a larger Supply Chain Management deployment and thereby enables you to use all the integration points. To limit a user's access to other modules, you must only assign those [security roles](../../fin-ops-core/dev-itpro/sysadmin/role-based-security.md) that are related to warehouse management processes. The relevant roles are:

- *Warehouse manager* – Enable and review processes, maintain master data, and respond to inquiries.
- *Warehouse mobile device user* – Access the *Warehouse Mobile Devices Portal* service.
- *Warehouse planner* – Work with setup and planning processes.
- *Warehouse system integration operator* – Set up integration processes related to inbound and outbound shipment orders.
- *Receiving clerk* – Work with inbound processes.
- *Shipping clerk* – Work with outbound processes.
- *Warehouse worker* – Work with daily warehouse processes.

## Why do I get the error "No fiscal calendar has been defined for the ledger. In general ledger setup, select a fiscal calendar for the ledger." when posting a counting journal?

Usually, Supply Chain Management requires that you configure several costing and general ledger settings, including [fiscal calendars](../../finance/budgeting/fiscal-calendars-fiscal-years-periods.md). However, you can remove this requirement by setting up item model groups that don't use these features, and associating those item model groups with the relevant released products. For details, see [Master and reference data](wms-only-mode-exchange-data.md#master-data).

## Why do I get the error "The accounting currency hasn't been defined for the ledger. You must define the currency in the Ledger form." when processing warehouse operations?

Usually, Supply Chain Management requires that you configure several costing and general ledger settings, including a [ledger currency](../../finance/general-ledger/configure-ledger.md). However, you can remove this requirement by setting up item model groups that don't use these features, and associating those item model groups with the relevant released products. For details, see [Master and reference data](wms-only-mode-exchange-data.md#master-data).

## Why do I get the error "The accounting currency hasn't been defined for the ledger. You must define the currency in the Ledger form." when processing different order types?

Warehouse management only mode uses just two types of documents: *inbound shipment orders* and *outbound shipment orders*. All other types of documents (such as *sales orders* or *purchase orders*) can only be processed if you have configured the required costing and general ledger options, regardless of your [item model group setup](wms-only-mode-exchange-data.md#master-data).

## Why can't I just **Receive complete** what I have partly inbound registered

Depending on your setup an inbound load will either automatically get created as part of the inbound shipment order import, via ASN import, or via a manual process. In the current version, the load line quantities must be fulfilled according to over-/under-delivery settings and the **Receiving completed** must be triggered manually.

## Why do I see the error "Unable to update product receipt for a load with inbound shipment order lines" for my existing "Update product receipts" process?

If you enable *Warehouse management only mode* and are already running a periodic *Update product receipts* batch job for loads associated with purchase orders, you'll need to update the query for the batch job to exclude inventory transaction updates for inbound shipment orders. You can do this by adding the *Load details* entity with a *NotExist* join to the *Loads* entity followed by a range definition for the *Reference* field with **Criteria** = *Inbound shipment order*.
