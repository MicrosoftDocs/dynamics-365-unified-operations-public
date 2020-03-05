---
# required metadata

title: Set up Azure DevOps code sharing and create a build pipeline
description: This topic describes how to set up code sharing with Azure DevOps and create a build pipeline for your Microsoft Dynamics 365 Commerce online extensibility code. 
author: samjarawan
manager: annbe
ms.date: 03/05/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Set up Azure DevOps code sharing and create a build pipeline

[!include [banner](../includes/banner.md)]

This topic describes how to set up code sharing with Azure DevOps and create a build pipeline for your Microsoft Dynamics 365 Commerce online extensibility code. 

## Overview

Leveraging [Azure DevOps](https://docs.microsoft.com/azure/devops/user-guide/what-is-azure-devops?view=azure-devops) will allow your team to plan work, collaborate on code development, and automate the building of your Dynamics 365 Commerce e-Commerce deployment packages.

This topic will guide you through the steps needed to:
* Create a GitHub repository (repo) for the Dynamics 365 Commerce online software development kit (SDK).
* Create and configure a build pipeline to generate a Dynamics 365 Commerce online deployable package.

##  Create an Azure DevOps Github repo

You can create an Azure DevOps GitHub repo project from a new or existing Azure DevOps service subscription. For more information, see [Azure DevOps Service](https://azure.microsoft.com/pricing/details/devops/azure-devops-services/). To get started with a free trial account, see the [Get started with Azure DevOps](https://docs.microsoft.com/azure/devops/user-guide/sign-up-invite-teammates?view=azure-devops) quickstart guide.

To create an Azure DevOps Github repo, follow these steps.

1. Once the Azure DevOps service is set up for your organization, create a new Azure DevOps project.

    ![Create new project](media/code-sharing-1.png)

1. Provide a project name and description. Select private or enterprise visibility so that it's accessible to your organization and developers.

    ![Provide project name](media/code-sharing-2.png)

1. We'll be using Git, a free and open source distributed version control system, to clone our SDK code. Go to https://git-scm.com/downloads to download and install the latest build. You should be able to accept all the default install values.

1. Install Visual Studio Code. Visual Studio Code is a lightweight source code editor that runs on your desktop and is available for Windows, macOS, and Linux. It comes with built in support for JavaScript, TypeScript, and Node.js. Go to https://code.visualstudio.com to download the latest stable build. Once downloaded, launch the installer and accept the user license agreement. You should be able accept all the default install values.

1. Clone the Microsoft Dynamics 365 Commerce Online SDK. The SDK will give you everything you need to extend your e-Commerce site including the ability to create new modules, data actions, and themes. The SDK configuration package is available through the following GitHub repository: https://github.com/microsoft/Msdyn365.Commerce.Online.

    There are two ways to get the SDK configuration packages to your development machine: you can either download it directly from the GitHub repo, or you can clone the repo. 

    To clone your repo, follow these steps.
        
    1. Launch a command prompt with administrator privileges and create a directory to hold your e-Commerce site code (for example, "c:\repos").  
    1. From the new directory, enter **git clone <YOUR_GIT_REPO>**, where <YOUR_GIT_REPO> is your Git repo. Since you're only pulling from the git repository once, you can remove the .git folder, which is a hidden directory under the root.

    ```console
    md c:\repos
    cd c:\repos
    git clone https://github.com/microsoft/Msdyn365.Commerce.Online.git
    cd Msdyn365.Commerce.Online
    ```

1. Clone the Azure DevOps GitHub project repo:
    1. Under the **Repos** on the left navigation pane, select **Files**.
    1. Select the copy symbol to copy the URL.

        ![Clone Azure DevOps repo](media/code-sharing-3.png)

    1. Launch a command prompt with administrator privileges and create a directory to hold your e-Commerce site code (for example, "c:\repos"). 
    1. From the new directory, enter **git clone <AZURE_DEVOPS_GIT_REPO>**, where <AZURE_DEVOPS_GIT_REPO> is the Azure DevOps GitHub project repo. A new, empty folder with the name of the Azure DevOps project will be created.

    ```console
    cd c:\repos
    git clone https://xxxxxx.dev.azure.com/<DevOpsProjectName>/_git/<DevOpsProjectName>
    ```

1. Copy all of the contents of "C:\repos\Msdyn365.Commerce.Online" to "C:\repos\\\<DevOpsProjectName>". Do not copy the hidden .git folder.

1. With Visual Studio Code, open the folder "c:\repos\\\<DevOpsProjectName>". When you select the source control tab on the left, Visual Studio Code will show the new changes to be committed.
1. To commit all of the changes to Git, enter a description in the text box at the top of the **SOURCE CONTROL: GIT** pane, and then select the checkmark symbol above it. When prompted to stage all your changes and commit them directly, select **Yes**.

    ![Commit changes](media/code-sharing-4.png)

1. Select the ellipsis symbol ("...") to the right of the checkmark symbol, and then in the flyout menu select **Push** to push the changes to the repo.  

    ![Push changes](media/code-sharing-5.png)

In Azure DevOps, you should now see the new files.

![New files in Azure DevOps](media/code-sharing-6.png)

## Create and configure a new build pipeline in Azure DevOps

To create and configure a new build pipeline in Azure DevOps, follow these steps.

1. Under **Pipelines** in the left navigation pane, select **Pipelines**, and then select **Create Pipeline** in the main window.

    ![Create a pipeline](media/code-sharing-7.png)

1. Select **Use the classic editor**.

    ![Select classic editor](media/code-sharing-8.png)

1. Select your Azure DevOps GitHub repo project, and then select **Continue**.

    ![Select repository](media/code-sharing-9.png)

1. Under **Select a template**, select **Empty job**.

    ![Select an empty job template](media/code-sharing-10.png)

1. Next to **Agent job**, select the plus symbol ("+") to add a new agent job.

    ![Add new agent job](media/code-sharing-11.png)

1. In the **Add tasks** pane, search for "PowerShell", and then in the **PowerShell** task, select **Add**.

    ![Add PowerShell task](media/code-sharing-12.png)

1. In the main window, select **PowerShell Script**. Then in the right pane under **Type**, select **Inline**, and then copy the script below into the **Script** box.

    ```console
    yarn
    yarn msdyn365 pack
    ```
  
    ![Configure task](media/code-sharing-13.png)

1. In the right pane, select **Advanced** to expand the section and then enter **$(Build.SourcesDirectory)** in the **Working Directory** box. 

    ![Set working directory](media/code-sharing-14.png)

1. In the main window next to **Agent job**, select the plus symbol ("+") to add a new agent job.

1. In the **Add tasks** pane, search for "copy", and then in the **Copy files** task, select **Add**.

    ![Add copy files agent](media/code-sharing-15.png)

1. In the main window, select the **Copy files** task, then in the **Copy files** pane, do the following:
    1. In the **Source Folder** box, enter **$(Build.SourcesDirectory)**. 
    1. In the **Contents** box, enter **\*.zip**. 
    1. In the **Target Folder** box, enter **$(Build.ArtifactStagingDirectory)**.

    ![Configure Copy Files task](media/code-sharing-16.png)

1. In the main window next to **Agent job**, select the plus symbol ("+") to add a new agent job.

1. In the **Add tasks** pane, search for "publish", and then in the **Publish Pipeline Artifacts** task, select **Add**.

    ![Add Publish Pipline Artifacts agent](media/code-sharing-17.png)

1. In the main window, select the **Publish Pipeline Artifacts** task. Then in the **Publish Pipeline Artifacts** pane, do the following:
    1. In the **File or directory path** box, enter **$(Build.ArtifactStagingDirectory)**.
    1. In the **Artifact name** box, enter **drop**.

    ![Configure Publish Pipline Artifacts agent](media/code-sharing-18.png)

1. From the top menu, select **Save & queue**.

    ![Save and queue a build](media/code-sharing-19.png)

1. In the **Run pipeline** pane, ensure that the value in the **Agent Specification** box is set to **vs2017-win2016**, and then select **Save and run**.

    ![Save and run](media/code-sharing-20.png)

    Tools that you commonly use to build, test, and run JavaScript apps (such as npm, Node, Yarn, and Gulp) are preinstalled on Microsoft-hosted agents in Azure Pipelines. For the exact versions of Node.js and npm that are preinstalled, refer to the Microsoft-hosted agents. To install a specific version of these tools on Microsoft-hosted agents, add the Node Tool Installer task to the beginning of your process. "VS2017-win2016" comes with yarn preinstalled.

1. Monitor the agent job logs for job completion.

    ![Agent job logs](media/code-sharing-21.png)

1. After the job is completed, under **Pipelines** in the left navigation pane, select **Pipelines**. Then select the **Runs** tab, and under **All pipeline runs** select the run to download the deployable package.

    ![Pipeline runs](media/code-sharing-22.png)

1. Under **Summary \> Artifacts**, select **1 published**.

    ![Published artifacts](media/code-sharing-23.png)

1. Select the **drop** folder to expand it and see the zip file that was created as part of the run. Select the download symbol to download the file.

    ![Published artifacts](media/code-sharing-24.png)
    
## Additional resources

[System requirements for a Dynamics 365 Commerce online extensibility development environment](system-requirements.md)

[Set up a development environment](setup-dev-environment.md)

[Configure a development environment (.env) file](configure-env-file.md)
