---
# required metadata

title: Download Electronic reporting configurations from Lifecycle Services
description: This tutorial explains how to download Electronic reporting (ER) configurations from Microsoft Dynamics Lifecycle Services (LCS).
author: kfend
manager: AnnBe
ms.date: 2016-08-01 14 - 19 - 02
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: ERSolutionImport, ERWorkspace
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 105843
ms.assetid: 97d82c77-b117-4356-973c-4a3d83d7dc3d
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.dyn365.intro: May-16
ms.dyn365.version: AX 7.0.1

---

# Download Electronic reporting configurations from Lifecycle Services

This tutorial explains how to download Electronic reporting (ER) configurations from Microsoft Dynamics Lifecycle Services (LCS).

This tutorial guides you through the process of downloading the newest version of Electronic reporting (ER) configurations from Microsoft Dynamics Lifecycle Services (LCS).

1.  Sign in to Dynamics 365 for Operations by using one of the following roles:
    -   Electronic reporting developer
    -   Electronic reporting functional consultant
    -   System administrator

2.  Go to **Organization administration** &gt; **Electronic reporting**.
3.  In the **Configuration providers** section, select the **Microsoft** tile.
4.  On the **Microsoft** tile, click **Repositories**. [![Update ER from LCS for MS - open MS repositories list](./media/update-er-from-lcs-for-ms-open-ms-repositories-list.png)](./media/update-er-from-lcs-for-ms-open-ms-repositories-list.png)
5.  On the **Configuration repositories** page, in the grid, select the existing repository of the **LCS** type. If this repository doesn't appear in the grid, follow these steps:
    1.  Click **Add** to add a new repository.
    2.  Select **LCS** as the repository type.
    3.  Click **Create repository**.
    4.  If prompted, follow the authorization instructions.
    5.  Enter a name and description for the repository.
    6.  Click **OK** to confirm the new repository entry.
    7.  In the grid, select the new repository of the **LCS** type.

6.  Click **Open** to view the list of ER configurations for the selected repository. [![Open button](./media/update-er-from-lcs-for-ms-make-lcs-repository.png)](./media/update-er-from-lcs-for-ms-make-lcs-repository.png)
7.  In the configurations tree in the left pane, select the ER configuration that you require.
8.  On the **Versions** FastTab, select the required version of the selected ER configuration.
9.  Click **Import** to download the selected version from LCS to the current Dynamics 365 for Operations instance. **Note:** The **Import** button is unavailable for ER configuration versions that are already present in the current Dynamics 365 for Operations instance. [![Import button](https://msdynamics.blob.core.windows.net/media/2016/05/Update-ER-from-LCS-for-MS-download-configuration-1024x565.png)](./media/update-er-from-lcs-for-ms-download-configuration.png)

**Note:** Depending on the ER settings, configurations are validated after they are imported. You might be notified about any inconsistency issues that are discovered. You must resolve those issues before you can use the imported configuration version. For more information, see the list of related articles for this tutorial.

See also
--------

[Electronic reporting overview](general-electronic-reporting.md)

