---
title: Import Electronic reporting (ER) configurations
description: This article explains how to import Electronic reporting (ER) configurations from Lifecycle Services (LCS) to a local business data application.
author: kfend
ms.date: 06/17/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Platform Update 8
ms.assetid: 
ms.search.form: ERSolutionTable, ERWorkspace, ERSolutionRepositoryTable, ERSolutionImport
---

# Import Electronic reporting (ER) configurations

[!include [banner](../includes/banner.md)]

This article explains how to download [Electronic reporting (ER) configurations](general-electronic-reporting.md#Configuration) from Microsoft Dynamics Lifecycle Services (LCS) to a local business data application. It also explains how to upload the ER configurations from an ER repository to the local business data (LBD) application.

> [!IMPORTANT]
> The use of LCS as a storage repository for ER configurations is being [deprecated](../../../finance/get-started/removed-deprecated-features-finance.md#features-removed-or-deprecated-in-the-finance-10017-release). For more information, see [Regulatory Configuration Service (RCS) – Lifecycle Services (LCS) storage deprecation](../../../finance/localizations/rcs-lcs-repo-dep-faq.md).

1. Sign in to your local business data application by using one of the following roles:

    * Electronic reporting developer
    * Electronic reporting functional consultant
    * System administrator

2. Go to **Organization administration** \> **Electronic reporting**.
3. In the **Configuration providers** section, select the card for the ER provider that is associated with your company.

    > [!NOTE]
    > To learn how to register a new ER solution provider, play the **Create a configuration provider and mark it as active** task guide.

4. On the selected tile, click **Repositories**.


5. On the **Configuration repositories** page, in the grid, select the existing repository of the **File system** type. If the repository doesn't appear in the grid, follow these steps:

    1. Click **Add** to add a new repository.
    2. Select **FILE SYSTEM** as the repository type.
    3. Click **Create repository**.
    4. Enter a name and description for the repository.
    5. Enter the path of the working directory for this repository. This path should point to a folder of the local file system where the ER configurations that belong to the repository will be stored.
    6. Click **OK** to confirm and save the new repository.
    7. In the grid, select the new repository of the **File system** type.

6. In your browser, open another tab, and sign in to LCS.
7. In the Shared asset library, select the **GER Configuration** asset type, and then click **Download all**.

    > [!NOTE]
    > All the ER configurations will be put into a zip file for download.

8. Open the file, select all the ER configurations, and then copy them to the working directory for the repository of the **File system** type.
9. On the **ER repositories** page, on the **Dynamics 365 Finance** tab, click **Open** to view the list of ER configurations for the selected repository.
10. In the **Configurations** tree in the left pane, select an ER configuration.
11. On the **Versions** FastTab, select the required version of the ER configuration.
12. Click **Import** to download the selected version from this repository to the current instance.

    > [!NOTE]
    > The **Import** button is unavailable for existing ER configuration versions.

> [!NOTE]
> Depending on the ER settings, configurations are validated after they are imported. You might be notified about inconsistencies or issues that are discovered. You must resolve these inconsistencies or issues before you can use the imported configuration version.

## Frequently asked questions

**Question:** When I click **Download all** in the Shared asset library, I receive the following warning: “Zip generation is in progress, please try again in a few minutes.” Why do I receive this warning?

**Answer:** You receive this warning because a new configuration is added to the Shared asset library, and the ER configuration is being archived.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

