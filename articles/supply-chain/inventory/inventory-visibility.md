---
# required metadata

title: Inventory Visibility Add-in Overview
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

# Inventory Visibility Add-in

The Inventory Visibility Add-in (also refer to Inventory Visibility) is an independent and highly scalable microservice that enables real-time on-hand inventory tracking, thus providing a global view of inventory visibility.

External systems access the service through RESTful APIs to either query on-hand information on given sets of dimensions or make changes to your inventory in different customized data sources.

As a microservice built on Microsoft Dataverse, it provides extensibility of building Power Apps and applying Power BI to provide customized functionality to meet your business requirements.

Inventory Visibility is flexible to integrate with multiple third-party systems by providing different configuraiton options of standardized inventory dimensions, transaction types, as well as customized extensibility with configurable calculated quantities.

## Supported features

### Inventory Visibility Integration in Dynamics 365 Supply Chain Management

This integration pull inventory data from Dynamics 365 SCM and continously track inventory changes. See [how to setup inventory visibility integration in D365 SCM](./inventory-visibility-setup.md).

### Get global view of Inventory Visibility

You are able to define your own data sources and centralize the inventory data to microservice by calling APIs. See [how to configure your data sources and calculated measures](./inventory-visibility-configuration.md).

There are two approaches to get your inventory visibility

- Inventory Query powered by high-performance API can return near real-time inventory data directly from cache instance. Find contracts and samples from [page of APIs](./inventory-visibility-api.md).
- Full raw on-hand list that syncs from cache instance periodically is visible in Dataverse. See [how to enable feature of loading on-hand list to Dataverse](./inventory-visibility-power-platform.md#feature-switch).

### Soft Reservation

Soft reservation applies when a business needs to reserve certain quantity of products to support for example a sales order fulfillment to avoid oversale. When a sales order is created and confirmed in D365 SCM or other order management systems, a request of quantity reservation is sent to Inventory visibility. Inventory Visibility service allows you to reserve products with dimension details and specific inventory transaction type. See [how to define your reservation check rule](./inventory-visibility-power-platform.md#setup-reservation-mapping). Once the quantity is successfully reserved, a reservation ID is returned to let you link back to original order in D365 SCM or other order management systems. The function is designed in such way that a reservation in inventory visibility will not change the total quantity but only flagging up the reserved quantity, hence being called ‘soft reservation’. The softly-reserved quantity can be off-set when the products are consumed in D365 SCM or 3rd-party systems by calling API back to make a quantity deduction and update the total quantity in Inventory Visibility. Please refer to more details [here](./inventory-visibility-reservations.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
