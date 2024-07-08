---
title: Configure unannounced returns in Warehouse management only mode
description: Learn how to configure unannounced returns in Warehouse management only mode by setting up source systems, source system disposition codes, return item receiving policies, and external warehouse management systems.
author: mq55qm
ms.author: mq55qm
ms.topic: how-to
ms.date: 07/29/2024
ms.custom: bap-template
ms.reviewer: kamaybac
audience: Application User
ms.search.region: Global
ms.search.form: WHSSourceSystem, WHSSourceSystemDispositionCode, WHSInboundShipmentOrder, WHSParameters, WHSInboundShipmentOrderMessage, WHSReturnItemReceivingPolicy
---

# Configure unannounced returns in Warehouse management only mode

[!include [banner](../includes/banner.md)]

This article explains how to configure unannounced returns in Warehouse management only mode and integrate it with External shared warehouse by setting up source systems, source system disposition codes, return item receiving policies, and external warehouse management systems.
It covers both the Blind returns and Return details receiving.

> [!NOTE]
> You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.41 or later to have access to this feature.

## <a name="prerequisites-and-basic-setup"></a>Prerequisites and basic setup

To use unannounced returns in Warehouse management only mode, you first need to setup the Warehouse management only mode. See details in [Enable and configure Warehouse management only mode](wms-only-mode-setup.md).

To enable the External shared warehouse integration, you need to setup that part of the system as well. See details in [Warehouse management only mode with external shared warehouses](wms-only-mode-external-shared-warehouse).

The basic setup is the same as for the [Receive unannounced sales returns](sales-returns-unannounced.md), so please check there for the details.

## <a name="source-system-configuration"></a>Source system configuration

1. Go to **Warehouse management** \> **Setup** \> **Warehouse management integration** \> **Source systems**.
2. Select the source system you have already created in the previous steps.
3. In the Inbound shipment orders fast tab
  - Set Enable returns process to Yes.
  - Set the Number sequnce code.
  - Set the Return order type.
    > [!NOTE]
    > If your source system is Microsoft Dynamics 365 Supply Chain Management (external shared warehouse integration scenario), the value must be set to 'Return' in order for the integration to work properly.
4. In the shipment orders fast tab
  - Set the Outbound shipment processing policy to a policy which has the Enforce shipment to order matching set to Yes.
  - For return details receiving, Enable return details creation must be set to Yes.
