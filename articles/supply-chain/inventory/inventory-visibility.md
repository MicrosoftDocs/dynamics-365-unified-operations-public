---
# required metadata

title: Inventory Visibility Add-in overview
description: This topic explains what Inventory Visibility is and describes its features.
author: sherry-zheng
ms.date: 10/26/2020
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: chuzheng
ms.search.validFrom: 2020-10-26
ms.dyn365.ops.version: Release 10.0.15
---

# Inventory Visibility Add-in overview

[!include [banner](../includes/banner.md)]

The Inventory Visibility Add-in (also referred to as *Inventory Visibility*) is an independent and highly scalable microservice that enables real-time on-hand inventory tracking. Therefore, it provides a global view of inventory.

External systems access the service through RESTful APIs. In that way, they can either query on-hand information on given sets of dimensions or make changes to your inventory in different customized data sources.

As a microservice that is built on Microsoft Dataverse, Inventory Visibility provides extensibility. You can use Power Apps to build apps. You can also apply Power BI to provide customized functionality that meets your business requirements.

You can integrate Inventory Visibility with multiple third-party systems by setting configuration options for standardized inventory dimensions and setting up transaction types. Inventory Visibility also supports customized extensibility through configurable calculated quantities.

## Inventory Visibility integration with Dynamics 365 Supply Chain Management

The integrated solution pulls inventory data from Dynamics 365 Supply Chain Management and continuously tracks inventory changes. For more information, see [Install and set up Inventory Visibility](inventory-visibility-setup.md) and [Configure Inventory Visibility](inventory-visibility-configuration.md).

## Get a global view of inventory

The integrated solution lets you define your own data sources and centralize inventory data. For more information, see [Configure Inventory Visibility](inventory-visibility-configuration.md).

There are two approaches to viewing your inventory:

- Submit a query through the high-performance API. This API can return near-real-time inventory data directly from a cached instance. You can find contracts and samples in [Inventory Visibility public APIs](inventory-visibility-api.md).
- View the raw on-hand list. This list is periodically synced from a cached instance and is visible in Dataverse. For more information, see [Inventory Visibility app](inventory-visibility-power-platform.md).

## Soft reservations

[!INCLUDE [preview-banner-section](../../includes/preview-banner-section.md)]

Soft reservation applies when a business must reserve a specific quantity of products to support, for example, sales order fulfillment that avoids over-selling. When a sales order is created and confirmed in Supply Chain Management or other order management systems, a request to reserve the quantity is sent to Inventory Visibility. Inventory Visibility lets you reserve products that have dimension details and specific inventory transaction types. (For more information, see [Inventory Visibility app](inventory-visibility-power-platform.md).) After the quantity is successfully reserved, a reservation ID is returned. You can use this reservation ID to link back to the original order in Supply Chain Management or other order management systems.

The functionality is designed so that a reservation in Inventory Visibility doesn't change the total quantity. Instead, it only flags the reserved quantity. (For this reason, it's called a *soft reservation*.) The soft-reserved quantity can be offset when the products are consumed in Supply Chain Management or a third-party system by calling the API again to make a quantity deduction and update the total quantity in Inventory Visibility. For more information, see [Inventory Visibility reservations](inventory-visibility-reservations.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
