---
# required metadata

title: Inventory Visibility Add-in overview
description: This topic describes what is Inventory Visibility and the features in Inventory Visibility.
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

The Inventory Visibility Add-in (also referred to as *Inventory Visibility*) is an independent and highly scalable microservice that enables real-time on-hand inventory tracking, thus providing a global view of inventory.

External systems access the service through RESTful APIs to either query on-hand information on given sets of dimensions or make changes to your inventory in different customized data sources.

As a microservice built on Microsoft Dataverse, it provides extensibility of building Power Apps and applying Power BI to provide customized functionality to meet your business requirements.

You can integrate Inventory Visibility with multiple third-party systems by setting configuration options for standardized inventory dimensions, and transaction types. It also supports customized extensibility with configurable calculated quantities.

## Supported features

### Inventory Visibility integration with Dynamics 365 Supply Chain Management

The integrated solution pulls inventory data from Dynamics 365 Supply Chain Management and continuously track inventory changes. For details, see [Inventory Visibility setup](inventory-visibility-setup.md).

### Get a global view of inventory

The integrated solution lets you define your own data sources and centralize the inventory data. For details, see [Inventory Visibility configuration](inventory-visibility-configuration.md).

There are two approaches to viewing your inventory:

- Submit a query through the high-performance API, which can return near real-time inventory data directly from a cached instance. You can find contracts and samples in [Inventory Visibility public APIs](inventory-visibility-api.md).
- View the raw on-hand list, which syncs from a cached instance periodically and is visible in Dataverse. For details, see [Inventory Visibility Power Apps](inventory-visibility-power-platform.md).

### Soft reservations

Soft reservation applies when a business needs to reserve certain quantity of products to support, for example, a sales order fulfillment to avoid over selling. When a sales order is created and confirmed in Supply Chain Management or other order-management systems, a request to reserve the quantity is sent to Inventory Visibility. Inventory Visibility allows you to reserve products with dimension details and specific inventory transaction types (see also [Inventory Visibility Power Apps](inventory-visibility-power-platform.md). Once the quantity is successfully reserved, a reservation ID is returned to let you link back to original order in Supply Chain Management or other order-management systems. The function is designed in such way that a reservation in Inventory Visibility won't change the total quantity, but instead only flags the reserved quantity, which is why it's called a *soft reservation*. The soft-reserved quantity can be offset when the products are consumed in Supply Chain Management or a third-party system by calling the API back to make a quantity deduction and update the total quantity in Inventory Visibility. For more information, see [Inventory Visibility Reservations](inventory-visibility-reservations.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
