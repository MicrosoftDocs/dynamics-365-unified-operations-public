---
title: Deploy and use a continuous build and test automation environment
description: Learn about how to deploy a developer topology that supports continuous build and test automation, including prerequisites and an overview of the workflow.
author: josaw1
ms.author: shailesn
ms.topic: install-set-up-deploy
ms.date: 01/22/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Deploy and use a continuous build and test automation environment

[!include [banner](../includes/banner.md)]

This article describes how to deploy and use an environment that supports continuous build and test automation.

## Prerequisites

Cloud deployment of virtual machines (VMs) requires a Microsoft Azure DevOps subscription.

## Workflow

After you configure an Azure DevOps subscription in Microsoft Dynamics Lifecycle Services, you can use Lifecycle Services to deploy developer VMs or build/test VMs. Lifecycle Services configures a developer VM that you can map to an Azure DevOps project. Lifecycle Services also configures a build VM that it automatically maps to an Azure DevOps project. The build VM has a build agent and controller that builds modules from the Azure DevOps project and runs automated tests that have an external endpoint for validation. The following illustration shows a typical workflow.

![Relationship of Lifecycle Services, Azure DevOps, and VMs.](./media/deploy-build-test.png)

This workflow includes a Lifecycle Services deployment of a developer VM and a build/test VM in Azure.

+ Lifecycle Services creates developer and the build/test environments in Azure. To create a build/test environment, Lifecycle Services must be able to determine where the source code for the Azure DevOps project is.
+ The developer works on source code on the developer VM, and the work is synced to the Azure DevOps project.
+ The build process synchronizes the code from Azure DevOps onto the build/test VM and produces deployable packages that you can apply to sandbox and production environments. The source code doesn't flow directly from the development VM to the build/test VM. They're synced through Azure DevOps.

For information about how to write custom test code or generate automated test code to integrate with the build infrastructure, see [Testing and validations](testing-validation.md).

## Set up Azure DevOps

### Choose a plan

The first step is to [choose an Azure DevOps plan](https://azure.microsoft.com/pricing/details/devops/azure-devops-services) for your organization.

### Set up Azure DevOps

To set up Azure DevOps, follow these steps:

1. [Create a personal access token](../lifecycle-services/synchronize-bpm-vsts.md#lifecycle-services-project-settings-set-up-azure-devops). Use the token for all Lifecycle Services background actions. These actions include upgrade and deployment. When users initiate actions from Lifecycle Services, Lifecycle Services expects that those users are added to Azure DevOps. The users must authorize Lifecycle Services access to Azure DevOps on their behalf.
1. [Configure Lifecycle Services](../lifecycle-services/synchronize-bpm-vsts.md#lifecycle-services-project-settings-set-up-azure-devops).

Until you authorize Lifecycle Services access to Azure DevOps, you see a "setup is not complete" message in action center.

### Suspend current builds

If you're deploying a build environment on an existing Azure DevOps project that already has a build definition, make sure that you don't have any active triggers to queue the build. Also, make sure that no builds are scheduled or queued against the build pool.

## Deploy Developer and Build/Test environments from Lifecycle Services

Lifecycle Services provides an option to deploy Development and Build/Test environments. By using this option, you can deploy developer and build VMs in the cloud that is connected to your Azure DevOps project.

Alternatively, you can use [Microsoft-hosted agents](../dev-tools/hosted-build-automation.md) to build and deploy your X++ code.

### Azure DevOps credential setup and linking to Lifecycle Services project

If you didn't already set up your Lifecycle Services project to connect to your Azure DevOps project, do it before you deploy a build environment.

1. Sign in to the Lifecycle Services portal to connect to Azure DevOps and your Lifecycle Services project at [https://lcs.dynamics.com/](https://lcs.dynamics.com/).
1. Select a project that you're working on.
1. Select the **Project Settings** tile.
1. Select **Azure DevOps** and enter the Azure DevOps URL where the source code for your module project is located.
1. Specify the Azure DevOps link, authorize, and then select **Choose default project**.

### Check in migrated or new module code to Azure DevOps

During code migration or development, check in your model source files and the associated test model source files to Azure DevOps. If you migrate your code by using the Lifecycle Services migration service, the service automatically checks in your code. If you work on direct check-in and don't check in any code to Azure DevOps, follow certain guidelines for the Azure DevOps folder structure. This structure helps you set up the correct build definition. Add all modules to the root folder **Metadata**. Each module should have two folders: one folder contains all models, and the other folder contains the descriptor XML for that module. 

![Azure DevOps folder structure.](media/build-trunk-main-metadata.png)

### Deploy a build environment

The article [Deploy and access development environments](../dev-tools/access-instances.md) describes how to deploy developer environments. Use the same flow to deploy a build environment. As you go through the deployment or configuration wizard, when prompted to **Select a Topology**, select **DevTest**. Then select a **Build and Test** topology.

You can configure the build agent name and build agent pool as part of the deployment wizard.

Click **Advanced settings**, select **Azure DevOps**
   1.  Build Agent Name: Friendly name for build agent on Azure DevOps
   1.  Build Agent Pool: specify build agent pool name which should be used for build machine deployment. Make sure Azure DevOps contains at least one agent pool. By default, there is the default pool. If you delete the default pool, the build deployment fails.
   1.  Branch Name: Specify your Azure DevOps source code branch which is the default source code sync location for the build VM. The default branch is "Main".

   
## Test integration with the build

Integrate tests into the build process for testing and validation by using two approaches:

-   SysTest framework based unit and component level tests.
-   Generate code from Task Recorder recording XML for automated test execution.

The [Testing and validation](testing-validation.md) article describes these two approaches. Review this article for the testing and validation strategy.

## Use the Build VM environment

When you deploy a Build VM in Developer topology through Lifecycle Services, it comes preconfigured and ready to start a build. You can change the default configuration at any time from the Visual Studio IDE or the Azure DevOps interface. On a Build VM, the module source code synchronizes to the build machine for easy build setup. The build machine also autoconfigures with default settings for the build agent, build controller, build process template, and build definition. Tests that integrate with the build definition run after the build succeeds.

### Review a preconfigured customizable build environment

The build VM contains the vNext build agent that Microsoft released as part of **Azure DevOps**. When you deploy the build VM, the build agent is configured by default to connect and sync with the Azure DevOps project. As part of the build VM configuration, the default build definition is also created and configured, as shown in the following section. 

[![Default build definition.](./media/build1-1024x488.jpg)](./media/build1.jpg) 

The default build definition contains multiple tasks to perform specific operations, as described in the following list.

1.  Configure the predefined variables parameters that the build passes. To set up a clean database for every build execution, provide the name of the database backup file for the **DatabaseBackupToRestore** variable. The build restores the packages folder at every build with a copy of a clean package folder.

    [![List of predefined variables pane.](./media/build2-1024x678.jpg)](./media/build2.jpg)

1.  Build the solution to discover and build all modules under "Trunk/Main" branch as shown in the following section.

    [![Build the solution pane.](./media/build3-1024x456.jpg)](./media/build3.jpg)

1.  Use the "Deploy Report" task to generate reports and deploy on build VM.
1.  Use the "Database Sync" task to synchronize the database to local SQL on build VM.
1.  After the build is successful, create a deployable package that you can use to update sandbox or staging environment.

    [![Generate packages pane.](./media/build4-1024x462.jpg)](./media/build4.jpg)

1.  The "Copy and publish build artifacts" task uploads the deployable package to Azure DevOps artifacts location.

    [![Publish Artifact pane.](./media/build5-1024x439.jpg)](./media/build5.jpg)

1.  For test execution, there are three default tasks: "Test Setup", "Execute Test", and "Test End".

    [![Execute Tests pane.](./media/build7-1024x457.jpg)](./media/build7.jpg)

1.  The default build is scheduled to trigger start every day at 5 P.M. You can change trigger as per your team's need to "Continuous" for each check-in.

    [![Default build schedule.](./media/build8-1024x491.jpg)](./media/build8.jpg)

You can make changes to the default configuration, and the build VM is ready to trigger a build.

## Start a build and verify the build and test execution results

After you review the default build configuration, you can manually trigger a build from Visual Studio IDE or Azure DevOps web interface.

1.  Open your browser and connect to the Azure DevOps URL.
1.  Sign in by using your credentials.
1.  On the home page, under **Recent projects and solutions**, select a project.
1.  From the top links, select **BUILD**.
1.  On the left panel, select the default build definition instance.
1.  Right-click and select **Queue Build** to trigger a build for your module and test module that you already checked into the Azure DevOps source control.

The portal displays the success or failure for the build, as shown by the following examples. You can view all builds. 

[![Display of build success or failure.](./media/build9-1024x443.jpg)](./media/build9.jpg) 

Select a specific completed build to view success or failure details. 

[![View details of build success or failure.](./media/build10-1024x446.jpg)](./media/build10.jpg) Select the **Test** link to visualize test execution failure. 

[![Visualize test execution failure.](./media/build11-1024x455.jpg)](./media/build11.jpg)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
