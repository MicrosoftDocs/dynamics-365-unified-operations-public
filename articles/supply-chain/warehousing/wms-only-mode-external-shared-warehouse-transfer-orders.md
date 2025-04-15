---
title: Transfer orders in Warehouse management only mode with external shared warehouses
description: Learn how to set up Microsoft Dynamics 365 Supply Chain Management to handle transfer orders when you use external shared warehouses. This article highlights aspects of the transfer orders process that works differently when used to transfer to or from external shared warehouse.
author: mq55qm
ms.author: jususnja
ms.reviewer: kamaybac
ms.search.form: WHSSourceSystem, WHSEWManagementSystem, InventTransferOrder
ms.topic: how-to
ms.date: 04/15/2025
ms.custom: 
  - bap-template
---

# Tranfer orders with external shared warehouses

[!include [banner](../includes/banner.md)]

This article explains how to set up Microsoft Dynamics 365 Supply Chain Management to handle transfer orders with external shared warehouses. Most aspects of the transfer order processing work in the same way, regardless of whether you use external shared warehouses. This article highlights the differences.

Transfer orders with external shared warehousing mean that either the source, destination, or both warehouses in a transfer order are external. Learn more about the external shared warehouses [Warehouse management only mode with external shared warehouses](wms-only-mode-external-shared-warehouse.md).

## Prerequisites

Before you can use the features described in this article, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.44 or later.
- Set up external shared warehouses as described in [Warehouse management only mode with external shared warehouses](wms-only-mode-external-shared-warehouse.md).
- In the warehouse configuration of the externally managed warehouse, apart from a *default location*, you also need to setup a *default license plate location*. This location will be used as a temporary location when processing a transfer order. When shipping from an external warehouse, an update about what has been shipped from it is received and it contains a license plate. Inventory is then moved from a *default location* to a *default license plate location* and the transfer order is processed against that location.

## Ship from external warehouse

When a transfer order is released to the warehouse, in the same way as described with sales orders in [Warehouse management only mode with external shared warehouses](wms-only-mode-external-shared-warehouse.md), *external warehouse outbound shipment order requests* are created from shipments and sent to an external warehouse. Once external warehouses processes the shipments, an *external warehouse outbound shipment order update* is sent back. When that update is processed, the inventory that has been shipped becomes *Picked* and this enables further processing of the transfer order as usual.

## Ship to external warehouse

When the first part of shipping from a warehouse in the transfer order is processed, a transfer order shipping journal is created. If the destination warehouse is external, then once that journal is created, an *external warehouse inbound shipment order request* gets created and sent to an external warehouse. Once external warehouse receives the goods in the warehouse, an *external warehouse inbound shipment order update* will be sent back. This process is similar to purchase orders in [Warehouse management only mode with external shared warehouses](wms-only-mode-external-shared-warehouse.md). When that update is processed, the inventory that has been sent to the external warehouse gets registered and the transfer order processing is finalized.

