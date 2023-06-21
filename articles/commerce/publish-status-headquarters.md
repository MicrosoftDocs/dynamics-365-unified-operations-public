---
# required metadata

title: View product search publishing status in headquarters
description: This article describes the capability to view product search publishing status in Microsoft Dynamics 365 Commerce headquarters.
author: ashishmsft
ms.date: 06/16/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2023-01-30

---

# View product search publishing status in headquarters

[!include[banner](../includes/banner.md)]

This article describes the capability to view product search publishing status in Microsoft Dynamics 365 Commerce headquarters.

As of Commerce version 10.0.32, you can view the publishing status for product search in Commerce headquarters. Therefore, whenever you publish product information by channel, headquarters show how many products and catalogs were successfully published to the Azure Cognitive Search index, and how many failed to be published. The total product count is for simple products and product masters. It excludes variants.

Product search publishing sessions are queued after the **1040**, **1070** and **1150** Commerce Data Exchange (CDX) jobs are completed. These jobs are scheduled after you select **Publish channel updates** on the **Channel categories and products attributes** page (**Retail and Commerce \> Channel setup \> Channel categories and product attributes**).

## Enable the product search publishing status capability

To enable the product search publishing status capability, you must turn on the **Search publishing sessions monitoring** feature in the **Feature management** workspace in headquarters (**Workspaces \> Feature management**). By enabling this feature, you make the **Session publishing sessions** page discoverable. This page shows the status of Commerce publishing sessions to the Azure Cognitive Search index.

## Information on the Search publishing sessions page

The **Search publishing sessions** page in headquarters shows the following information about publishing jobs:

- Session number
- Channel database ID
- Entity type
- Organization number
- Publishing status
- Message
- Queued date and time
- Started date and time
- Completed date and time

The following table describes each session publishing status.

| Publishing status | Description |
|---|---|
| Queued | Publishing is waiting to begin. |
| In progress | Publishing is in progress. |
| Completed | Publishing was successfully completed. |
| Failed | There was an error during publishing. The system will automatically try again to publish. |
| Timed out | For some reason, the system could not complete the publish operation in the normal timeframe. Possible reasons include a bad query plan, unavailability of required resources, and network latency issues. |

In addition to the publishing status and product count, the product search publishing status capability provides visibility into when was a job was successfully published, how long a job waited to be published, and how much time was required to publish a job for a specific channel. 

## Frequently asked questions

#### Can the system show what products weren't successfully published to the Azure Cognitive Search index?

Currently, the system shows the aggregated count of products that are published across all catalogs for a given channel. (These catalogs include the default assortment-based catalog, which is also known as "Catalog=0".) For example, if you publish 100 products, the system might show that 80 products were successfully published, and 20 products weren't successfully published. The Commerce team is working on functionality to give you more visibility into which products weren't successfully published.

#### Can the system show why products failed to be published?

A product might fail to be published for a wide range of reasons. In some cases, there might be deeper technical issues that require support from Microsoft. However, in other cases, you might be able to fix the issues by updating the product configuration. In these cases, Microsoft recommends that you use the channel merchandising configuration validator that's available in headquarters. This tool can help you identify the product configurations issues that must be fixed. For example, publishing issues might be caused by missing values for specific locales. (These values include product names, category names, attribute values, and product descriptions.) The configuration validator can identify these missing values. For more information, see [Channel merchandising configuration validator](channel-merch-config-validator.md).

#### Can the system show a breakdown of the products that were successfully published and failed to be published by catalog?

Currently, the system is limited to showing the aggregated product count for a given channel across all catalogs and all locales. In future versions, the Commerce team hopes to introduce functionality that will provide the count of products that were successfully published and failed to be published by locale and channel.

#### Can the system show a breakdown of the products that were and weren't published by catalog?

Currently, the system is limited to showing the aggregated product count for a given channel across all catalogs. In future versions, the Commerce team hopes to provide a breakdown of published/not published products by catalog.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
