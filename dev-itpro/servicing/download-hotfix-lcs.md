---
# required metadata

title: Download hotfixes from Lifecycle Services
description: Use this tutorial to download the Microsoft Dynamics AX hotfixes from Lifecycle Services (LCS).
author: kfend
manager: AnnBe
ms.date: 2016-02-26 19 - 53 - 09
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 56171
ms.assetid: 61069cf2-6c3f-4ebc-bbee-b21b1c99626a
ms.search.region: Global
# ms.search.industry: 
ms.author: anupams
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Download hotfixes from Lifecycle Services

Use this tutorial to download the Microsoft Dynamics AX hotfixes from Lifecycle Services (LCS).

This tutorial will guide you through downloading the newest version of Microsoft Dynamics hotfix from Lifecycle services (LCS).  This tutorial is a part of the [Servicing environments](developer-landing-page.md#servicing-environments) content.

1.  Log in to LCS with your credentials.
2.  Select an environment from the LCS project.
3.  On the **Environment** page, **Monitoring** is shown in two sections, **X++ updates** and **Binary updates**. The update tiles show the hotfixes that are relevant or required for your environment. For example, if a specific X++ hotfix is already installed on your environment, we will not include that X++ hotfix in the  X++ updates.There are two kinds of updates - X++ updates and binary updates. There are two kinds of binary updates - application and platform.
4.  Select one of the update tiles to view the list of available hotfixes that can be used to create a hotfix package for download.
5.  Select the applicable KBs, and then click **Add hotfix to package**. [![](./media/add-hotfixes.png)](./media/add-hotfixes.png) **Note**: For X++ updates, if you want to download all available updates at this point, you should click on Select all and then click on **Add** instead of **Add hotfix to package**.
6.  Click **Download package** to download the hotfix package. [![](./media/donwload-hotfix.png)](./media/donwload-hotfix.png) After you select **Download package**, the **Review and download hotfixes** page will open. Use this page to review selected hotfixes, discard the package, return to the hotfix selections, or download the final package. [![](./media/review-and-download-hotfixes.png)](./media/review-and-download-hotfixes.png)

This tutorial is a part of the [Servicing environments](developer-landing-page.md#servicing-environments) content.

