---
title: Commerce data residency
description: Access information about data residency considerations when deploying a cloud Commerce Scale Unit (CSU), including prerequisites.
author: josaw
ms.author: ritakimani
ms.topic: how-to
ms.date: 05/20/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2018-04-30
ms.custom: 
  - bap-template
---

# Commerce data residency

[!include[banner](../includes/banner.md)]


## Choose a region

When you initialize a cloud Commerce Scale Unit (CSU), you need to select a data center location to host. To minimize network latency and improve performance, you should choose a datacenter location that is in proximity to the channels that you plan to serve using the CSU. To reference approximate locations of each datacenter, see [Azure regions](https://azure.microsoft.com/global-infrastructure/regions/). You can also reference a web-based utility, such as [Azure speed reference](https://azurespeedtest.azurewebsites.net/), and measure latency to Azure datacenters from each store location. This information can help you to make the right choice of datacenter when you initialize the CSU.

## Data between regions

If you initialize CSU in a data center that is different than where your head office is located, the data travels between these data centers with periodic synchronization. The system is preconfigured to transfer specific types of data. You can modify this configuration to synchronize different data.

To view the data synchronization configuration, go to **Retail and Commerce** \> **Headquarters setup** \> **Commerce scheduler** \> **Scheduler jobs** to view the data synchronization jobs and subjobs. To view the fields being synchronized, click through a subjob. 

## Synchronize specific segments of records

You can configure Commerce Data Exchange (CDX) so that only specific segments of records are synchronized to specific CSUs. 

### Prerequisites

Before you configure the record segments that will be synchronized, you need to configure channel database groups. These database groups must be configured for each CSU where you want to synchronize segmented data. All CSUs in the same channel database group receive the data that is needed to serve all the channels in that CSU. You need to create a separate database group for each CSU channel database where you plan to synchronize segmented data. 

To configure channel database groups, follow these steps:

1. Go to **Retail and Commerce** \> **Headquarters setup** \> **Commerce scheduler** \> **Channel database group**.
2. Create a new database group for each CSU where you want to synchronize segmented data.
3. Go to **Retail and Commerce** \> **Retail and Commerce IT** \> **Distribution schedule**.
4. Add the newly created channel database group to each scheduler job.
5. Go to **Retail and Commerce** \> **Headquarters setup** \> **Commerce scheduler** \> **Channel database**.
6. Select the channel database for the corresponding Commerce Scale Unit (cloud).
7. Select **Edit** and choose the channel database group that you created in step 2.
8. Select **Save**. 
9. Select **Full data sync for all jobs** for the selected channel database.

### Available controls for synchronizing segments of data to different CSUs

Channel configuration data is only synchronized for channels that are served by specific CSUs. For example, only the channel configuration data for channels that are configured to be served by the West Europe channel are synchronized to that CSU. 

Using assortments, product and pricing related data can be segmented by specific channels. For example, if your stores in North America only sell women's shoes and your stores in West Europe only sell sporting goods, you can use Assortments to segment this data. When data is synchronized to CSU, women's shoes data is only synchronized to the North America CSU, and sporting goods data is only synchronized to the West Europe CSU.

Customer and employee records are configured using the Global Address Book, which can be configured for specific channels. For example, you can configure separate address books for customers and employees for channels served by the West Europe CSU and those served by the North America CSU.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
