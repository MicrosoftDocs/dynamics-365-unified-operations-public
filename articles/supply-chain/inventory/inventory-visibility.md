---
title: Inventory Visibility Add-in overview
description: This topic explains what Inventory Visibility is and describes its features.
author: yufeihuang
ms.date: 03/18/2022
ms.topic: overview
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yufeihuang
ms.search.validFrom: 2020-10-26
ms.dyn365.ops.version: 10.0.15
---

# Inventory Visibility Add-in overview

[!include [banner](../includes/banner.md)]

The Inventory Visibility Add-in (also referred to as the *Inventory Visibility service*) provides an independent and highly scalable microservice that enables real-time on-hand inventory change postings and visibility tracking across all your data sources and channels. It provides a platform that lets you manage your global inventory by using functionality that includes (but isn't limited to) the following list:

- Centrally track the latest inventory status (such as on-hand, ordered, purchased, in-transit, returned, and quarantined) across all your data sources, warehouses, and locations by connecting your Supply Chain Management or third-party logistics data sources (such as order management systems, third-party enterprise resource planning \[ERP\] systems, point of sale \[POS\] systems, and warehouse management systems) to the Inventory Visibility service.
- Query on-hand stock availability and shortages, and obtain immediate responses by calling the Inventory Visibility service directly.
- Avoid overselling, especially when your demand comes from different channels, by making real-time soft reservations in the Inventory Visibility service.
- Better manage promised orders and customer expectations by providing accurate current or next-available dates, so that the omnichannel available-to-promise (ATP) feature can calculate expected order fulfillment dates.

## Extensibility

The Inventory Visibility service is highly extensible because data input and output aren't restricted to Microsoft applications. External systems can access the service through RESTful application programming interfaces (APIs). In addition to using the out-of-box mappings that are provided for the Supply Chain Management data source and dimensions, you can integrate Inventory Visibility with multiple third-party systems by setting up additional data sources, inventory statuses measures (referred to as *physical measures* in Inventory Visibility service), and inventory dimensions via the configuration app. In this way, you can flexibly query and change your multiple data sources and predefined inventory dimensions.

Additionally, because Inventory Visibility is built on Microsoft Dataverse, its data can be used to build and integrate with Power Apps. You can also use Power BI to create customized dashboards that meet your business requirements.

## Scalability

The Inventory Visibility service can be scaled up or down, depending on your data volume. The scalability experience is mostly seamless and is conducted by the Microsoft platform team, based on automatic detection and assessment of your transaction data volume.

## Feature highlights

### Get a global view of real-time inventory

Inventory Visibility ensures that you have access to the most up-to-date inventory quantities at all times, across all your channels, locations, and warehouses. You will benefit most from using it to support your daily operational business whenever you must obtain inventory records. Physical on-hand inventory, quantities sold, and quantities purchased are all available out of the box. You can also configure other physical inventory measures (such as returned, quarantined, and posted data) as you require, to obtain those details in real time. Inventory Visibility can efficiently process millions of inventory change posts. This data can be aggregated and reflected in the latest inventory quantities in the service immediately, per second, or per minute, depending on the interval that data is posted at. For more information, see [Inventory Visibility public APIs](inventory-visibility-api.md).

### Soft reservation to avoid overselling across all order channels

A *soft reservation* lets you assign or flag specific quantities to fulfill an order or demand. A soft reservation doesn't affect physical inventory, but it does deduct from the *available for reservation* inventory quantity and provides an updated quantity for future order fulfillment. This feature will be useful if sales requests or orders come into your business from one or more channels or data sources that are outside your system-of-record enterprise resource planning (ERP) system.

If you don't use soft reservations in the Inventory Visibility service, you must wait until the order is synced to and processed by your ERP system to get a physical inventory quantity update. This process typically has huge latency. However, soft reservations take immediate effect each time that a sales request or order is generated in your sales channels. Therefore, they help prevent oversell situations by ensuring that your omnichannel orders won't interfere with each other when they eventually reach the ERP system. Soft reservations also ensure that you can fulfill all the orders that you've promised. Therefore, they help you meet customer expectations and maintain customer loyalty. For more information, see [Inventory Visibility reservations](inventory-visibility-reservations.md).

### Immediate response of ATP dates confirmation

Visibility into your near-future projected inventory (including supply, demand, and projected on-hand details) is important, because it helps your company achieve the following goals:

- Minimize inventory levels to reduce inventory management costs.
- Facilitate internal order processing, so that salespeople can calculate shipment and delivery dates, based on the availability of the products that are ordered.
- Provide transparency about when customers can expect an out-of-stock item to become available, by providing the next-available date.

The ATP feature is easy to adopt into your daily order fulfillment process. Most importantly, like other Inventory Visibility offerings, the ATP feature is *global and real-time*. Therefore, you can set up multiple ATP calculation formulas to have full inventory availability queries that cover all your business channels and data sources. For more information, see [Inventory Visibility on-hand change schedules and available to promise](inventory-visibility-available-to-promise.md).

### Compatibility with advanced warehouse management items

Microsoft aims to provide out-of-box integration with advanced warehouse management (WHS), so that WHS customers can also enjoy the benefits of the Inventory Visibility service. Per the 2022 Wave 1 release (public preview in March), inventory service supports WHS item on-hand queries and ATP. The soft reservation and allocation feature will be supported for WHS customers in next wave. For more information, see [Inventory Visibility support for WHS items](inventory-visibility-whs-support.md).

## Licensing

The Inventory Visibility service is available in the following versions:

- **Inventory Visibility Add-in for Microsoft Dynamics 365 Supply Chain Management** – For companies that have a valid Supply Chain Management license, Inventory Visibility is available at no extra license cost. You can start to try it out today. For installation details, see [Install and set up Inventory Visibility](inventory-visibility-setup.md).
- **Inventory Visibility Service as a component of IOM** – This version is for either Intelligent Order Management (IOM) customers or companies that aren't using Supply Chain Management as their ERP system. The license is included in the IOM bundle. For more information, see [Intelligent Order Management overview](/dynamics365/intelligent-order-management/overview).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
