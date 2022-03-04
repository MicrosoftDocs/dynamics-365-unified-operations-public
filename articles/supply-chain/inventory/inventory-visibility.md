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

# Inventory Visibility Service Overview
  
The Inventory Visibility Add-in (also referred to as Inventory Visibility Service) is an independent and highly scalable microservice that enables real-time on-hand inventory change posting and visibility tracking across all your data sources and channels. It provides you a platform of global inventory that empowers you to have a smart control of your global inventory such as but not restricted to:
- Track centrally the latest inventory status such as onhand, ordered, purchased, in-transit, returned, quarantined, etc. across all of your datasources, warehouse and locations by connecting your D365 SCM or 3PL data sources (OMS, 3PL ERPs, POS, WMS, etc.) to inventory visibility services
- Check onhand stock availability/shortage and obtain immediate response by calling inventory visibility service directly
- Avoid oversell especially when your demand comes from different channels by real-time Soft-reserve in inventory visibility service
- Better manage order-promising and customer expectation by providing accurate current or next available date based on which you can calculate the expected order fulfillment date with the omnichannel Available-to-Promise feature
## Extensibility
  Inventory Visibility Service is highly extensible as the data input and output are not restricted to Microsoft applications. External systems can access the service through RESTful APIs. In addition to current out-of-box mappings with D365 supply chain management datasource and dimensions, you can integrate Inventory Visibility with multiple third-party systems by setting up additional datasource, inventory statuses measures (called physical measures in inventory visibility service) and inventory dimensions via the configuration app. In that way, you can query and make changes to your multiple datasources and pre-defined inventory dimensions flexibly.

  Additionally, as a microservice that is built on Microsoft Dataverse, Inventory Visibility service data can be leveraged to integrate and build power apps. You can also apply Power BI to provide customized dashboards that meet your business requirements.
## Scalability
As an inventory data performance engine, inventory visibility service can be scaled up or down depending on your organization’s data volume. The scalability experience is seamless and is conducted by Microsoft platform team based on automatic detection and assessment of your transaction data volume. For details about platfrom scalbility please refer to xxxx.
## Feature Highlights
### Get a global view of real-time inventory
Inventory visibility ensures you to have the most up-to-date inventory quantities  at any time across all your channels, locations, and warehouse. You will benefit most from it by using it to support your daily operational business whenever needing to obtain inventory records. The physical onhand inventory, quantities sold, purchased, are all available with out of box offerrings. You can also configure other inventory physical measures such as returned, quarantined and post data accordingly to obtain those level of details in real-time. Inventory Visibility service is capable of processing millions of inventory change posts efficiently and can be aggregated and reflected to the latest inventory quantitiess in the service immediately, per minute or other length depends on the way you post data. For configuration details please go to xxxx

### Soft reservation to avoid oversell across all order channels
Inventory Visibilitys soft reservation best fits when your business have sales requests or orders coming in from one or multiple channels/datasources that are outside of your system of record ERP system. Instead of awaiting until the order gets synced and processed in ERP to trigger the inventory change update in your ERP, you can optimize and soft reserve in Inventory Visibility service the moment when sales requests/orders are generated in your sales channels. Thus avoiding oversell situation that your omnichannle orders will not step on each others' toes when they all reach to ERP later. Thus ensuring you can fulfill the orders that you promised to the customer, helping you to meet customer expectation and to maintain customer loyalty. For more information please go to xxxxx
### Immediate response of Available to Promise dates confirmation
Having visibility into your near future's projected inventory with supply,demand and projected onhand details are important as this helps your company to 
- minimise inventory levels to reduce inventory management costs and 
- facilitate internal order processing for sales people to calculate order shipment and delivery date with the based on the available dates of the ordered products. 
- provide customers transparency on when they should expect an out-of-stock item to be available with next available date
 
The Available-to-Promise (ATP) feature is easy to adopt into your daily order fulfillment process. Most importantly, just like other offerings by Inventory Visibilty service, the ATP feature here is also **global and real-time**, you can set up **multiple ATP calculation formulas** to have a full inventory availability queries covering all of your business channels and datasources. For more information please go to xxxx
### Compatiability with D365 Advanced Warehouse Management items
We aim to provide out of box integration with D365 Advanced Warehouse Management so that WHS customers can also enjoy the benefit of inventory visibility service. Per 2022 Wave 1 release (public preview in March) inventory service supports WHS item onhand query and ATP. The soft reservation and allocation feature will be supported for WHS customers in next wave. For details please refer to xxxx
## Liscensing
Currently we offer two forms of Inventory Visibility Service products.
- **Inventory Visibility Service add-in** for D365 supply chain management. For customers holding valid D365 SCM liscence there is no extra liscence cost for the Inventory Visibility add-in service. You can really start trying out from today. Please refer to xxxx for installation details
- **Inventory Visibility Service as a component of IOM** for either IOM customers or customers who do not have D365 SCM as ERP. The liscence is included in IOM bundle. For more information please go to xxxx


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
