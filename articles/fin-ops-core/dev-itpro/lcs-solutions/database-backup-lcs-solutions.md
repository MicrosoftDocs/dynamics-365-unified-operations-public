---
title: Back up the databases for finance and operations apps
description: Learn about the database backup that is required for your Microsoft Dynamics Lifecycle Services (LCS) solution package.
author: johnmichalak
ms.author: johnmichalak
ms.topic: article
ms.date: 11/10/2025
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.assetid: fc0f06e8-1a20-45f7-ae98-ee074fe1f030
---

# Back up the databases for finance and operations apps

[!include[banner](../includes/banner.md)]

You need a backup of the finance and operations apps database for your Microsoft Dynamics Lifecycle Services solution package. When you back up the database, include the master, reference, and transactional data that's specific to your solution and industry. Use this data for your presales demo deployments.

On demo or development environments, the database is typically named AXDBRain. Your database backup shouldn't be larger than 15 gigabytes (GB). Otherwise, a time out error might occur when you try to upload the database to the Asset library in Lifecycle Services. 

To compress your database backup, in Microsoft SQL Server Management Studio, on the **Back Up Database** page, in the **Set backup compression** field, select **Compress backup**.

:::image type="content" source="./media/databasebackup01.jpg" alt-text="Screenshot of the Set backup compression field with Compress backup selected.":::

## Additional resources

[Requirements for publishing apps on AppSource](lcs-solutions-app-source.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

