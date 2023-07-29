---
# required metadata

title: Upgrade from AX 2012 - Estimate effort by using the Code upgrade service
description: This article explains how to use the Code upgrade service in Microsoft Dynamics Lifecycle Services to estimate the tasks and effort that are required in order to upgrade a code base.
author: LaneSwenka
ms.date: 07/27/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 106163
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2017-05-31
ms.dyn365.ops.version: Platform update 8

---

# Upgrade from AX 2012 - Estimate effort by using the Code upgrade service

[!include [banner](../includes/banner.md)]

[!include [upgrade banner](../includes/upgrade-banner.md)]

This article explains how to use the Code upgrade service in Microsoft Dynamics Lifecycle Services to help estimate the tasks and effort that are required in order to upgrade a code base from Microsoft Dynamics AX 2012 finance and operations.

## Overview

The Code upgrade service converts an export of your AX 2012 model store to the correct format. However, the new version of your code won't be fully functional until a developer resolves any issues that the service identifies but can't resolve itself.

The Code upgrade service performs these actions:

- Directly resolve some types of conflict issues.
- For other issues, log Microsoft Azure DevOps tasks.
- Create a version of your code in the correct format, and check the new version into a new branch of your Azure DevOps project.

In the Analyze phase, we use the report to help estimate the effort that's required to complete code conversion activities.

The following illustration shows an overview of the process for configuring the Code upgrade service.

![Configuration process for the Code upgrade service.](media/codeUpgradeConfigurationProcess.png)

For information about how to configure the Code upgrade service, see [Configure the code upgrade service in Lifecycle Services (LCS)](../lifecycle-services/configure-execute-code-upgrade.md).

The output of the Code upgrade service is designed to be consumed by a developer. This output will help the developer estimate the effort that's required to complete the code upgrade tasks. To form an estimate, the developer must review the tasks that the service generates in Azure DevOps and the new version of the code that the service generates.

## Details

The Code upgrade service works by connecting to your Azure DevOps project, finding your Trunk\\Main branch, branching to a new branch that's named Releases\\\<version number\>, and then doing the code upgrade there. After this process is completed, you can synchronize your developer environment to this new branch under Releases\\\<version number\> and resolve conflicts. After you've compiled and tested your upgraded code, you can merge the new branch back into Trunk\\Main by using Source Control Explorer in Visual Studio. At that point, the process is completed.

Dynamics 365 finance and operations apps don't allow for customization via overlayering of Microsoft models. Before you upgrade, you must have a plan to refactor your customizations into extensions. For more information, see [Extensibility](../extensibility/extensibility-home-page.md) and [Relax model restrictions to refactor overlayering into extensions](../extensibility/refactoring-over-layering.md).

## Process

### Export your AX 2012 model store

> [!NOTE]
> The AX 2012 Management utilities must be installed in the environment that you want to export the model store from. For more information, see [Install management utilities](../../dynamicsax-2012/appuser-itpro/install-management-utilities.md).

To export the model store, follow these steps.

1. Open **Microsoft Dynamics AX 2012 Management Shell**, which is located under **Administrative Tools**.
2. Run the following command to export the model store. Adjust the path as required.

    ```
    axutil exportstore /file:C:\Temp\AX2012R3CU12ModelStore
    ```

3. Compress (zip) the exported model store file (**\*.axmodelstore**).

### Create the Trunk\\Main folder structure

For the Code upgrade service to recognize your source code, your Azure DevOps project must contain a Team Foundation Version Control (TFVC) code repository. In addition, the folder structure of the code repository must conform to the following strict pattern:

- **For code and metadata:** `/<Azure DevOps project name>/Trunk/Main/Metadata`
- **For Visual Studio project and solution files:** `/<Azure DevOps project name>/Trunk/Main/Projects`

You can create new folders directly in the Azure DevOps web interface, under **Repos**.

> [!NOTE]
> - Folder names are case sensitive.
> - By default, Azure DevOps projects use Git version control. You must add a TFVC repository.
>
>    1. Go to **Project settings**, and select **Repositories**.
>    2. Select **New repository**.
>    3. In the **Type** field, select **TFVC**.
>    4. Select **Create**.

### Create a personal access token

To connect to an Azure DevOps project, Lifecycle Services is authenticated by using a personal access token. Follow these steps to create a personal access token in Azure DevOps. If you've already configured your Lifecycle Services project to connect to your Azure DevOps project, you can skip this section.

1. Sign in to VisualStudio.com, and find your Azure DevOps project.
2. Select **User settings**, and then select **Personal access tokens**.
3. Select **New token** to create a personal access token. Set the following fields:

    - **Name** – Enter an appropriate name.
    - **Organization** – This field should be set to the organization by default.
    - **Expiration** – Enter a date.
    - **Scopes** – Set this field to **Full access**.

4. Select **Create**.
5. Copy the **CodeUpgrade token** value to your clipboard.

> [!NOTE]
> You won't be able to find the token details after this step is completed. Confirm that the token code is copied before you navigate away from the page.

### Configure your Lifecycle Services project to connect to Azure DevOps

1. In your Lifecycle Services project, go to the **Project settings** tile, and select **Azure DevOps**.
2. Select **Setup Azure DevOps**. This configuration is required by many Lifecycle Services tools. If you've already configured Lifecycle Services to connect to your Azure DevOps project, you can skip this section.
3. Enter the site for your Azure DevOps organization and the access token that you created earlier. Then select **Continue**.
4. Select the project in your Azure DevOps organization that you want to connect to. Then select **Continue**.
5. On the **Review and save** page, select **Save**.

### Run the Code upgrade tile

1. In your Lifecycle Services project, select the **Code upgrade** tile.
2. Select **Add**, and set the following fields:

    - **Name** – Enter a name for the code upgrade.
    - **Description** – Enter a description.
    - **Version you are upgrading from** – Specify **Microsoft Dynamics AX 2012**.
    - **Release you are upgrading to** – Specify **Dynamics 365 for finance and operations**.
    - **Estimation only** – Select this checkbox to generate a report without checking in or creating a new code branch in Azure DevOps. Use this setting when you want to evaluate the potential size of the work that's involved in the upgrade before you commit to the actual upgrade.

3. Select **Create**.
4. Select **Add files**. Then, on the **File upload** page, set the following fields:

    - **File Type** – Specify **ModelStore.zip file**.
    - **Browse** – Browse for the exported compressed model store file that you created earlier.

5. Select **Upload**.
6. After the file is uploaded, it appears on the **Code upgrade service file upload** page. Select the zip file.
7. Select **Analyze code**. The code upgrade process is started. For a large solution, this process typically takes 40 to 60 minutes to be completed.
8. Return to the **Code upgrade** tile in Lifecycle Services, and select the name of your analysis to view the results.
9. The code upgrade service creates a new branch and checks the upgraded code in to your Azure DevOps project. After the upgrade process is completed, your code exists in a new branch under the **Releases** folder. The branch name is suffixed with the date and time of the upgrade.

> [!NOTE]
> If you selected the **Estimation only** checkbox, no code is uploaded into Azure Dev Ops.

### Merge Releases back into Trunk\\Main

After the upgraded code in Releases\\\<version number\> is successfully compiled, and you've completed your code migration and testing, the branch can be merged into Trunk\\Main.

To merge the branch, follow these steps in your development environment in Visual Studio.

1. Open the **Source Control Explorer** pane.
2. Tap and hold (or right-click) the **Releases\\\<version number\>** branch, and then select **Branching and merging** \> **Merge**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
