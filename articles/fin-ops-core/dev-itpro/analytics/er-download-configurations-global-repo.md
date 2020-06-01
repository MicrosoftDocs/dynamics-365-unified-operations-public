---
# required metadata

title: Download ER configurations from Gloabl repository of Configuration service (RCS)
description: This topic explains how to download Electronic reporting (ER) configurations from Global repository of Configuration service (RCS).
author: NickSelin
manager: AnnBe
ms.date: 05/29/2020
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

# Import Electronic reporting (ER) configurations from Gloabl repository of Configuration service

[!include [banner](../includes/banner.md)]

This topic explains how to download [Electronic reporting (ER)](#general-electronic-reporting.md) configurations from Gloabl repository of for [Configuration service](https://docs.microsoft.com/business-applications-release-notes/october18/dynamics365-finance-operations/regulatory-service-configuration).

This tutorial guides you through the process of downloading the newest version of ER configurations from Gloabl repository of Configuration service.

## Open configurations repository

1. Sign in to the Finance application by using one of the following roles:

    - Electronic reporting developer
    - Electronic reporting functional consultant
    - System administrator

2. Go to **Organization administration** &gt; **Workspaces** &gt; **Electronic reporting**.
3. In the **Configuration providers** section, select the **Microsoft** tile.
4. On the **Microsoft** tile, click **Repositories**.

    ![Electronic reporting workspace](./media/er-download-configurations-global-repo-er-workspace.png)

5. On the **Configuration repositories** page, in the grid, select the existing repository of the **Global** type. If this repository doesn't appear in the grid, follow these steps:

    1. Click **Add** to add a new repository.
    2. Select **Global** as the repository type.
    3. Click **Create repository**.
    4. If prompted, follow the authorization instructions.
    5. Enter a name and description for the repository.
    6. Click **OK** to confirm the new repository entry.
    7. In the grid, select the new repository of the **Global** type.

6. Click **Open** to view the list of ER configurations for the selected repository.

    ![Configuration repositories page](./media/er-download-configurations-global-repo-repositories-list.png)

## Import a single configuration

1. In the configurations tree in the left pane, select the ER configuration that you require.
2. On the **Versions** FastTab, select the required version of the selected ER configuration.
3. On the **Versions** FastTab, click **Import** to download the selected version from Gloabl repository to the current instance.

    > [!NOTE]
    >
    > The **Import** button is unavailable for ER configuration versions that are already present in the current Finance instance.

    ![Configuration repository page](./media/er-download-configurations-global-repo-repository-content.png)

## Import filtered configurations

1. Expand **Filter** FasTab.
2. Specify selection conditions to import desire configurations:
    1. In the **Tags** grid, add desire tags.
    2. In the **Country/region applicability** field, select desire country/region codes.
    3. Select **Apply filter**.

    > [!NOTE]
    >
    > The **Configurations** FastTab shows all configuratons that have been filtered as satisfying specified selection conditions.

3. On the **Configurations** FastTab, click **Import** to download the filtered configurations from Gloabl repository to the current instance.
4. On the **Configurations** FastTab, click **Reset filter** to clean up specified selection conditions.

    ![Configuration repository page](./media/er-download-configurations-global-repo-filtered-configurations.png)

> [!NOTE]
>
> Depending on the ER settings, configurations are validated after they are imported. You might be notified about any inconsistency issues that are discovered. You must resolve those issues before you can use the imported configuration version. For more information, see the list of related articles for this topic.

> [!NOTE]
>
> ER configuratoins might be configured as dependent on other configurations. Thefore, along with a selected configuration, other configurations might be automatically imported. For more about configuration dependencies, see [Define the dependency of ER configurations on other components](tasks/er-define-dependency-er-configurations-from-other-components-july-2017.md).

## Additional resources

[Electronic reporting (ER) overview](general-electronic-reporting.md)
