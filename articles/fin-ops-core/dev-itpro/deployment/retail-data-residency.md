---
# required metadata

title: Commerce data residency
description: This topic provides information about data residency considerations when deploying the Commerce Scale Unit (cloud).
author: AamirAllaq
ms.date: 10/06/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: retail
ms.author: aamiral
ms.search.validFrom: 2018-4-30 
ms.dyn365.ops.version: 8.0 
---


# Commerce data residency

[!include[banner](../includes/banner.md)]


## Choose a region

When you initialize a Commerce Scale Unit (cloud), you need to select a data center location to host. To minimize network latency and improve performance, you should choose a datacenter location that is in proximity to the channels that you plan to serve using the RCSU. To reference approximate locations of each datacenter, see [Azure regions](https://azure.microsoft.com/global-infrastructure/regions/). You can also reference a web-based utility, such as [Azure speed reference](https://azurespeedtest.azurewebsites.net/), and measure latency to Azure datacenters from each store location. This can help you to make the right choice of datacenter when you initialize the RCSU.

## Data between regions

If you initialize RCSU in a data center that is different than where your head office is located, the data will travel between these data centers with periodic synchronization. The system is pre-configured to transfer specific types of data. You can modify this configuration to synchronize different data.

To view the data synchronization configuration, go to **Retail and Commerce** \> **Headquarters setup** \> **Commerce scheduler** \> **Scheduler jobs** to view the data synchronization jobs and sub-jobs. To view the fields being synchronized, click through a sub-job. 

## Synchronize specific segments of records

You can configure Commerce Data Exchange (CDX) so that only specific segments of records are synchronized to specific RCSUs. 

### Prerequisites

Before you configure the record segments that will be synchronized, you need to configure Channel database groups. These database groups must be configured for each CSU where you want to synchronize segmented data. All CSUs in the same Channel database group receive the data that is needed to serve all the channels in that CSU. You will need to create a separate database group for each CSU channel database where you plan to synchronize segmented data. To do this, perform the following steps:

1. Go to **Retail and Commerce** \> **Headquarters setup** \> **Commerce scheduler** \> **Channel database group**.
2. Create a new database group for each CSU where you want to synchronize segmented data.
3. Go to **Retail and Commerce** \> **Retail and Commerce IT** \> **Distribution schedule**.
4. Add the newly created Channel database group to each scheduler job.
5. Go to **Retail and Commerce** \> **Headquarters setup** \> **Commerce scheduler** \> **Channel database**.
6. Select the Channel database for the corresponding Commerce Scale Unit (cloud).
7. Select **Edit** and choose the channel database group that you created in step 2.
8. Select **Save**. 
9. Select **Full data sync for all jobs** for the selected channel database.

### Available controls for synchronizing segments of data to different RCSUs

Channel configuration data will only be synchronized for channels that are served by specific RCSUs. For example, only the channel configuration data for channels that are configured to be served by the West Europe channel will be synchronized to that RCSU. 

Using assortments, product and pricing related data can be segmented by specific channels. For example, if your stores in North America only sell women's shoes and your stores in West Europe only sell sporting goods, you can use Assortments to segment this data. When data is synchronized to RCSU, women's shoes data will only be synchronized to the North America RCSU and sporting goods data will only be synchronized to the West Europe RCSU.

Customer and employee records are configured using the Global Address Book, which can be configured for specific channels. For example, you can configure separate address books for customers and employees for channels served by the West Europe RCSU and those for North America RCSU.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]