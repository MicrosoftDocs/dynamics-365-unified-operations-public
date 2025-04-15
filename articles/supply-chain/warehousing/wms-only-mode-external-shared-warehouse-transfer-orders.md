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

This article explains how to set up Microsoft Dynamics 365 Supply Chain Management to handle transfer orders with external shared warehouses. Most aspects of the transfer order processing work in the same way, regardless of whether you use exteranl shared warehouses. This article highlights the differences.

Tranfer orders with external shared warehousing means that either source, destination or both warehouses in a transfer orders are external. Learn more about the external shared warehouses [Warehouse management only mode with external shared warehouses](wms-only-mode-external-shared-warehouse.md).

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.44 or later.
- Setup external shared warehouses as described in [Warehouse management only mode with external shared warehouses](wms-only-mode-external-shared-warehouse.md).
- In the warehouse configuration of the externally managed warehouse, apart from a *default location*, you also need to setup a *default license plate location*. This location will be used as a temporary location when processing a transfer order. When shipping from an external warehouse, an update about what has been shipped from it is received and it contains a license plate

## Ship from external warehouse


