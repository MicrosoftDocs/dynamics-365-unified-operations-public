---
# required metadata

title: View product search publishing status in headquarters
description: This article describes the capability to view product search publishing status in Microsoft Dynamics 365 Commerce headquarters.
author: ashishmsft
ms.date: 06/08/2023
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

Starting in Commerce version 10.0.32, you can view the publishing status for product search in headquarters. With this capability, whenever you publish product information by channel, you're able to see how many products and catalogs were successfully published to the Azure search index, and how many products failed. The total product count is for simple and product masters, and excludes variants.

Product search publishing sessions are queued upon the conclusion of the **1040**, **1070** and **1150** Commerce Data Exchange (CDX) jobs that are scheduled after **Publish channel updates** is executed from **Channel categories and products attributes** form (**Retail and Commerce \> Channel setup \> Channel categories and product attributes**). 

To enable the product search publishing status capability, you must turn on the **Search publishing sessions monitoring** feature in the feature management workspace. Enabling this feature makes discoverable the **Session publishing sessions** form that shows the status of the product/customer Commerce publishing sessions to Azure Search.

Search session publishing statuses are shown in the following table. 

|Publishing status |Description |
--- | --- |
|Queued|Waiting for publisher to start publishing.|
|In-progress|Publishing is in progress.|
|Completed|Publishing was successfully completed.|
|Failed|There was an error in publishing, system will retry automatically.|
|Timed out|Due to some reason, bad query plan or unavailability of required resources or network latency issue it couldn't complete the publishing in appropriate time.|

Along with the publishing status and product count, it also gives you visibility into the timeframe as when was it published successfully and typically how long it has been waiting to be published as well as duration of time required to publish for a particular channel. 

![Search publishing status in headquarters](./media/Search_Publishing_Status_HQ.png)

## Frequently asked questions

### Can system share what products were not published to search index? 

Currently, the system would show the aggregated count of products that are published across all catalogs for a given channel (including default assortment based catalog aka Catalog=0). That means, if it is showing you that 80 products have successfully been published but 20 have not been published. Rightly, you may wonder which 20 did not make it? We want to give you that visibility and we are trying to see what is the most effective manner to provide that view to you. 

#### Can system share why products are failing to get published?

Ideally, we want to show all failure reasons in this view, but there are going to be so many reasons for which the product publishing might be failing and some maybe fixable by updating product configuration and other may require support from Microsoft to address some deeper technical issues. For the issues that maybe fixable by updating product configuration, we recommend you leverage 'Channel merchandising configuration validator' available in headquarters, that would actually help in parallel or complement where it would kind of a showcase to you what product configurations would have been required.

#### Can system show the breakdown of the products published or failed by each catalog? 

Currently, it's limited to show the aggregated product count for a given channel across all catalogs, in future versions we will look for opportunity to provide the published products count by each catalog. 

#### Can system show the breakdown of the products published or failed by each catalog? 

Currently, it's limited to show the aggregated product count for a given channel across all catalogs and all locales, in future versions we will look for opportunity to provide the published products count by each locale. We recommend you leverage 'Channel merchandising configuration validator' for common mistakes that may cause issues with locales specific product publishing where it can identify missing values (Product name, category name, attribute values or product description) for a specific locale. 


