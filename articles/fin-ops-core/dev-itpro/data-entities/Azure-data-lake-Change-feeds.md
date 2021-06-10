---
# required metadata

title: Changed data in Azure Data lake
description: This topic explains change data in the lake and what you can do with it.
author: MilindaV2
ms.date: 06/08/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: NOINDEX, NOFOLLOW
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend

# ms.tgt_pltfrm: 
ms.custom: 96283
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: milindav
ms.search.validFrom: 2020-06-01
ms.dyn365.ops.version: Platform Update 40

---

# Change data in Azure Data Lake

[!include [banner](../includes/banner.md)]

> [!NOTE]
> The **Export to Data Lake** feature is in public preview in the United States, Canada, United Kingdom, Europe, South East Asia, East Asia, Australia, and Japan regions. If your Finance and Operations environment is in any of those regions, you can enable this feature in your environment by using Microsoft Dynamics Lifecycle Services (LCS).
>
> In the coming months, Microsoft will enable this feature in additional regions, based on the demand. If your environment isn't in a region where the preview is enabled, [complete the survey and let us know](https://aka.ms/FnODataLakePreviewSurvey). You can also join a [preview Yammer group](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=32768909312&view=all). You can use the Yammer group to stay in contact and ask questions that will help you understand the feature. 

The **Export to Data Lake** feature lets you copy data from your Finance and Operations apps into your own data lake (Azure Data Lake Storage Gen2). The system lets you select the tables and entities that are included. After you select the data that you want, the system makes an initial copy. The system then keeps the selected data up to date by applying changes, deletions, and additions. After data changes in your Finance and Operations app instances, there might be a delay of a few minutes before the data is available in your data lake.

## Turn on the Export to Data Lake feature
Before you can use this feature, see [Configure export to Azure Data Lake](configure-export-data-lake.md).
