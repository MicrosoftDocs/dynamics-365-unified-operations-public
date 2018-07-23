---
# required metadata

title: Set up new environments, Visual Studio Team Services, and branches for Retail projects
description: This topic describes recommended practices for Microsoft Dynamics 365 for Retail implementation projects.
author: Andreash1
manager: AnnBe
ms.date: 07/09/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
ms.search.industry: Retail
ms.author: andreash
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: Retail 7.3

---

# Set up new environments, Visual Studio Team Services, and branches for Retail projects

Starting in Microsoft Dynamics AX 7.0, most environments are hosted in the cloud. They are either Microsoft-hosted (on a Microsoft subscription) or cloud-hosted (on a customer subscription). By default, environments are Microsoft-hosted. Typically, cloud-hosted environments are used to provide more control over a development or build environment. For more details, see [Understand Lifecycle Services](../../dev-itpro/lifecycle-services/lcs-works-lcs.md).

Tier 1 machines are developer or build environments.

## Development Tier 1 environments

For implementations of Microsoft Dynamics 365 for Retail that include code extensions, we recommend that you use a development environment that has administrative privileges. If you use a development environment that doesn't have administrative privileges, other programming tools and features of the operating system (OS) cannot be installed or configured. An alternative setup is a machine that is hosted on a separate Microsoft Azure subscription. (This type of machine is also known as "cloud-hosted" in Microsoft Dynamics Lifecycle Services [LCS].)

There are three hosting models for a Tier 1 development or build environment: a Microsoft-hosted environment, a cloud-hosted environment, and a self-hosted downloaded virtual machine (VM).

If you want to extend channel components, see ‘Prepare the development environment’ below to configure a development environment so it is ready for development.

Because the decision about what hosting model to use has financial impact, you can reduce some of the hosting cost by using a Tier 1 environment as a simple test environment or golden config environment. One Tier 1 environment is free with your Dynamics subscription. Although this approach isn't ideal, it should work for most projects.

> [!NOTE]
> You can shut down cloud-hosted environments at any time. This capability helps reduce the hosting cost.

A hosting alternative is to download a virtual hard disk (VHD) from LCS and host it locally on a server. From a development perspective, VHD images have the same capabilities as a hosted VM. The only difference is that LCS deployments are not supported on VHDs. However, command-line deployments are supported.

The following table shows the advantages and disadvantages of each hosting model. Use this information to evaluate the model that will work best for your project.

<table>
<thead>
<tr>
<th>Hosting model</th>
<th>Advantages</th>
<th>Disadvantages</th>
</tr>
</thead>
<tbody>
<tr>
<td>Microsoft-hosted environment (in an LCS project, default or based on an add-on)</td>
<td>
<ul>
<li>One environment is included in the subscription. We recommend that you use this environment as a build environment.</li>
<li>Telemetry data is collected and is available on the LCS diagnostics page.</li>
</ul>
</td>
<td>
<ul>
<li>Users can't perform administrative actions.</li>
<li>Therefore, users can't install any tools or certificates.</li>
</ul>
</td>
</tr>
<tr>
<td>Cloud-hosted environment (in an LCS project, private subscription)</td>
<td>
<ul>
<li>Users have full administrative rights and can install any tools.</li>
<li>Users can install certificates.</li>
</ul>
</td>
<td>There is additional cost. (However, you can mitigate this cost by shutting down the environment.)</td>
</tr>
<tr>
<td>Self-hosted downloaded VM</td>
<td>The experience depends on the host. The experience can be much faster if the VM runs on a solid-state drive (SSD).</td>
<td>Users can't deploy any packages from LCS.</td>
</tr>
</tbody>
</table>

Tier 2 and higher machines are multi-box environments for multiple test and verification purposes. Production environments are hands-off, and the size of the environment is determined by the sizing process in LCS.

## Branches, build definitions, and environments

Branching is an important practice in software development. For more information about branching, see [Branching and Merging Primer](https://msdn.microsoft.com/en-us/library/aa730834(v=vs.80).aspx).

Here is a summary of branching from the preceding page:

> A branching and merging strategy involves a tradeoff between risk and productivity. You trade the safety of working in isolation for the increased productivity of working with other people. The productivity increases come with a cost—the additional effort required for merging software assets sometime in the future.
>
> Using branches provides better isolation and control of individual software assets and increases productivity, because teams or individuals can work in parallel. However, using branches also requires an increase in merge activities and therefore risk, because you must later reassemble branches into a whole.

For more information about the delivery of implementation projects for Microsoft Dynamics 365 for Finance and Operations, watch [ Continuous Delivery Using Dynamics 365 for Operations](https://mbspartner.microsoft.com/D365/Videos/101393).

There is no single best strategy for creating branches. The approach that is used depends on the project and the size of the implementation. The approach that Joris De Gruyter mentions in the preceding video is a successful method.

The following illustration shows three code branches: Dev, Main, and ProdRel1. The numbers indicate the order of setup.

[![Branch creation](./media/1-Three-Code-Branch.png)](./media/1-Three-Code-Branch.png)

Here is an explanation of the setup. The numbers in brackets refer to the numbers in the preceding illustration:

- The **Dev** branch [2] is used for daily work that isn't ready for testing or may not be stable but must be shared with other developers. For larger teams, you might want to have multiple Dev branches for different features or purposes.
- The **Main** branch [1] is for changes that meet a certain quality bar and are ready for testing by other people. This testing might include user acceptance tests, performance tests, integration tests, and sanity tests after hotfixes. Deployable packages for this branch must be created by a build environment. As a best practice, you should not generate X++ packages in a Tier 1 environment and then deploy those packages into an official test or production environment. In that case, uncommitted source changes could be included. The correct approach is always to deploy packages that were built on official build environments.
- The **ProdRel1** branch [3] holds all source code exactly as it's deployed in a production environment at any given point. A build environment can be used but isn't required. If packages from the Main branch are deployed to a production environment, the code should be merged (from Main to ProdRel1) after a production deployment. By having a branch for production, you can generate official builds later if you require them.
- All three branches hold both X++ code (extensions and hotfixes in Metadata folders) and a copy of the Retail software development kit (SDK) in **RetailSdk** folders [5, 6, 7]. The Retail SDK includes base Microsoft code and code extensions. This base code and the code extensions can differ in each branch.
- The **RetailSdk-mirror** folder [4] is used to bring in Microsoft changes to the Retail SDK. It isn't used for development or build purposes. It should be updated only when a new version or hotfix is used. The exact process is described in detail in [Dynamics 365 for Finance and Operations hotfix and deployment cheat sheet](https://dynamicsnotes.com/dynamics-365-for-finance-and-operations-hotfix-and-deployment-cheat-sheet/).

For small Retail projects, it's acceptable to have only two branches (Main = Dev branch). However, developers must be more disciplined, as any code submissions could immediately affect the quality of test builds. 

You can build deployable packages out of multiple branches. In this case, you must have one build definition for each branch that can be built. The initial build definition is automatically created when a build environment is deployed (Main branch). You can make copies of the build for other branches. Note that you must make small additions to incorporate the Retail code.

The following high-level steps are used to set up an environment so that development work can begin. For details about the numbers in brackets, see the previous illustration and the related information.

1. Deploy a build environment and an empty Main branch in Microsoft Visual Studio Team Services (VSTS) [1].
2. Deploy a development environment.
3. Create the Dev branch and the release branch (for example, ProdRel1 in the previous illustration) [2, 3].
4. Add the Retail SDK [4–7].
5. Prepare the development environment.
6. Optional: Deploy a second build environment for a different release branch.
7. Prepare the build definitions.

After you've completed all these steps, your branches, environment, and builds will be ready.

The following sections explain each step in detail.

## Deploy a build environment and an empty Main branch in VSTS

Use the LCS portal to deploy a new build environment. We recommend that you use a cloud-hosted environment, because you will have more options and capabilities if you have administrative rights. See the table about the various environment hosting models in the "Development Tier 1 environments" section, earlier in this topic.

Unless you have already done so before, start with creating a new VSTS project. In your VSTS account, click **New project**.

[![VSTS project](./media/2-VSTS-project.png)](/media/2-VSTS-project.png)

After the new VSTS project is created, you must allow VSTS to access it. First create a new personal access token on the VSTS account. Then configure the LCS project with the correct URL and Personal access token.

[![LCS project](./media/3-LCS-project.png)](/media/3-LCS-project.png)

After the LCS project is linked to VSTS, you're ready to deploy.

Add a new environment, select the version, select **DEVTEST** as the topology, and select a build environment. On the next page, enter a meaningful name for the environment. Then enter a similar name for the build agent.

[![Build agent](./media/4-build-agent.png)](/media/4-build-agent.png)

Next, under **Customize virtual machine names**, enter a unique name, and then deploy.

The build box is deployed, and the build definition and Main branch are created. This process might take a couple of hours.

[![Build box main branch](./media/5-build-box-main-branch.png)](/media/5-build-box-main-branch.png)

[![Build definitions](./media/19-build-definitions.png)](/media/19-build-definitions.png)

[![Agents for the Default pool](./media/20-agents-for-pool-default.png)](/media/20-agents-for-pool-default.png)

## Deploy a development environment

Use the LCS portal of your implementation project to create a cloud-hosted development environment. Make sure that you're signed in to the correct user account. This user account is used to create the tenant of the development machine. For example, if you're signed in to LCS as `lily@pad.com`, the environment is set up for the @pad.com tenant and expects users from that tenant. Although other users can be added, the POS activation must be done by a user from that tenant. In some cases, user accounts from different domains can be used, such as when customers, partners, or other parties use email accounts from different domains. In these cases, coordination is required during the POS activation, because only the tenant that was used during deployment can activate users.

Select the correct version, select **DEVTEST**, and then select **DEV**. Enter a meaningful and unique name, and make sure that the machine name is also unique in the advanced settings. The process of preparing the machine might take a couple of hours.

Because there is currently no Dev branch, you can skip the process for mapping VSTS to the local directories. However, you will have to complete that process later.

## Create the Dev and release branches

As mentioned earlier, you must have a branch that holds changes that are often made but less often tested. You must also have a branch that holds the source code for production. The following illustration shows the expected hierarchy.

[![Main branch hierarchy](./media/6-main-branch-hierarchy.png)](/media/6-main-branch-hierarchy.png)

Follow these steps to create the branches.

1. Sign in to a development environment.
2. Start Microsoft Visual Studio as an administrator, and make sure that you signed in by using an account that has access to the VSTS project.
3. In Team Explorer, connect Visual Studio to the VSTS project (if this connection doesn't already exist).
4. Map the Trunk/Main folder to a local folder (if this mapping doesn't already exist). This mapping is temporary.
5. In Source Control Explorer, right-click the **Main** folder, and then select **Branching and Merging** \> **Convert to Branch**.
6. Right-click the **Main** branch, select **Branching and Merging** \> **Branch**, and name the new branch **Dev**.
7. Use **Pending Changes**, and submit this change to VSTS.
8. Right-click the **Main branch**, select **Branching and Merging** \> **Branch**, and name the new branch **ProdRel1**.
9. Use **Pending Changes**, and submit this change to VSTS.

At this point, Source Depot Explorer in Visual Studio should resemble the following illustration.

[![Source Depot Explorer](./media/7-source-depot-explorer.png)](/media/7-source-depot-explorer.png)

## Add the Retail SDK

Next, you must add the Retail SDK to each of the three code branches, so that code changes can be propagated from Dev to Main and eventually to ProdRel1. This step also enables separate changes between these branches, as for the X++ code. Therefore, we will have the Retail SDK in every branch, together with the X++ code. 

First, add the mirror branch. The Retail SDK mirror branch is required as a baseline for code merges when updates from Microsoft are imported. The process for taking updates will be explained later in this topic. First, we need to create the mirror branch.

The mirror branch or folder is only required one time per project.

1. Find the unchanged Retail SDK that has the exact version you want to start your development with. This Retail SDK can be found on every development machine on the service drive, or in every downloaded hotfix. You can uniquely identify a version of the Retail SDK by inspecting the Microsoft-version.txt file. This file should not be changed, except by an update to the Retail SDK mirror folder.

    [![Retail SDK](./media/8-retail-sdk.png)](/media/8-retail-sdk.png)

2. In Source Control Explorer, right-click the **Trunk** folder, and then select **Add Items to Folder**.
2. Select the top folder in the Retail SDK, and then click **Next**.
3. Visual Studio shows the number of files that will be added. Make sure that the **RetailSdk** folder is under the **Trunk** folder.
4. Make sure that there are 0 (zero) excluded items by selecting items and then clicking **Include items**.

    [![Source control](./media/9-source-control.png)](/media/9-source-control.png)

5. Click **Finish**. This process will take a few minutes.
6. When the process is completed, rename the folder **RetailSdk-mirror**.

Next, you must branch to each branch. Follow the same path that the code changes will flow in: first to Dev, then the Main, and then to ProdRel1.

1. Select the folder for the mirror branch, right-click, and then select **Branching and Merging** \> **Branch**.
2. Go to the **Dev** branch, append **/RetailSdk** to the name, and then click **OK**.

    [![Branch change](./media/10-branch-change.png)](/media/10-branch-change.png).

3. Use **Pending Changes**, and submit the changes.
4. Follow the same steps to branch the **RetailSdk** folder of the **Dev** branch to the **Main** branch.
5. Follow the same steps to branch the **RetailSdk** folder of the **Main** branch to the **ProdRel1** branch.

At this point we have the code branches and code locations for X++ and Retail extensions setup. In Source Control Explorer, the file structure should resemble the following illustration.

[![Source Control Explorer](./media/11-source-control-explorer.png)](/media/11-source-control-explorer.png)

You should also change the version of the Retail customization. This version should be different in the Dev, Main, and ProdRel1 branches. Change either the Customization.settings file, or add a new global.props file in the **RetailSdk**\\BuildTools** folder. For example, you can number Dev as 1.0.0.x, Main as 1.0.1.x, and ProdRel1 as 1.0.2.x.

## Prepare the development environment

You can now prepare the development environment for Retail development tasks. The development environment will map the code locations for both X++ and the Retail SDK in the Dev branch to local folders. The Metadata folder (X++) must be always mapped to the PackagesLocalDirectory folder. The location of the RetailSdk folder must follow these guidelines:

- The location should be somewhere inside the local user's folder.
- The file path of any file should have no more than 256 characters. Therefore, use a short path for the root of the Retail Sdk. For example, you can use **c:\\users\\\<user name\>\\Source\\RetailSdk**.

To map the X++ and Retail SDK, you must edit the current workspace. Click **Pending Changes** \> **Actions** \> **Workspaces**, and update the current workspace so that it resembles the following illustration. As mentioned above, map the Metadata folder of the branch to the PackagesLocalDirectory and the RetailSdk to a short folder of your choice.

[![Edit current workspace](./media/12-edit-current-workspace.png)](/media/12-edit-current-workspace.png)

The actual download of the files can take a few minutes.

Regardless of whether there are customizations in the code branches, the following steps help bring a development box into a state where Retail extension code can be authored and executed. Some steps might be optional, depending on the customizations that are planned.

1. Install your favorite development tools. For information about one automated script, see [Auto-Installing most needed dev tools in 5 mins with Chocolatey](https://dynamicsnotes.com/auto-installing-most-needed-dev-tools-in-5-mins/).
2. To help reduce the compile time, exclude the code folders from Microsoft Windows Defender.
3. If there is already code in the Dev/Metadata folder, build all Retail models. Select all the models, and then click **Database sync**.
4. To speed up the development experience, switch to Microsoft Internet Information Services (IIS). For instructions, see [MSDyn365FO. How to switch from IIS Express to IIS on development VM.](https://ievgensaxblog.wordpress.com/2018/04/02/msdyn365fo-how-to-switch-from-iis-express-to-iis-on-development-vm/). This step can be done only on the Tier 1 VM where you have administrative privileges (cloud-hosted environment).
5. Optional: Restore a recent copy of a production database that has good data.

    1. Rename the existing database **AxDB_Orig**.
    2. In Microsoft SQL Server Management Studio, restore the .bak file. (If a .bacpac file exists, follow the steps in [topic](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/database/copy-database-from-azure-sql-to-sql-server).)
    3. In Visual Studio, refresh the model store.
    4. In Visual Studio, do a full build if the source and destination environments of the database are on different versions.
    5. In Visual Studio, run a full database synchronization.
    6. Make sure that the Batch service is running.
    7. Run the Environment reprovisioning tool (Find the latest version in the LCS Asset library, and deploy it by using the **Maintain** function.)
    8. Verify that the tool succeeded. The following query should show the URLs of all local dev machines that were updated:

    ```
    select * from dbo.RETAILCHANNELPROFILEPROPERTY where ISSYSTEMRECORD = 1
    ```

    9. In Retail, run the **Initialize Retail Scheduler** job to delete old data.

6. Make sure that you now can sign in to Dynamics 365 for Retail by using your user account. If you weren't the original Admin user in the production database, you can run the Admin Provisioning tool to take ownership. (This tool is in the PackagesLocalDirectory/bin folder.)
7. Verify that the CDX data synchronization works. In Retail, go to **Download sessions**. You should see many applied sessions. If you don't see them, select job **9999**, and run it.
8. Install TypeScript version 2.2.2 from <https://www.microsoft.com/en-us/download/details.aspx?id=48593>.
9. Do a full build of the Retail SDK from a command prompt.

    1. Open an MSbuild command prompt for Microsoft Visual Studio 2015 as an administrator.
    2. Change the directory to the location of your Retail SDK on the local VM.
    3. Type **msbuild**, and then press Enter. The build should succeed.

10. Add the development/sample Retail Modern POS (MPOS) certificate to the local machine's trusted root certificate store: **...\\RetailSDK\\BuildTools\\ModernPOSAppxSigningCert-Contoso.pfx**. Set the password to an empty string.
11. Install MPOS or MPOSOffline by executing the installer at **...\\RetailSDK \\References\\YourCompany|Contoso.ModernPOSSetupOffline.exe**. This step is required once in order to deploy the ClientBroker files.
12. In Visual Studio, open **ModernPOS.sln** (as an administrator), and do a full rebuild.
13. Press F5 to start MPOS in the debugger.
14. In Finance and Operations, open the **Channel profiles** page, and copy the Retail Server URL for the default channel profile.
15. Open a browser window, and paste the URL into the address bar. You should be able to browse to your local Retail Server.
16. In Finance and Operations, add external user credential to any worker (for activation), save the password, and don't allow a password reset on first sign-in.
17. In Finance and Operations, run job **1060** (**AX/Distribution schedule**).
18. Activate Modern POS by using the same Azure Active Directory (Azure AD) user that you added earlier in step 16. Paste the Retail Server URL, select a store and a register and finish the activation.

You should now be able to run MPOS in the debugger from your local sources. This concludes the preparation of a development environment. At this point, any extension code (X++, CRT, RetailServer, Channel SQL, POS, etc.) can be authored, debugged, tested and submitted to VSTS.

## Optional: Deploy a second build environment for a different release branch

If you have to maintain multiple releases at the same time, you must create deployable packages from different code branches (for example Main2 or Main3, and/or ProdRel1 or ProdRel2).

The steps to set up a second build environment are the same as the steps for the first build environment. At this point, a VSTS project and the link between the LCS project and the VSTS project already exist.

To separate the build environments, we recommend that you create a new VSTS agent queue for the release branch. Although there are ways to share an agent queue (and its build environment) for multiple branches, it can be tricky.

Currently, the build environment must be on the same platform and binary hotfix version as the target environment during deployment. Otherwise, LCS may reject  the deployable package because of version incompatibility.

First, you must create a new VSTS agent queue.

[![VSTS agent queue](./media/13-VSTS-agent-queue.png)](/media/13-VSTS-agent-queue.png)

When you deploy from LCS, use **PRODREL1** as the name of the agent pool.

[![Queue name in LCS](./media/14-queue-name-lcs.png)](/media/14-queue-name-lcs.png)

Next, on the **Customize virtual machine names** tab, enter a unique name, and then deploy.

The process of deploying a new build and creating a new agent queue can take a couple of hours.

[![New agent queue](./media/15-new-agent-queue.png)](/media/15-new-agent-queue.png)

## Prepare the build definitions

After following the steps earlier in this topic, you should have one build definition and two agent queues, each of which has one agent. To build different branches, you must configure the build definition differently. Therefore, you must clone the build definition.

However, before you clone the build definition, you must add the Retail SDK into the build, so that you don't have to complete this step twice. To edit the existing build definition (which is named "Unified Operations platform - Build Main"), follow the steps in [Integrate the Retail SDK with the continuous build system (VSTS)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/retail-sdk/integrate-retail-sdk-continuous-build) to integrate the Retail SDK into the metadata build of the Main branch.

If you had multiple build branches and environments, just clone the build definition, and name the new build definition so that it's clear which branch it's for. (The clone feature is available in the VSTS portal). Select the new agent queue that you created, and change the following paths in any build steps or source mappings (in the paths, change **Main** to **ProdRel1**):

- Source mappings
- Retail SDK build step
- Retail SDK copy binaries step
- Build the solution step (X++ build)
- Retail SDK copy packages step

## Tips

- You can speed up an official build by making these changes in the **Variables** section of the build definition:

    - Set **DeployReports** to **0**.
    - Set **SkipSourcePackageGeneration** to **1**.

- Change the version of the Retail customization in each branch. The version should be different in the Dev, Main, and ProdRel1 branches. Either change the Customization.settings file or add a new global.props file under the RetailSdk\\BuildTools folder. You can use any kind of numbering for the file name. For example, you can number Dev as 1.0.0.x, Main as 1.0.1.x, and ProdRel1 as 1.0.2.x.
- For efficiency, shut down build or dev environments when they aren't being used.
- If you're using cloud-hosted Tier 1 development environments (where you have administrative privileges), you can switch from IIS Express to IIS. Using IIS for running all web application is more robust, more performant and avoids the switching. For details, see [MSDyn365FO. How to switch from IIS Express to IIS on development VM](https://ievgensaxblog.wordpress.com/2018/04/02/msdyn365fo-how-to-switch-from-iis-express-to-iis-on-development-vm/).
- For prototyping purposes, a developer might want to change the Retail SDK on a development VM without using VSTS source control. Always keep the original Retail SDK untouched, and make a copy that you can work in temporarily. In that way, you can take the unchanged Retail SDK into your mirror branch later, if it's required.
- Currently, a build environment must be on the same platform and binary hotfix version as the target environment.

## Additional resources

[Update code and environments for Retail projects](./updating-environments.md)

[Testing and performance](./retail-implementation-testing-performance.md)


