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

Starting in Commerce version 10.0.32, you can view the publishing status for product search in headquarters. With this capability, whenever you publish product information by channel, you're able to see how many products and catalogs were successfully published to the Azure Cognitive Search index, and how many products failed. The total product count is for simple and product masters, and excludes variants.

Product search publishing sessions are queued upon the conclusion of the **1040**, **1070** and **1150** Commerce Data Exchange (CDX) jobs that are scheduled after selecting **Publish channel updates** from the **Channel categories and products attributes** form (**Retail and Commerce \> Channel setup \> Channel categories and product attributes**). 

## Enable the product search publishing status capability

To enable the product search publishing status capability, you must turn on the **Search publishing sessions monitoring** feature in the headquarters feature management workspace (**Workspaces \> Feature management**). Enabling this feature makes the **Session publishing sessions** form discoverable. This form shows the status of Commerce publishing sessions to the Azure Cognitive Search index.

## Information displayed on the Search publishing sessions form

The **Search publishing sessions** form in headquarters displays the following information about publishing jobs:

- **Session number**
- **Channel database ID**
- **Entity type**
- **Organization number**
- **Publish status**
- **Message**
- **Queued date and time**
- **Started date and time**
- **Completed date and time**

Descriptions for each type of search session publishing status are listed in the following table. 

| Publishing status | Description |
| --- | --- |
| Queued | Waiting to start publishing. |
| In progress | Publishing is in progress. |
| Completed | Publishing was successfully completed. |
| Failed | There was an error during publishing, the system will automatically retry to publish. |
| Timed out | Due to some reason (for example, a bad query plan, unavailability of required resources, or network latency issues), the system couldn't complete the publish operation in the normal timeframe. |

Along with the publishing status and product count, the product search publishing status capability also provides visibility into when was a job was successfully published, how long a job was waiting to be published, and the time duration that was needed to publish a job for a particular channel. 

## Frequently asked questions

#### Can the system show what products weren't successfully published to the Azure Cognitive Search search index? 

Currently, the system shows the aggregated count of products that are published across all catalogs for a given channel (including the default assortment-based catalog, also known as "Catalog=0"). For example, if you publish 100 products, the system might show that 80 products were successfully published, and 20 products weren't successfully published. The Commerce team is working on functionality to give you more visibility into which products weren't successfully published. 

#### Can the system show why products failed to get published?

When a product fails to get published, there are a wide range of reasons that may have caused the publishing to fail. Some issues may be resolved by updating product configuration, and other issues may require support from Microsoft to address deeper technical issues. 

For issues that may be fixable by updating the product configuration, Microsoft recommends that you use the channel merchandising configuration validator available in headquarters. This tool can help you identify what product configurations issues need to be resolved. For example, the configuration validator can identify missing values for specific locales (such as product names, category names, attribute values, or product descriptions) that may be causing publishing issues. 

For more information, see [Channel merchandising configuration validator](channel-merch-config-validator.md).

#### Can the system show a breakdown of the products that successfully published and failed to publish by each catalog? 

Currently, the system is limited to showing the aggregated product count for a given channel across all catalogs and all locales. In future versions, the Commerce team hopes to introduce functionality that will provide the successfully published and failed to publish product count by each locale and channel. 

#### Can the system show a breakdown of the products that are published/not published by each catalog? 

Currently, the system is limited to showing the aggregated product count for a given channel across all catalogs. In future versions, the Commerce team hopes to provide a breakdown of published/not published products by each catalog.



[!INCLUDE[footer-include](../includes/footer-banner.md)]
