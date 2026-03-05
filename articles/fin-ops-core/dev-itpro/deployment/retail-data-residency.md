---
title: Commerce data residency
description: Access information about data residency considerations when deploying a cloud Commerce Scale Unit (CSU), including prerequisites.
author: josaw
ms.author: ritakimani
ms.topic: how-to
ms.date: 03/05/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2018-04-30
ms.custom: 
  - bap-template
---

# Commerce data residency

[!include[banner](../includes/banner.md)]

## Choose a region

When you initialize a cloud Commerce Scale Unit (CSU), select a data center location to host it. To minimize network latency and improve performance, choose a datacenter location that's close to the channels you plan to serve by using the CSU. For approximate locations of each datacenter, see [Azure regions](https://azure.microsoft.com/global-infrastructure/regions/). You can also use a web-based utility, such as [Azure speed reference](https://azurespeedtest.azurewebsites.net/), to measure latency to Azure datacenters from each store location. This information can help you choose the right datacenter when you initialize the CSU.

## Data between regions

If you initialize CSU in a data center that's different from where your head office is located, the data travels between these data centers by using periodic synchronization. The system is preconfigured to transfer specific types of data. You can modify this configuration to synchronize different data.

To view the data synchronization configuration, go to **Retail and Commerce** > **Headquarters setup** > **Commerce scheduler** > **Scheduler jobs** to view the data synchronization jobs and subjobs. To view the fields being synchronized, select a subjob.

## Synchronize specific segments of records

You can configure Commerce Data Exchange (CDX) so that only specific segments of records synchronize to specific CSUs.

### Prerequisites

Before you configure the record segments that you want to synchronize, configure channel database groups. Configure these database groups for each CSU where you want to synchronize segmented data. All CSUs in the same channel database group receive the data they need to serve all the channels in that CSU. Create a separate database group for each CSU channel database where you plan to synchronize segmented data.

To configure channel database groups, follow these steps:

1. Go to **Retail and Commerce** > **Headquarters setup** > **Commerce scheduler** > **Channel database group**.
1. Create a new database group for each CSU where you want to synchronize segmented data.
1. Go to **Retail and Commerce** > **Retail and Commerce IT** > **Distribution schedule**.
1. Add the newly created channel database group to each scheduler job.
1. Go to **Retail and Commerce** > **Headquarters setup** > **Commerce scheduler** > **Channel database**.
1. Select the channel database for the corresponding Commerce Scale Unit (cloud).
1. Select **Edit** and choose the channel database group that you created in step 2.
1. Select **Save**.
1. Select **Full data sync for all jobs** for the selected channel database.

### Available controls for synchronizing segments of data to different CSUs

Channel configuration data synchronizes only for channels that specific CSUs serve. For example, the West Europe channel synchronizes only the channel configuration data for channels that it's configured to serve.

By using assortments, you can segment product and pricing related data by specific channels. For example, if your stores in North America only sell women's shoes and your stores in West Europe only sell sporting goods, you can use assortments to segment this data. When data synchronizes to CSU, women's shoes data synchronizes only to the North America CSU, and sporting goods data synchronizes only to the West Europe CSU.

You can configure customer and employee records by using the Global Address Book for specific channels. For example, you can configure separate address books for customers and employees for channels served by the West Europe CSU and those served by the North America CSU.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
