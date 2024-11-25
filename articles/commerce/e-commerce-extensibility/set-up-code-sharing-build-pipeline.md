---
# required metadata

title: Set up Azure DevOps code sharing and create a build pipeline
description: This article describes how to set up code sharing with Microsoft Azure DevOps and create a build pipeline for your Microsoft Dynamics 365 Commerce online extensibility code. 
author: samjarawan
ms.date: 05/28/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Set up Azure DevOps code sharing and create a build pipeline

[!include [banner](../includes/banner.md)]

This article describes how to set up code sharing with Microsoft Azure DevOps and create a build pipeline for your Microsoft Dynamics 365 Commerce online extensibility code. 

By taking advantage of the capabilities of [Azure DevOps](/azure/devops/user-guide/what-is-azure-devops), you can help your team plan work, collaborate on code development, and automate the building of deployment packages for Dynamics 365 Commerce e-Commerce.

This article guides you through the steps that are required to complete the following tasks:

* Create a GitHub repository (repo) for the Commerce online software development kit (SDK).
* Create and configure a build pipeline to generate a Commerce online deployable package.

## Create an Azure DevOps GitHub repo

You can create an Azure DevOps GitHub repo project from a new or existing Azure DevOps service subscription. For more information, see [Azure DevOps Service](https://azure.microsoft.com/pricing/details/devops/azure-devops-services/). To get started with a free trial account, see the [Get started with Azure DevOps](/azure/devops/user-guide/sign-up-invite-teammates) quickstart guide.
To create an Azure DevOps GitHub repo, follow these steps.

1. After the Azure DevOps service is set up for your organization, create a new Azure DevOps project.

    ![Azure DevOps "Create a project to get started" page with "Private" visibility selected](media/code-sharing-1.png)

1. Enter a project name and a description. Select **Private** or **Enterprise** visibility, so that the project is accessible to your organization and developers.

    ![Azure DevOps new project page.](media/code-sharing-2.png)

1. For this example, you will use Git to clone the SDK code. Git is a free, open-source distributed version control system. Go to <https://git-scm.com/downloads> to download and install the latest build. You should be able to accept all the default installation values.

1. Install Visual Studio Code. Visual Studio Code is a lightweight source code editor that runs on your desktop, and is available for Windows, macOS, and Linux. It includes built-in support for JavaScript, TypeScript, and Node.js. Go to <https://code.visualstudio.com> to download the latest stable build. Then open the installer, and accept the user license agreement. You should be able accept all the default installation values.

1. Clone the Commerce online SDK. The SDK provides everything that you need to extend your e-Commerce site. For example, you can use it to create new modules, data actions, and themes. The SDK configuration package is available through the following GitHub repo: <https://github.com/microsoft/Msdyn365.Commerce.Online>.

    There are two ways to get the SDK configuration packages to your development computer. You can either download the packages directly from the GitHub repo, or you can clone the repo. 

    To clone the repo, follow these steps:

    1. Open a Command Prompt window as an admin, and create a directory to hold your e-Commerce site code (for example, **c:\\repos**).
    1. From the new directory, enter **git clone \<YOUR\_GIT\_REPO\>**, where \<YOUR\_GIT\_REPO\> is your GitHub repo. Because you're pulling from the GitHub repo only one time, you can remove the .git folder, which is a hidden directory under the root.

    Here is an example.

    ```console
    md c:\repos
    cd c:\repos
    git clone https://github.com/microsoft/Msdyn365.Commerce.Online.git
    cd Msdyn365.Commerce.Online
    ```

1. Clone the Azure DevOps GitHub project repo:

    1. In the left navigation pane, under **Repos**, select **Files**.
    1. Select the **Copy** button to copy the URL.

        ![Azure DevOps "Files" page with "Files" link and copy button highlighted](media/code-sharing-3.png)

    1. Open a Command Prompt window as an admin, and create a directory to hold your e-Commerce site code (for example, **c:\\repos**).
    1. From the new directory, enter **git clone \<AZURE\_DEVOPS\_GIT\_REPO\>**, where \<AZURE\_DEVOPS\_GIT\_REPO\> is the Azure DevOps GitHub project repo. A new, empty folder that has the name of the Azure DevOps project will be created.

        ```console
        cd c:\repos
        git clone https://xxxxxx.dev.azure.com/<DevOpsProjectName>/_git/<DevOpsProjectName>
        ```

1. Copy all the contents of C:\\repos\\Msdyn365.Commerce.Online to C:\\repos\\\<DevOpsProjectName\>. Don't copy the hidden .git folder.

1. In Visual Studio Code, open the **c:\\repos\\\<DevOpsProjectName\>** folder. When you select the **Source Control** button on the left, Visual Studio Code shows the new changes that must be committed.

1. To commit all the changes to Git, enter a description in the field at the top of the **Source Control: Git** pane, and then select the check mark symbol above it. When you're prompted to stage all your changes and commit them directly, select **Yes**.

    !["Source Control" button and check mark symbol highlighted on the "Source Control: Git" pane in Visual Studio Code](media/code-sharing-4.png)

1. Select the ellipsis (**...**) to the right of the check mark symbol, and then, on the menu that appears, select **Push** to push the changes to the repo.

    !["Push" item highlighted on the flyout menu in Visual Studio Code](media/code-sharing-5.png)

In Azure DevOps, you should now see the new files.

![Azure DevOps "Files" page with new files listed](media/code-sharing-6.png)

## Create and configure a new build pipeline in Azure DevOps

To create and configure a new build pipeline in Azure DevOps, follow these steps.

1. In the left navigation pane, under **Pipelines**, select **Pipelines**, and then select **Create Pipeline** in the main part of the page.

    ![Azure DevOps "Pipelines" page with "Create Pipeline" highlighted](media/code-sharing-7.png)

1. Select **Use the classic editor**.

    ![Azure DevOps "Where is your code?" page with the "Use the classic editor" link highlighted](media/code-sharing-8.png)

1. In the **Repository** field, select your Azure DevOps GitHub repo project, and then select **Continue**.

    ![Azure DevOps "Select your repository" page with the "Repository" field highlighted](media/code-sharing-9.png)

1. Under **Select a template**, select **Empty job**.

    ![Azure DevOps "Choose a template" page with "Empty job" link highlighted](media/code-sharing-10.png)

1. Next to **Agent job**, select the plus sign (**+**) to add a new agent job.

    ![Azure DevOps pipeline "Tasks" tab with "Agent job" plus sign highlighted](media/code-sharing-11.png)

1. In the **Add tasks** pane on the right, search for "PowerShell," and then, in the **PowerShell** task, select **Add**.

    ![Azure DevOps "Add tasks" pane with search box and PowerShell task "Add" button highlighted](media/code-sharing-12.png)

1. In the main part of the page, select **PowerShell Script**. Then, in the **PowerShell** pane on the right, under **Type**, select **Inline**. Copy the following script into the **Script** field.

    ```console
    yarn
    yarn msdyn365 pack
    ```

    ![Azure DevOps "PowerShell" pane with the "Inline" option and the "Script" field value highlighted](media/code-sharing-13.png)

1. In the right pane, on the **Advanced** FastTab, in the **Working Directory** field, enter **$(Build.SourcesDirectory)**.

    ![Azure DevOps "PowerShell" pane with the "Advanced" FastTab and the "Working directory" field highlighted](media/code-sharing-14.png)

1. In the main part of the page, next to **Agent job**, select the plus sign (**+**) to add a new agent job.

1. In the **Add tasks** pane on the right, search for "copy," and then, in the **Copy files** task, select **Add**.

    ![Azure DevOps "Add tasks" pane with search box and "Copy files" task "Add" button highlighted](media/code-sharing-15.png)

1. In the main part of the page, select the **Copy files** task, and then, in the **Copy files** pane on the right, follow these steps:

    1. In the **Source Folder** field, enter **$(Build.SourcesDirectory)**.
    1. In the **Contents** field, enter **\*.zip**.
    1. In the **Target Folder** field, enter **$(Build.ArtifactStagingDirectory)**.

    ![Azure DevOps "Copy files" pane with "Source Folder," "Contents," and "Target Folder" fields highlighted](media/code-sharing-16.png)

1. In the main part of the page, next to **Agent job**, select the plus sign (**+**) to add a new agent job.

1. In the **Add tasks** pane on the right, search for "publish," and then, in the **Publish Pipeline Artifacts** task, select **Add**.

    ![Azure DevOps "Add tasks" pane with search box and "Publish Pipeline Artifacts" task "Add" button highlighted](media/code-sharing-17.png)

1. In the main part of the page, select the **Publish Pipeline Artifacts** task. Then, in the **Publish Pipeline Artifacts** pane on the right, follow these steps:

    1. In the **File or directory path** field, enter **$(Build.ArtifactStagingDirectory)**.
    1. In the **Artifact name** field, enter **drop**.

    ![Azure DevOps "Publish Pipeline Artifacts" pane with "File or directory path" and "Artifact name" fields highlighted](media/code-sharing-18.png)

1. On the toolbar, select **Save & queue**.

    !["Save and queue" highlighted on the toolbar](media/code-sharing-19.png)

1. In the **Run pipeline** dialog box, make sure that the **Agent Specification** field is set to **windows-2019**, and then select **Save and run**.

    !["Run pipeline" dialog box with "Agent specification" field and "Save and run" button highlighted](media/code-sharing-20.png)

    Tools that you typically use to build, test, and run JavaScript apps (such as npm, Node, Yarn, and Gulp) are preinstalled on Microsoft-hosted agents in Azure Pipelines. For the exact versions of Node.js and npm that are preinstalled, see the Microsoft-hosted agents. To install a specific version of these tools on Microsoft-hosted agents, add the **Node Tool Installer** task to the beginning of your process. Yarn and Node.js version 16.x are both preinstalled on the windows-2019 agent.
    
    > [!NOTE]
    > Version 10.0.26 and earlier of the online SDK requires Node version 12.x. To support this on the agent, add the Node tool installer task specifying version 12.x ahead of the PowerShell task, as shown in the following illustration.

    ![Add the Node task to install version 12](media/code-sharing-25.png)   

1. Monitor the agent job logs to learn when the job is completed.

    ![Azure DevOps showing running job with agent job logs](media/code-sharing-21.png)

1. After the job is completed, in the left navigation pane, under **Pipelines**, select **Pipelines**. Then, on the **Runs** tab, under **All pipeline runs**, select the pipeline run to download the deployable package.

    ![Azure DevOps "Pipelines" page with "Runs" tab and pipeline run highlighted](media/code-sharing-22.png)

1. Under **Summary**, under **Artifacts**, select **1 published**.

    ![Pipeline run page with "1 published" link highlighted](media/code-sharing-23.png)

1. Select the **drop** folder to expand it and see the zip file that was created as part of the pipeline run. Select the **Download** button to download the file.

    !["Artifacts" page showing the pipeline run zip file under the expanded "Drop" folder](media/code-sharing-24.png)

## Increase Node memory size

The default memory setting should be sufficient for most customization scenarios. However, if your application needs more heap space (for example, if you see a "JavaScript heap out of memory" build error) you can specify the environment variable in the **scripts** section of the package.json file by adding **--max_old_space_size=4096**, as shown in the following example.

```json
"build": "SET NODE_OPTIONS=--max_old_space_size=4096 && yarn msdyn365b build --use-eslint",
```

## Additional resources

[Get started with e-commerce online extensibility development](sdk-getting-started.md)

[System requirements for a Dynamics 365 Commerce online extensibility development environment](system-requirements.md)

[Set up a development environment](setup-dev-environment.md)

[Configure a development environment (.env) file](configure-env-file.md)

[Configure an e-commerce development environment against a Commerce cloud environment](debug-tier-1.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
