---
# required metadata

title: Upgrade from AX 2012 - Estimate effort by using the Code upgrade service
description: This article explains how to use the Code upgrade service in LCS to estimate the tasks and effort that are required in order to upgrade a code base.
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

This article explains how to use the Code upgrade service in Microsoft Dynamics Lifecycle Services (LCS) to help estimate the tasks and effort that are required in order to upgrade a code base from Microsoft Dynamics AX 2012 finance and operations.

## Overview
The Code upgrade service converts an export of your AX 2012 model store to the correct format. However, the new version of your code won’t be fully functional until a developer resolves any issues that the service identifies but can’t resolve itself.

The Code upgrade service performs these actions:

- Directly resolve some types of conflict issues.
- For other issues, log Microsoft Azure DevOps tasks.
- Create a version of your code in the correct format, and check the new version into a new branch of your Azure DevOps project.

In the Analyze phase, we use the report to help estimate the effort that is required in order to complete code conversion activities.

The following illustration shows an overview of the process for configuring the Code upgrade service.

![Configuration process for the Code upgrade service.](media/codeUpgradeConfigurationProcess.png)

For information about how to configure the Code upgrade service, see [Configure the code upgrade service in Lifecycle Services (LCS)](../lifecycle-services/configure-execute-code-upgrade.md).

The output of the Code upgrade service is designed to be consumed by a developer. This output will help the developer estimate the effort that is required in order to complete the code upgrade tasks. To form an estimate, the developer must review the tasks that the service generates in Azure DevOps and the new version of the code that the service generates.

## Details
The code upgrade service operates by connecting to your Azure DevOps project, locating your Trunk\\Main branch, branching to a new branch that will be named as Releases\\\<version number\>, and then performing the code upgrade there. After this process is complete, you can synchronize your developer environment to this new branch under Releases\\\<version number\> and resolve conflicts. When you have compiled and tested your upgraded code you can merge the new branch back into Trunk\\Main, using source control explorer in Visual Studio and the process is complete.

Dynamics 365 for finance and operations doesn't allow customization via overlayering of Microsoft models. Before you upgrade, you must have a plan to refactor your customizations into extensions. For more information, see [Extensibility](../extensibility/extensibility-home-page.md) and [Relax model restrictions to refactor overlayering into extensions](../extensibility/refactoring-over-layering.md).

## Process
### Export your AX 2012 model store
>[!NOTE]
>You will need to have the AX 2012 Management utilities installed on the environmnet you wish to export the model store from. For more information, see: [Install management utilities](../dynamicsax-2012/appuser-itpro/install-management-utilities.md).

To export the model store, follow these steps:
1. Open **Microsoft Dynamics AX 2012 Management Shell**, this is located under **Administrative Tools**
2. Run the following command to export the model store, adjust paths as needed:
   ```
   axutil exportstore /file:C:\Temp\AX2012R3CU12ModelStore
   ```
3. Compress (ZIP) the exported model store file (*.axmodelstore).
   
### Create the Trunk\\Main folder structure
For the code upgrade service to recognize your source code, your Azure DevOps project must contain a Team Foundation Version Control (TFVC) code repository. In addition, the code repository folder structure must conform to the following strict pattern. 
 - For code and metadata: `/<DevOps project name>/Trunk/Main/Metadata`
 - For Visual Studio project and solution files: `/<DevOps project name>/Trunk/Main/Projects`
 
You can create new folders directly in the Azure DevOps web interface under **Repos**.
 
> [!NOTE]
> - Folder names are case sensitive. 
> - Azure DevOps projects use Git version control by default. You will need to add a TFVC repository.
>     1. Go to **Project settings**, then **Repositories**.
>     2. Select **New repository**.
>     3. In the **Type** field, select **TFVC**, and click **Create**.

### Create a personal access token
To connect to an Azure DevOps project, LCS is authenticated using a personal access token. Use the following steps to create a personal access token in Azure DevOps. If you have already configured your LCS project to connect to your Azure DevOps project, you can skip this section.

1. Sign in to visualstudio.com and locate your Azure DevOps project.
2. Click **User settings**, select **Personal access tokens**.
3. Select **New token** to create a new personal access token, and set the following:
   - **Name** - Enter an appropriate name
   - **Organization** - This should default to organization
   - **Expiration** - Enter a date
   - **Scopes** - Set to full access
4. Click **Create** 
5. Copy the **CodeUpgrade token** to your clipboard. 
> [!NOTE]
> You won't be able to find the token details after this step is completed. Confirm that the token code is copied before navigating away from this page.

### Configure your Lifecycle Services project to connect to Azure DevOps
1. In your LCS project, go to the **Project settings** tile, select **Azure DevOps**.
2. Click **Setup Azure DevOps**. This configuration is needed by many LCS tools, if you have already configured LCS to connect to your Azure DevOps project, you can skip this section. 
3. **Enter the site** for your Azure DevOps organization and the access token created earlier. Select **Continue**.
4. **Select the project** within your Azure DevOps organization that you want to connect to. Select **Continue**. 
5. On the **Review and save** page, select **Save**.

### Execute the code upgrade tile

1. In your LCS project, select the **Code upgrade** tile. 
2. Select **Add** and enter: 
   - **Name** - Enter a name for the code upgrade
   - **Description** - Enter a description
   - **Version you are upgrading from** - Microsoft Dynamics AX 2012
   - **Release you are upgrading to** - Dynamics 365 for finance and operations 
   - **Estimation only** - Select this check box to generate a report and doesn't check in or create a new code branch in Azure DevOps. Use this option if you want to evaluate the potential size of the work involved in upgrading before you commit to the actual upgrade.
3. Click **Create**.
4. Select **Add files**, the **File upload** page will display. Set the following:
   - **File Type** - ModelStore.zip file
   - **Browse** - Browse for the exported compressed model store file created in the steps above.
   - Click **Upload**
6. After the file is uploaded, it will diplay on the **Code upgrade service file upload** page, select the zip file.
7. Select **Analyze code**. The code upgrade process starts and typically takes 40 to 60 minutes for a large solution to complete.
8. Return to the **Code upgrade** tile in LCS to view the results by clicking on the name of your analysis.
9. The code upgrade service creates a new branch and checks in the upgraded code to your Azure DevOps project. After the upgrade process is complete, your code will exist in a new branch under the **Releases** folder. The branch name is suffixed with the date and time of the upgrade. 
> [!NOTE]
> If **Estimation only** is selected, no code is uploaded into Azure Dev Ops.

### Merge Releases back into Trunk\\Main

After the upgraded code in Releases\\\<version number\> compiles successfully, and you have completed your code migration and testing, the branch can be merged into Trunk\\Main. 

To merge, on your development environment in Visual Studio, complete the following:
1. Open the Source control explorer pane. 
2. Right-click on the **Releases\\\<version number\>** branch.
3. In the context menu, go to **Branching and merging**, select **Merge**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
