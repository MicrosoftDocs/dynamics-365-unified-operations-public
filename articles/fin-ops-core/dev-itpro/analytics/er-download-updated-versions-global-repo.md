---
# required metadata

title: Import updated versions of ER configurations 
description: This topic explains how to import updated versions of ER configurations from the Global repository of Configuration service.
author: NickSelin
manager: AnnBe
ms.date: 06/09/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERSolutionImport, ERWorkspace, ERSolutionRepositoryTable
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 105843
ms.assetid: dc44dea2-22ce-401e-98b9-d289e0e2825b
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 10.0.5

---

# Import updated versions of ER configurations

[!include [banner](../includes/banner.md)]

ER [repositories](general-electronic-reporting.md#Repository) are used to share [Electronic reporting (ER) configurations](general-electronic-reporting.md#Configuration). You can [import](download-electronic-reporting-configuration-lcs.md) desire ER configurations from different repositories to your Finance instance. Upon you imported ER configurations, new [versions](general-electronic-reporting.md#component-versioning) of them could be published to repositories by configuration [providers](general-electronic-reporting.md#Provider) for sharing. This topic explains how to import updated versions of ER configurations from the Global repository of Configuration service. For more information, see [Microsoft Dynamics 365 for Finance and Operations - Regulatory Services, Configuration service](https://docs.microsoft.com/business-applications-release-notes/october18/dynamics365-finance-operations/regulatory-service-configuration).

## Review available updated versions

1. Sign in to the Dynamics 365 Finance application using one of the following roles:
    - Electronic reporting developer
    - Electronic reporting functional consultant
    - System administrator
2. Go to **Organization administration > Workspaces > Electronic reporting**.
3. In the **Related links** section, select **Import configurations versions updates**.
    <br>![Electronic reporting workspace](./media/er-download-updated-versions-global-repo1.png)
4. On the **Import ER configurations versions updates** dialog page, in the **Run mode** field, select **Only show available updates** to get the following information about ER configurations of the current Finance instance in comparison with the content of the Global repository:
    <br>![Electronic reporting workspace](./media/er-download-updated-versions-global-repo2.png)
    1. Total number of ER configurations.
    2. ER configurations that are not presented in the Global repository.
    3. ER configurations the latest version of which are already available in the current Finance instance.
    <br>![Electronic reporting workspace](./media/er-download-updated-versions-global-repo3.png)
    4. ER configurations the latest version of which are available in the Global repository for import to the current Finance instance.
    <br>![Electronic reporting workspace](./media/er-download-updated-versions-global-repo4.png)

## Import available updated versions

1. Sign in to the Dynamics 365 Finance application using one of the following roles:
    - Electronic reporting developer
    - Electronic reporting functional consultant
    - System administrator
2. Go to **Organization administration > Workspaces > Electronic reporting**.
3. In the **Related links** section, select **Import configurations versions updates**.
4. On the **Import ER configurations versions updates** dialog page, in the **Run mode** field, select **Import latest updates** to import the latest versions of ER configurations from the Global repository to the current Finance instance.
5. In the **Run in background** section, set **Batch processing** to **Yes** if you want to schedule a batch job for doing such import. Configure the required recurrence if you want to repeat such import periodically.
    <br>![Electronic reporting workspace](./media/er-download-updated-versions-global-repo5.png)
6. When you run this import interactively, review user Infolog to learn what configuration versions have been imported. 
    <br>![Electronic reporting workspace](./media/er-download-updated-versions-global-repo6.png)
7. When you run this import in batch mode, do the following to learn what configuration versions have been imported.
    1.  Open **Common \> Inquiries \> Batch jobs \> My batch jobs**.
    2.  Find the **Import electronic reporting configurations versions updates** job.
    3.  Open job history.
    4.  Open job log.
    <br>![Electronic reporting workspace](./media/er-download-updated-versions-global-repo7.png)

## Additional resources

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[Download ER configurations from the Global repository of Configuration service](er-download-configurations-global-repo.md)
