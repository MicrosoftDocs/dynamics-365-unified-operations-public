---
# required metadata

title: Inventory Visibility Add-in overview
description: This topic explains what Inventory Visibility is and describes its features.
author: yufeihuang
ms.date: 10/26/2020
ms.topic: overview
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
ms.author: yufeihuang
ms.search.validFrom: 2020-10-26
ms.dyn365.ops.version: 10.0.15
---

# Inventory Visibility Add-in overview

[!include [banner](../includes/banner.md)]

The Inventory Visibility Add-in (also referred to as *Inventory Visibility service* <!-- KFM: Why have two names? Are these always exactly the same thing? If they are not the same thing, which one are we describing in this topic? Yufei: because it is a microservice therefore sometimes being called as inventory visibility service-->) provides an independent and highly scalable microservice that enables real-time on-hand inventory change postings and visibility tracking across all your data sources and channels. It provides a platform <!-- KFM: Word missing? maybe "management" or "monitoring" or something else? Yufei: updated--> that lets you manage your global inventory using functionalities including (but not restricted to):

- Track centrally the latest inventory status (such as on-hand, ordered, purchased, in-transit, returned, quarantined, and so on) across all of your data sources, warehouses and locations by connecting your Supply Chain Management or 3rd party logistics data sources (order management systems, 3rd-party ERPs, Point of sales systems, warehouse management systems, and so on) <!-- KFM: Spell out all of these acronyms (OMS, 3PL ERPs, POS, WMS ). Why is 3PL listed twice? Yufei:updated--> to Inventory Visibility service <!-- KFM: Why plural? Yufei: Sorry typo-->.
- Query on-hand stock availability and shortages and obtain immediate responses by calling the Inventory Visibility service directly.
- Avoid overselling, especially when your demand comes from different channels, by making real-time soft reservations in the Inventory Visibility service.
- Better manage promised orders and customer expectations by providing accurate current or next-available dates, which enable the omnichannel available-to-promise feature to calculate expected order fulfillment dates.

## Extensibility

The Inventory Visibility service is highly extensible because data input and output are not restricted to Microsoft applications. External systems can access the service through RESTful APIs. In addition to the out-of-box mappings provided for the Supply Chain Management data source and dimensions, you can integrate Inventory Visibility with multiple third-party systems by setting up additional data source, inventory statuses measures (called physical measures in Inventory Visibility service) and inventory dimensions via the configuration app. In that way, you can query and make changes to your multiple data sources and pre-defined inventory dimensions flexibly.

Additionally, because Inventory Visibility is built on Microsoft Dataverse, its data can be leveraged to build and integrate with Power Apps. You can also use Power BI to create customized dashboards that meet your business requirements.

## Scalability

Inventory Visibility service <!-- KFM: Is the Inventory Visibility service really best described as an "inventory data performance engine" ? Yufei: deleted the description--> can be scaled up or down depending on your data volume. The scalability experience is mostly seamless <!-- KFM: Is "seamless" really the right word here? Do we mean it's automatic, without requiring anything from the customer? added 'mostly'. The scalability is normally done automatically by the platform team but if there's performance issue or require additional liscence customer will contact us and platform team--> and is conducted by Microsoft platform team based on automatic detection and assessment of your transaction data volume. <!-- KFM: Link needed Yufei: deleted the additional link as we are still trying to obtain the information-->.

## Feature Highlights

### Get a global view of real-time inventory

Inventory Visibility ensures that you have access to the most up-to-date inventory quantities at all times across all your channels, locations, and warehouses. You will benefit most by using it to support your daily operational business whenever you need to obtain inventory records. The physical on-hand inventory, quantities sold, and quantities purchased are all available with the out-of-box offering. You can configure other physical inventory measures (such as returned, quarantined, and posted data <!-- KFM: is "posted date" correct here? -->) as needed to obtain those details in real-time. Inventory Visibility is capable of efficiently processing millions of inventory change posts,  and this data can be aggregated and reflected in the latest inventory quantities in the service immediately, within a second or per minute depends on the the interval you post data <!-- KFM: I don't understand the last phrase Yufei: added word'interval'-->. you can find a list if APIs available for data posting here [Inventory Visibility public APIs](https://docs.microsoft.com/en-us/dynamics365/supply-chain/inventory/inventory-visibility-api) <!-- KFM: Link needed -->.

### Soft reservation to avoid oversell across all order channels

<!-- KFM: I think it would help to define what a soft reservation is here. Yufei: updated -->

A soft reservation is to assign/flag certain quantities for the purpose to support an order/demand fulfillment. It does not affect physical inventory and would deduct from the 'Available for Reservation' inventory quantity and provide you an updated quantity for future order fulfillment reference. This function will be useful if your business has sales requests or orders coming in from one or multiple channels or data sources that are outside of your system of record enterprise resource planning (ERP) system.

Instead of waiting until the order gets synced to and processed by your ERP system for a physical inventory quantity update (which normally has huge latency), you can use soft reservations in Inventory Visibility service, which takes affect right away each time a sales request or order is generated in your sales channels. This helps to prevent oversell situations by ensuring your omnichannel orders will not step on each other's toes later when they eventually reach the ERP system. It ensures that you can fulfill all of the orders that you have promised, helping you to meet customer expectations and and maintain customer loyalty. For more information, see [inventory visibility reservations](https://docs.microsoft.com/en-us/dynamics365/supply-chain/inventory/inventory-visibility-reservations) <!-- KFM: Link needed Yufei:done-->.

### Immediate response of available to promise dates confirmation

Having visibility into your near-future projected inventory (including supply, demand, and projected on-hand details) is important because this helps your company to:

- Minimize inventory levels to reduce inventory management costs.
- Facilitate internal order processing so sales people can calculate shipment and delivery dates based on the availability of the ordered products.
- Provide transparency on when customers can expect an out-of-stock item to become available by providing the next-available date.

The available-to-promise (ATP) feature is easy to adopt into your daily order fulfillment process. Most importantly, just like other Inventory Visibility offering, the ATP feature is *global and real-time*, so you can set up *multiple ATP calculation formulas* to have full inventory availability queries that cover all of your business channels and data sources. For more information, see [XXXX](#X) <!-- KFM: Link needed Yufei: Hi Karl do you now have the published link of ATP feature? if so can you help to add here? many thanks-->.

### Compatibility with advanced warehouse management items

We aim to provide out of box integration with advanced warehouse management (WHS) so that WHS customers can also enjoy the benefit of Inventory Visibility service. Per 2022 Wave 1 release (public preview in March) inventory service supports WHS item on-hand query and ATP. The soft reservation and allocation feature will be supported for WHS customers in next wave. For more information, see [XXXX](#X) <!-- KFM: Link needed Yufei: same as ATP, public link not available yet, dependent on the individual link page-->.

## Licensing

The Inventory Visibility service is available in the following versions:

- **Inventory Visibility Add-in for Microsoft Dynamics 365 Supply Chain Management** – This version is for companies holding a valid Supply Chain Management license, Inventory Visibility is available at no extra license cost. You can start trying out from today. For installation details, see [Install and set up inventory visibility](https://docs.microsoft.com/en-us/dynamics365/supply-chain/inventory/inventory-visibility-setup) <!-- KFM: Link needed yufei: done-->.
- **Inventory Visibility Service as a component of IOM** <!-- KFM: Is this the official name of this product? -->. – This version is for either IOM <!-- KFM: Spell out "IOM" --> customers or companies who aren't using Supply Chain Management as their ERP system. The license is included in the IOM bundle. For more information, see [Intelligent Order Management Overview](https://docs.microsoft.com/en-us/dynamics365/intelligent-order-management/overview) <!-- KFM: Link needed yufei: done-->.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
