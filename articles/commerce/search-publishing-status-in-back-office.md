---
# required metadata

title: View product search publishing status in headquarters
description: This article describes the capability to view product search publishing status in Microsoft Dynamics 365 Commerce headquarters.
author: ashishmsft
ms.date: 06/07/2023
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

In this article, you can learn how to view the publishing status for product search in the back-office. Starting 10.0.32, you can enable this feature 'Search publishing sessions monitoring' from feature management and this will enable 'Session publishing sessions' form that shows the status of the product/customer Commerce publishing sessions to Azure Search.

With this feature, we are introducing an ability for back-office users to view product search publishing status in back office, that means whenever you are publishing product information by channel, you would be able to see how many products and catalogs were successfully published to Azure search index and how many products failed. Total product count is for simple and product masters, it is excluding variants. 

The product search publishing sessions get queued upon conclusion of the CDX jobs (1040, 1070 and 1150) that are scheduled post trigger of 'Publish channel updates' from 'Channel categories and products attributes' form. And search sessions publishing status will be one of the following - 

|Publishing status |Description |
--- | --- |
|Queued|Waiting for publisher to start publishing|
|In-progress|Publishing is in-progress|
|Completed|Publishing was successfully completed|
|Failed|There was an error in publishing, system will re-try automatically|
|Timed out|Due to some reason, bad query plan or unavailability of required resources or network latency issue it couldn't complete the publishing in appropriate time|

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


