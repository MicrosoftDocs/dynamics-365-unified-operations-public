---
# required metadata

title: Project resource scheduling performance
description: This topic provides information about how to improve the performance of resource scheduling for a large number of projects.
author: Yowelle
manager: AnnBe
ms.date: 08/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Service industries
ms.author: roschlom
ms.dyn365.ops.version: 10.0.14
ms.search.validFrom: 2020-09-01
---
# Project resource scheduling performance

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]


Performance issues related to resource scheduling can occur when the number of projects reaches into the thousands. To improve resource scheduling performance, a feature is available that allows users to reduce the time that it takes to launch the resource availability form. Specifically, this removes the resource capacity roll-up synchronization process and uses the **ResProjectResource** table to speed up the resource lookup. Note that the **ResRollup** table will no longer be used.

> [!IMPORTANT]
> If there is a dependency on either the resource capacity roll-up synchronization process or the **ResProjectResource** table, do not use this feature.

## Enable resource scheduling performance enhancement
To enable resource scheduling performance enhancement, complete the following steps.

1. Go to **Feature management** > **All**, and in the feature list, locate **Enable project resource scheduling performance enhancement feature**.
2. Select **Enable now**.

> [!NOTE]
> If you can't find the feature in the list, select **Check for updates** to refresh the list.

3. Refresh your browser, and then go to **Project management and accounting** > **Periodic** > **Project resources** > **Synchronize resource calendars capacity across all companies**.
4. Set **Remove existing capacity records** to **Yes** to remove previous data. If you want generate incremental data, set it to **No**.
5. In the **Period code** field, select the period in which data should be generated. If you select a period code, a start and end date do not need to be defined.
6. If you leave the **Period code** field blank, select specific start and end dates to generate data.
7. Select **OK**.

 > [!NOTE]
 > This will distribute general data to the **ResCalendarCapacity** table across all companies in your environment, so the batch job only needs to be run in one legal entity. The data in this batch job is needed to calculate resource capacity through the associated calendar.

8. Go to **Project management and accounting** > **Periodic** > **Project resources** > **Populate project resources across all companies** and then select **OK**. This is the data upgrade script for general data in the **ResProjectResource**, **ResCalendarDateTimeRange**, and **ResEffectiveDateTimeRange** tables. Values for the **PSAPRojSchedRole.RootActivity** field are also updated. If this is not run, you will receive a warning when you try to execute resource scheduling operations.
 
## Turn off resource scheduling performance enhancement

1. Go to **Feature management** > **All**  and search for **Enable project resource scheduling performance enhancement feature**.
2. Select the feature, and then select the **Disable** button.
3. Refresh your browser.
4. Go to **Project management and accounting** > **Periodic** > **Capacity synchronization** > **Synchronize resource capacity roll-ups**.
5. On the **Capacity roll-up synchronization** page, set **Remove existing capacity records** to **Yes** to remove previous data. If you want to generate incremental data, set it to **No**.
6. In the **Period code** field, select the period in which data should be generated. If you select a period code, a start and end date do not need to be defined.
7. If you leave the **Period code** field blank, select specific start and end dates to generate data.
8. Select **OK**.

> [!NOTE]
> This will distribute general data to the **ResRollup** table across all companies in your environment, so the batch job only needs to be run in one legal entity. This batch job is needed for all **Resource Availability** views. If this batch job is not run, the **ResRollup** data will be generated on the fly, which can take time.
