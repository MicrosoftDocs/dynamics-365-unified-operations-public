---
# required metadata

title: Retail data residency
description: This topic provides information about data residency considerations when deploying the Retail Cloud Scale Unit.
author: AamirAllaq
manager: AnnBe
ms.date: 04/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Retail, Operations 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: retail
ms.author: aamiral
ms.search.validFrom: 2018-4-30 
ms.dyn365.ops.version: 8.0 
---


# Retail data residency

[!include[banner](../includes/banner.md)]


## Choose a region

When you initialize a Retail Cloud Scale Unit (RCSU), you must select a data center location to host. To minimize network latency and improve performance, you might choose a datacenter location that is in close proximity to the retail channels that you plan to serve using the RCSU. To reference approximate locations of each datacenter, see [Azure regions](https://azure.microsoft.com/global-infrastructure/regions/). You may also reference a web based utility, such as the [Azure speed reference](https://azurespeedtest.azurewebsites.net/), and measure latency to Azure datacenters from each store location. This can help you to make the right choice of datacenter when you initialize the RCSU.

## Data between regions

If you initialize RCSU in a different data center than where your head office is located, the data will travel between these data centers with periodic synchronization. The system is pre-configured to transfer specific types of data. You can modify this configuration to synchronize different data.

To view the data synchronization configuration, navigate to **Retail** \> **Headquarters setup** \> **Retail scheduler** \> **Scheduler jobs** to view the data synchrnoization jobs and sub-jobs. To view the fields being synchronized, click through a sub-job. 

## Synchornize specific segments of records

You may choose to configure CDX so that only specific segments of records are synchronized to specific RCSUs. 

### Prerequisities

Before you can configure which record segments will be synchronized, you must first configure Channel database groups. These database groups must be configured for each RCSU where you want to synchronize segmented data. All RCSUs in the same Channel database group recieve the data that is needed to serve all of the channels in that RCSU. You will need to create a separate database group for each RCSU channel database where you plan to syncrhonize segmented data. To do this, perform the following steps:

1. Navigate to **Retail** \> **Headquarters setup** \> **Retail scheduler** \> **Channel database group**.
2. Create a new database group for each RCSU where you want to synchronize segmented data.
3. Navigate to **Retail** \> **Headquarters setup** \> **Retail scheduler** \> **Channel database**.
4. Select the Channel database for the corresponding Retail Cloud Scale Unit.
5. Click **Edit** and choose the channel database group that you created in step 2.
6. Click **Save**. 
7. Click **Full data sync for all jobs** for the selected channel database.

### Available controls for synchronizing segments of data to different RCSUs

Channel configuration data will only be synchronized for channels that are served by specific RCSUs. For example, only the channel configuration data for retail channels that are configured to be served by the West Europe channel will be synchronized to that RCSU. 

Using assortments, product and pricing related data can be segmented by specific channels. For example, if your stores in North America only sell women's shoes and your stores in West Europe only sell sporting goods, you can use Assortments to segment this data. When data is synchronized to RCSU, women's shoes data will only be synchronized to the North America RCSU and sporting goods data will only be synchronized to the West Europe RCSU.

Customer and employee records are configured using the Global Address Book, which can be configured for specific retail channels. For example, you can configure separate address books for customers and employees for channels served by the West Europe RCSU and those for North America RCSU. 
