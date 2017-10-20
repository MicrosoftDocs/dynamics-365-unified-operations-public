---
# required metadata

title: Download updates from Lifecycle Services
description: Use this tutorial to download hotfixes for Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, from Lifecycle Services (LCS).
author: kfend
manager: AnnBe
ms.date: 10/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 56171
ms.assetid: 61069cf2-6c3f-4ebc-bbee-b21b1c99626a
ms.search.region: Global
# ms.search.industry: 
ms.author: anupams
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Download updates from Lifecycle Services

[!include[banner](../includes/banner.md)]

Use this tutorial to download updates from Microsoft Dynamics Lifecycle Services (LCS). This tutorial is a part of the [Servicing environments](..\dev-tools\developer-home-page.md#service-environments) content.

## Types of updates

- **Binary updates** are pre-compiled and cumulative. Every subsequent binary update includes all previous updates. These updates don't have to be compiled in a development environment, and they can be applied directly to a non-development environment from LCS.

    If you're running an environment that has retail functionality and a customized instance of Cloud point of sale (POS), you must complete the additional steps that are listed under Retail SDK packaging. For Microsoft Dynamics 365 for Retail, all updates, even updates for application models, are released as binary updates.

- **X++ updates** include updates to specific application functionality in application models. These updates can be independently downloaded and applied. You can select specific X++ updates to apply to your environment. Any dependent X++ updates are then automatically selected and downloaded. X++ updates are source code updates. Before they can be applied to a non-development environment, they must be compiled in a developer environment and merged with any customizations. X++ updates apply only to Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.

## Download an update

1. Sign in to LCS by using your credentials.
2. In the LCS project, select an environment.
3. On the **Environment** page, the **Monitoring** section includes update tiles. For Retail, you will see tile for binary updates only. For Finance and Operations, you will see tiles for both X++ updates and binary updates. These two types of updates can be independently downloaded and applied. However, some X++ updates might depend on binary updates, and some binary updates might depend on X++ updates. Any dependencies are included in the update description.
4. Select an update tile to view the list of available hotfixes that you can use to create a hotfix package for download.
5. On the **Add hotfixes** page, select the applicable Knowledge Base (KB) numbers, and then select **Add hotfix to package**.

    [![Add a hotfix](./media/add-hotfixes.png)](./media/add-hotfixes.png)

    > [!NOTE]
    > For X++ updates, you can download all available updates at this point. Select **Select all**, and then select **Add** instead of **Add hotfix to package**.

6. Select **Download package**.

    [![Download the hotfix](./media/donwload-hotfix.png)](./media/donwload-hotfix.png)

7. On the **Review and download hotfixes** page, you can review the hotfixes that you selected, discard the package, return to the hotfix selections, or download the final hotfix package.

    [![Review and download hotfixes](./media/review-and-download-hotfixes.png)](./media/review-and-download-hotfixes.png)
