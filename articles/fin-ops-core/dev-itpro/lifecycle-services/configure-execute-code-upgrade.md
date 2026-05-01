---
title: Configure the code upgrade service in Lifecycle Services
description: Learn about how to configure the Code upgrade tile to migrate your solution to the latest version of the finance and operations apps.
author: LaneSwenka
ms.author: laswenka
ms.topic: upgrade-and-migration-article
ms.date: 03/06/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 964b5a15-9b9c-434c-a4c2-e14406ebfaeb
ms.custom: sfi-image-nochange
---

# Configure the code upgrade service in Lifecycle Services

[!include [banner](../includes/banner.md)]
[!include [LCS freeze](../../../includes/lcs-freeze-banner.md)]

This article explains how to configure the **Code upgrade** tile in Microsoft Dynamics Lifecycle Services to migrate your solution to the latest version of the Dynamics 365 finance and operations apps.

## Overview

The code upgrade tool connects to your Azure DevOps project, locates your Trunk\Main branch, and branches to a new branch named Releases\<version number>. It then performs the code upgrade. After this process is complete, you can synchronize your developer environment to this new branch under Releases\<version number> and resolve conflicts. When you compile and test your upgraded code, you can merge the new branch back into Trunk\Main by using source control explorer in Visual Studio.

Dynamics 365 for Finance and Operations version 8.0 and newer doesn't allow customization through overlayering of Microsoft models. Before you upgrade, plan to refactor your customizations into extensions. For more information, see the [Extensibility home page](../extensibility/extensibility-home-page.md) and [Relax model restrictions to refactor overlayering into extensions](../extensibility/refactoring-over-layering.md).

## Process

### Create the Trunk\Main folder structure

For the code upgrade service to recognize your source code, your Azure DevOps project must contain a Team Foundation Version Control (TFVC) code repository. In addition, the code repository folder structure must conform to the following strict pattern.

- For code and metadata: `/<DevOps project name>/Trunk/Main/Metadata`
- For Visual Studio project and solution files: `/<DevOps project name>/Trunk/Main/Projects`

 You can create new folders directly in the Azure DevOps web interface under **Repos**.

> [!NOTE]
>
> - Folder names are case sensitive, that is, you must use Main and not MAIN, or the code upgrade service won't recognize the folder.
> - Azure DevOps projects use Git version control by default. You need to add a TFVC repository.
>
>     1. Go to **Project settings**, and then select **Repositories**.
>     1. Select **New repository**.
>     1. In the **Type** field, select **TFVC**, and then select **Create**.

### Create a personal access token

To connect to an Azure DevOps project, Lifecycle Services authenticates by using a personal access token. Use the following steps to create a personal access token in Azure DevOps. If you already configured your Lifecycle Services project to connect to your Azure DevOps project, you can skip this section.

1. Sign in to visualstudio.com and locate your Azure DevOps project.
1. In the top-right corner, hover over your name to open a menu, and then select **Security**.
1. Select **Add** to create a new personal access token, give it a name, and then enter the amount of time that you want the token to last for. Select **Create Token**.  

   :::image type="content" source="./media/codeupgrademaketoken.png" alt-text="Screenshot of the Code upgrade create token page.":::

1. Copy the token to your clipboard. You can't find the token details after this step is completed, so be sure that you copy the token before navigating away from this page.

### Configure your Lifecycle Services project to connect to Azure DevOps

1. In your Lifecycle Services project, go to the **Project settings** tile, select **Visual Studio Team Services**, and then select the **Setup Visual Studio Team Services** button. Many Lifecycle Services tools need this configuration. If you already configured Lifecycle Services to connect to your Azure DevOps project, you can skip this section.

   :::image type="content" source="./media/lcs_vsts_setup.png" alt-text="Screenshot of the Lifecycle Services VSTS setup page.":::

1. Enter the root URL for your Azure DevOps organization and the access token you created earlier, and then select **Continue**.

   :::image type="content" source="./media/lcstoken.png" alt-text="Screenshot of the Lifecycle Services token entry page.":::

1. Select the project within your Azure DevOps organization that you want to connect to, and select **Continue**.

   :::image type="content" source="./media/lcs_selectproject.png" alt-text="Screenshot of the Lifecycle Services select project page.":::

1. On the **Review and save** page, select **Save**.

### Create an ax7.version file

> [!NOTE]
> If you're migrating from AX 2012, you can skip this step.

The code upgrade tile in Lifecycle Services automatically finds the version that you're migrating from by reading the ax7.version file under the Main folder in your source control. You must create this file manually, either in Visual Studio or through the Azure DevOps web portal, as shown in the following image. This file isn't needed if you're migrating your code from Dynamics AX 2012 R3 or an earlier version. The version number entered here must be the application version (not the platform version). Take care to enter the correct version number because an incorrect version number in this file might cause your code upgrade run to fail.

:::image type="content" source="./media/ax7_versionfile.png" alt-text="Screenshot of the ax7 version file.":::

For more information about how to identify which application version you have, see [Overview of Microsoft Dynamics AX build numbers](https://blogs.msdn.microsoft.com/axsupport/2012/03/29/overview-of-microsoft-dynamics-ax-build-numbers/).

### Execute the code upgrade tile

1. In your Lifecycle Services project, select the **Code upgrade** tile.

   :::image type="content" source="./media/codeupgradetile.png" alt-text="Screenshot of the Code upgrade tile.":::

1. In the lower-left corner of the screen, select **Add**, and then enter a name and description. Select the version you're upgrading from as Microsoft Dynamics AX 7, and then select **Create**.

   - If you're upgrading your code from Dynamics AX 2012 R3, select the version you're upgrading from. You see a prompt to upload a zipped version of your Dynamics AX 2012 R3 model store file.
   - If you select the **Estimation Only** check box, the tool only generates a report and doesn't check in or create a new code branch in Azure DevOps for you. Use this option if you want to evaluate the potential size of the work involved in upgrading before you commit to the actual upgrade.

   :::image type="content" source="./media/codeupgrade_new.png" alt-text="Screenshot of the new code branch creation page.":::

1. Select **Analyze code** in the lower-right corner. The code upgrade process starts. This process typically takes 40 minutes for a large solution to complete. When it finishes, return to the **Code upgrade** tile in Lifecycle Services to view the results.
1. The code upgrade service creates a new branch and checks in the upgraded code to your Azure DevOps project. After the upgrade process finishes, your code exists in a new branch under the **Releases** folder. The branch name is suffixed with the date and time of the upgrade.

   :::image type="content" source="./media/codeupgradebranch.png" alt-text="Screenshot of the code upgrade branch in Azure DevOps.":::

### Merge Releases back into Trunk\\Main

When the upgraded code in `Releases\\<version number>` compiles successfully and you complete your code migration and testing, you're ready to merge this branch back into `Trunk\\Main`. To merge, on your development environment in Visual Studio, open the Source control explorer pane. Then right-click on the `Releases\\<version number>` branch. In the context menu, go to **Branching and Merging**. On the submenu, select **Merge**.

:::image type="content" source="./media/MergeReleasesBranch.PNG" alt-text="Screenshot of the merge release branch option in Visual Studio Source Control Explorer.":::

The [Source Control Merge Wizard](https://www.visualstudio.com/docs/tfvc/merge-folders-files#sourcecontrolwizard) opens. It guides you through merging the `Releases\\<version number>` branch back into `Trunk\\Main`.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
