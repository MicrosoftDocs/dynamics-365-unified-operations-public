---
# required metadata

title: Deployment with continuous build and test automation
description: This topic describes how to deploy a developer topology that supports continuous build and test automation.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 13171
ms.assetid: 300b7ebe-c320-4a2f-89a9-33635c7108d2
ms.search.region: Global
# ms.search.industry: 
ms.author: shailesn
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Deployment with continuous build and test automation

[!include[banner](../includes/banner.md)]


This topic describes how to deploy a developer topology that supports continuous build and test automation.

Prerequisite: This requires a Visual Studio Team Services (VSTS) account for cloud VM deployment.

## Workflow
After you have configured a VSTS subscription in Lifecycle Services (LCS), you can trigger Developer Topology Deployment to set up Developer and Build VMs. In this deployment, the Developer VM is configured with workspace mapping to develop against a VSTS project. The Build VM is auto-configured with the build agent/controller to build modules  VSTS project and to execute automated tests with external endpoint for validation. For more information on writing custom test code or generating automated test code to integrate with build infrastructure, see [Testing and validations](testing-validation.md). A typical workflow or usage scenario is shown below. 

[![build12](./media/build12-1024x693.jpg)](./media/build12.jpg)

## Set up Visual Studio Team Services (VSTS)
Compare VSTS features required for your organization: <https://www.visualstudio.com/products/visual-studio-team-services-feature-matrix-vs>

-   **TFVC vs GIT**: For RTW, we only support TFVC as source control repository that can be configured in VSTS project connected to LCS. Git is not supported.
-   **Suspend current builds:** If you are deploying the build agent on an existing VSTS project which already has build definition created, please ensure you do not have any active triggers to queue the build. Additionally, make sure there are no builds scheduled / queued against the build pool. 
    
    [![BuildTriggers](./media/buildtriggers.jpg)](./media/buildtriggers.jpg)
    
-   **Free VSTS account provides only one build agent**. Using free VSTS account and deploying new build VM with another build agent will fail as your account is not provisioned for more than one build agent.

To use more than one build agents, setup your VSTS account with Azure billing: <https://www.visualstudio.com/get-started/setup/set-up-billing-for-your-account-vs> 

[![VSTS1](./media/vsts1-300x155.jpg)](./media/vsts1.jpg)

-   After your account is linked with the Azure subscription. Follow the instructions in the Azure management portal to provision more build agents - <https://www.visualstudio.com/en-us/get-started/setup/get-more-build-or-load-testing-vs>

[![VSTS2](./media/vsts2-300x151.jpg)](./media/vsts2.jpg) 

Note: make sure you increase “Private Agents” under PAID option. 

[![VSTS3](./media/vsts3-300x191.jpg)](./media/vsts3.jpg)

-   **Build Agent Pool role and permissions:** <https://msdn.microsoft.com/library/vs/alm/build/agents/admin#agent-pools>

Once build agents are added, add user (who will be deploying build VM from LCS) to “Agent Pool Administrators” role. 

[![VSTS4](./media/vsts4.jpg)](./media/vsts4.jpg)

-   **Manage agent:** If you have multiple agents configured and want to delete one, select the agent and use the delete button to the right of the status column.

    [![build14](./media/build14.jpg)](./media/build14.jpg)

-   **Deleting Default Pool:** If for some reason you have deleted the default pool, please do not create a new pool with the name "Default". Instead create a new pool with the different name and pass the pool name from the "Advanced Settings" customization from LCS during deployment.
-   **Personal access token:** This token is used for all Lifecycle Services (LCS) background actions, including upgrade and deployment. When a user initiates actions from LCS, LCS expects that users will be added to VSTS. The user must authorize LCS access to VSTS on behalf of the user. Until the projects users authorize with VSTS, you will see the below message in action center: 

[![VSTS setup in LCS\_May27](./media/vsts-setup-in-lcs_may27-300x216.jpg)](./media/vsts-setup-in-lcs_may27.jpg)

## Deploy Developer topology from LCS
LCS provides an option to deploy a Development topology environment. With this option, you can deploy developer and build VMs in the cloud that are connected to your Visual Studio Team System  (VSTS) project.

### VSTS credential setup and linking to LCS project

1.  Login to the LCS portal to connect to VSTS and your LCS project at [https://lcs.dynamics.com/](https://lcs.dynamics.com/en/).
2.  Select a project that you are working on.
3.  Click the **Project Settings** tile.
4.  Select **Visual Studio Team Services** and enter the VSTS URL where the source code for your module project is located.
5.  Specify the VSTS link, authorize, and then click **Choose default project**.
6.  **Note:** We currently support VSTF as source control and do not support Git. 

    [![VSTS](./media/vsts-1024x792.jpg)](./media/vsts.jpg)

### Check-in migrated or new module code into VSTS

As part of code Migration process or development activities, we expect you to check-in your model source files and the associated test model source files into VSTS. If you have migrated your code using the LCS migration service, this is automatically done for you. If you have not checked in any code into VSTS and work on direct check-in, you must follow certain guidelines for the VSTS folder structure. This will help with setting up correct build definition. All modules should be added to root folder **Metadata**. Under each module, there should be two folders. One folder contains all models. The other folder should contain descriptor XML for that module. 

![VSTS folder structure](media/build-trunk-main-metadata.png)

### Deploy developer topology (Developer and Build VM)

1.  In the LCS portal, select the project that is connected to VSTS.
2.  In the **Environments** pane, click **+** to deploy a new environment.

    ![Azure settings](media/azure-settings.png)
    
3.  In the **Select environment topology** pane, select **Azure**.

    ![select environment topology](media/select-environment-topology.png)
    
4.  Proceed to deploy a DEV/TEST environment.
    -   Depending on your LCS project type, some deployment steps described below may vary.

5.  On the **Deploy environment** pane, enter the environment name for the deployment, and select the number of instances for **Developer** VMs.
6.  **Note:** You can only deploy one Build VM and one Developer VM. If you don’t want to deploy a Developer VM, then set instances count to zero. If you want multiple Developer VMs then deploy new environment per developer VM.

    [![Deploy](./media/deploy-1024x669.jpg)](./media/deploy.jpg)
    
7.  Click **Advanced settings**, select **Visual Studio Team Services**
    1.  Build Agent Name: Friendly name for build agent on VSTS
    2.  Build Agent Pool: specify build agent pool name which should be used for build machine deployment. Make sure VSTS contains at least one agent pool. By default, there will be the default pool. If you have deleted the default pool then build deployment will fail.
    3.  Branch Name: Specify your VSTS source code branch which will be default source code sync location for the build VM. Default branch is "Trunk\\Main".
    
    [![Settings](./media/settings-1024x389.jpg)](./media/settings.jpg)

8.  After the settings are verified, click **Next** to start the deployment. You can see progress of deployment under **Environments**.
9.  After the deployment is complete, you can use Remote Desktop to view Developer and Build VM.

## Use a Developer VM environment
When a Developer VM gets deployed, it’s auto-configured with a workspace that will be used to synchronize your code from source control (VSTS). As this Developer VM has Microsoft Dynamics 365 for Finance and Operations, Enterprise edition deployed on it, it can also be used as a test VM.

### Configure Visual Studio to connect to VSTS

When you open Visual Studio the first time on a Developer VM, connect to VSTS using your credentials.

1.  Open **Team explorer** and click **Select Team projects**.
2.  Enter the VSTS URL and click **OK**. You will be prompted for your VSTS username and password.
3.  After you are logged into the VSTS, your **Default workspace** that you will use for your development.

    ![manage workspaces](media/manage-workspaces.png)

## Test integration with the build
There are two ways to integrate test as part of build process for testing and validation:

-   SysTest framework based unit and component level tests.
-   Generate code from Task Recorder recording XML for automated test execution.

The details of these two approaches are mentioned in the [Testing and validation. ](testing-validation.md)Review this article for testing and validation strategy.

## Use the Build VM environment
When a Build VM is deployed in Developer topology through LCS, it is pre-configured and ready to start a build. You can change the default configuration at any time from the Visual Studio IDE or the VSTS interface. On a Build VM, the module source code is synchronized to the build machine for easy build setup. The build machine is also auto-configured with default settings for build agent, build controller, build process template, and build definition. Tests that are integrated with build definition are executed after the build is successful.

### Review a pre-configured customizable build environment

The build VM contains the vNext build agent which was released as part of TFS 2015. When you deploy the Build VM, the build agent is configured by default to connect and sync with the VSTS project. As a part of the Build VM configuration, the default build definition is also created and configured, as shown below. 

[![Build1](./media/build1-1024x488.jpg)](./media/build1.jpg) 

Default build definition contains multiple tasks to perform specific operation, as described below.

1.  Configure the predefined variables parameters that will be passed to the build. To set up a clean database for every build execution, provide the name of the database backup file for the **DatabaseBackupToRestore** variable. The packages folder is restored at every build with a copy of a clean package folder.

    [![build2](./media/build2-1024x678.jpg)](./media/build2.jpg)
    
2.  Build the solution to discover and build all modules under "Trunk/Main" branch as shown below.

    [![Build3](./media/build3-1024x456.jpg)](./media/build3.jpg)
    
3.  Use "Deploy Report" task to generate reports and deploy on build VM.
4.  Use "Database Sync" task to synchronize the database to local SQL on build VM.
5.  After the build is successful, create a deployable package that can be used to update sandbox/ staging environment.

    [![Build4](./media/build4-1024x462.jpg)](./media/build4.jpg)
    
6.  "Copy and publish build artifacts" uploads the deployable package to VSTS artifacts location.

    [![build5](./media/build5-1024x439.jpg)](./media/build5.jpg)
    
7.  For test execution, there are three default tasks "Test Setup", "Execute Test" and "Test End".

    [![build7](./media/build7-1024x457.jpg)](./media/build7.jpg)
    
8.  The default build is scheduled to trigger start every day at 5 P.M. You can change trigger as per your team's need to "Continuous" for each check-in.

    [![build8](./media/build8-1024x491.jpg)](./media/build8.jpg)

You can make changes to the default configuration, and the build VM will be ready to trigger a build.

## Start a build and verify the build and test execution results
After you review the default build configuration, you can manually trigger a build from Visual Studio IDE or VSTS web interface.

1.  Open your browser and connect to the VSTS URL.
2.  Login using your credentials.
3.  On the home page, under **Recent projects and solutions**, select a project.
4.  From top links options, select **BUILD**.
5.  On the left panel, select the default build definition instance.
6.  Right-click and select **Queue Build** to trigger a build for your module and test module that is already checked into the VSTS source control.

[![image045](./media/image045.png)](./media/image045.png) 

Success or failure for the build will display, as shown by the following examples. View all builds. 

[![build9](./media/build9-1024x443.jpg)](./media/build9.jpg) 

Select specific completed build and view success/ failure details. 

[![build10](./media/build10-1024x446.jpg)](./media/build10.jpg) Click on Test link to visualize test execution failure. 

[![build11](./media/build11-1024x455.jpg)](./media/build11.jpg)



