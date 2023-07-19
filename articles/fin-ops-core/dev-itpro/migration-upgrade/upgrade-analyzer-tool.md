---
title: Upgrade from AX 2012 - Plan by using the Upgrade analysis report
description: This article explains how to use the Upgrade analysis report to plan your upgrade from Dynamics AX 2012.
author: ttreen
ms.date: 07/18/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 2023-07-18
ms.dyn365.ops.version: Platform update 54
ms.custom: 106163
ms.assetid: 
---

# Upgrade from AX 2012 - Plan by using the Upgrade analysis report

[!include [banner](../includes/banner.md)]

[!include [upgrade banner](../includes/upgrade-banner.md)]

This article explains how to use the Upgrade analysis report to plan your upgrade from Microsoft Dynamics AX 2012. The report script is run against an AX 2012 database and parses tables for application setup and data volumes. It provides feedback on deprecated features, application settings, database settings and table space savings. 

Space saving observations provide clean up routines in AX 2012 to help reduce the subscription cost for finance and operations apps. SQL configuration optimizations suggestions can help speed up the upgrade processes. Additionally, the tool warns if any AX 2012 features are obsolete in the current version. You can plan ways to replace or work around those features.

## Download

Download the Upgrade analysis report script (UpgradeAnalysisReport.SQL) from here: [Upgrade Analysis Report](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/blob/master/AX2012DataUpgrade/UpgradeAnalysisReport.SQL)

## Running

1. Open SQL Management Studio.
2. Open the Upgrade analysis report script **UpgradeAnalysisReport.SQL** in a new query window.
3. Change the database connection to your AX2012 business data database, for example, MicrosoftDynamicsAX.
   > [!NOTE]
   > The script requires the model store database to cross check against object data. However, the script isn't directly executed against the model store.
4. Execute the script.
5. Save or copy and paste the results in a spreadsheet.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
