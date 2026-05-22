---
title: Update code and environments for Commerce projects
description: Learn about recommended practices for updating code and environments for Microsoft Dynamics 365 Commerce implementation projects.
author: andreashofmann1
ms.date: 02/20/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: andreash
ms.search.validFrom: 2017-12-31
ms.custom:
  - bap-template
  - sfi-image-nochange
---
# Update code and environments for Commerce projects

[!include [banner](../../includes/banner.md)]

This article explains recommended practices for updating code and environments for Microsoft Dynamics 365 Commerce implementation projects.

You can update an environment by updating either its data or its code.

You can update the data in many ways. For examples that show how to get data into an environment, see [Integration between finance and operations apps and partner services](/dynamics365/fin-ops-core/dev-itpro/data-entities/integration-overview).

When you update an environment, consider moving the whole database. This approach lets you quickly and easily duplicate the data from one environment to another.

Other updates are code updates. The environment page in Microsoft Dynamics Lifecycle Services (LCS) tracks the updates that you applied and the updates that you must apply. The following illustration shows an environment that has 79 outstanding X++ fixes, 14 outstanding binary updates, and nine outstanding platform binary updates.

:::image type="content" source="./media/17-LCS-environment-page.png" alt-text="Screenshot of the LCS environment page.":::

Platform code is at a low level, and no Microsoft Dynamics 365 Commerce features are implemented in the platform. Therefore, stand-alone platform binary updates don't require that you retest any Commerce-specific code. Examples of features that the platform implements are the Data Import/Export Framework (DIXF) and the batch framework.

Binary updates or hotfixes include dynamic-link libraries (DLLs), scripts, and channel SQL schema changes. All channel-side hotfixes are released together as a binary update or hotfix. Because binary updates are DLLs, they're cumulative. For example, if you download a binary update on Friday, you automatically receive all binary hotfixes from Monday through Thursday.

If you do the code merge correctly, the version of a binary hotfix that you take matches the version of the Microsoft-version.txt file in the Retail software development kit (SDK). Typically, binary updates are also linked to the latest platform. Therefore, when you take binary updates, you must stay up to date with the platform. Platform updates help increase the stability of the platform, and they affect build environments and test efforts to some extent.

Application updates or hotfixes are delivered in X++ source code. Therefore, they're not for the channel but for the Microsoft Dynamics 365 side. They're either Commerce-related or not Commerce-related.

Some updates require both an application update and a binary update. For hotfix recommendations, see the next section.

Partner packages resemble application packages, but other developers create them. For more information about how to use independent software vendor (ISV) packages, see [Manage Runtime Packages](../../fin-ops-core/dev-itpro/dev-tools/manage-runtime-packages.md).

## Updating data by restoring the database

A common and useful operation is moving the whole database from one environment to another. For example, you might move the production database to development environments when you're preparing to develop more features. Alternatively, you might move the golden setup database to the production database as part of the go-live process.

For more information, see [Copy Database From Azure SQL to SQL Server](/dynamics365/fin-ops-core/dev-itpro/database/dbmovement-operations). If the source and destination environments don't have the same binary version, you should also do either a build and a database synchronization (for a development environment), or a deployment (for a sandbox or production environment).

Every time you restore a database moved from a different environment, you can break specific links in the database. The Environment reprovisioning tool fixes all these broken links for the default database group, regardless of the type of environment. If the database comes from a different environment, run the Environment reprovisioning tool.

In many cases, you should reset the Commerce scheduler after you update the database.

After you restore the database, follow these steps:

1. Either do a build and a database synchronization, or deploy the deployable package.

    > [!NOTE]
    > If you have table extensions that include data, you must have the metadata for those extensions in the environment. Otherwise, you can lose data, because columns and tables might be dropped.

1. Make sure that the batch service is running.
1. Run the Environment reprovisioning tool. (Find the latest version in the global Shared asset library in LCS, and then deploy it by using the **Maintain** function.)
1. Verify that the tool succeeded, the Commerce channel profile is up to date with the correct URLs, and the data synchronization jobs for the Default data group succeeded.
1. In Commerce, run the **Initialize Commerce scheduler** job (select to delete old data). This step assumes that all Commerce Data Exchange (CDX) configuration changes are automated by using a resource file. If CDX configuration changes aren't automated, and if tables, subjobs, and jobs are manually created in the Commerce channel schema, don't select the option to delete the existing configuration. Automate CDX configuration changes. 

## Taking updates frequently

If your project is more than a few weeks away from go-live or the final user acceptance testing (UAT), take all hotfixes (binary, X++, and platform) on a regular schedule. Specifically, take all hotfixes once per month. The more often you perform this task, the fewer problems you should experience, because the code churn of the hotfixes is smaller. If you perform this task often, it takes less than eight hours.

Don't pick and choose hotfixes because this approach is more likely to cause errors and probably isn't worth your time. If you have 500 or 1,000 outstanding hotfixes, consider whether you're ready to go-live. The quality of the product is higher if the count on the update tiles in LCS is low (fewer than 100 application fixes and fewer than 10 binary fixes).

After you take new hotfixes, the results of a previous round of UAT become less meaningful. Therefore, it's crucial to retest. The number of files that changed determines how extensive the testing must be. If you frequently take hotfixes, especially during the implementation phase, the number of new files isn't large, and the retesting effort is manageable.

Another approach is to take all hotfixes frequently and run only part of the UAT. Then, the next time that you take new hotfixes, run a different part of the UAT. Run the different parts of the UAT in a circular manner. Before go-live, you should do a full UAT run.

## The flow of code changes through branches and environments

Just as project, team, or other constraints determine the branching strategy, your project has flexibility about how the changes propagate through the branches. The following illustration shows an example of the process. However, this example might be too simple for some projects and too complex for other projects. The important point is that a project should have a plan. Different persons on the team have different responsibilities (development, deployment, code merges, sign out, and so on), and the role ownership should be clearly defined.

:::image type="content" source="./media/1-1-diagram.png" alt-text="Screenshot of the branch diagram.":::

### Steps 1–3: Obtain and apply updates

If you set up the branches in the same manner as the preceding illustration, do this work in the Dev branch.

### Steps 3.1–3.2: Keep development environments up to date

You don't need a build environment for the Dev branch. In fact, you usually don't need a build environment for the Dev branch. You just need to coordinate the packages that you deploy to keep the version correct.

After you download binary updates and platform updates, you can deploy them through LCS package deployment.

For the X++ code, developers just synchronize the Metadata folder and do a full build and database synchronization.

If other team members check in major new changes (for example, new files, configuration changes, or a new Retail SDK), synchronizing and building the new files isn't enough. A few web applications that are installed on the developer machine aren't updated through a compilation. You must deploy those web applications. Use LCS package deployment to deploy the commerce package that can be produced at an MSBuild command prompt. For smaller code changes, new package deployments aren't required to keep the dev environments in sync if the incremental changes are dropped to the install locations. 

:::image type="content" source="./media/1-2-environment-change-history.png" alt-text="Screenshot of the environment change history.":::

### Step 4: Move changes from the Dev branch to the Main branch

In this example, the Dev and Main branches are separated to provide an opportunity to "leave some unwanted changes behind." Although this approach isn't required, it's a good option to have. Microsoft Visual Studio makes the process of moving the code from Dev to Main easy. You can select a range of changes, select all or individual changes, and merge those changes. To keep the process simple, you can have some type of a code freeze in the Dev branch. Then, when you're satisfied with the quality, you can merge all changes. There's no reason to treat X++ differently than the Retail SDK. They reside next together in each branch, because they're dependent on each other.

### Steps 4.1–4.2: Update test environments

Use your build environment to produce officially built packages from the code in the Main branch.

:::image type="content" source="./media/1-3-build-definition-unified-operations.png" alt-text="Screenshot of Build Definitions Unified Operations.":::

When the build finishes, find the packages that the process built. Download and rename them according to your naming conventions.

:::image type="content" source="./media/1-4-artifacts-explorer.png" alt-text="Screenshot of the Artifacts Explorer.":::

Upload the packages to the LCS Asset library.

:::image type="content" source="./media/1-5-asset-library.png" alt-text="Screenshot of the Asset library.":::

Finally, deploy the packages to your test environments.

:::image type="content" source="./media/1-6-environment-change-history-UAT.png" alt-text="Screenshot of the environment change history for UAT.":::

### Step 4.3: Deploy packages to the production environment

When all the required tests pass, you're ready to deploy the same packages to production. After you deploy and validate the packages in a Tier 2 or higher environment, you must mark them as Release Candidates in the LCS Asset library. You must then plan the deployment and submit it via the LCS environment page.

Many considerations exist when you update a production environment, such as downtime, downtime mitigation, data migration, store updates, and mass deployment. It's important that you have a plan of all the steps that are required for an update, because Commerce projects usually require more than just deployment. For some more considerations, see the "Tips" section of this article.

It's assumed that the planning for go-live was started earlier. For more information, see [Implementation lifecycle](../../fin-ops-core/fin-ops/imp-lifecycle/implementation-lifecycle.md).

### Step 5: Merge the code from the Main branch to the ProdRel1 branch

Immediately after deployment to production, and before you add any new feature work to the Main branch, take a snapshot and move it to the ProdRel1 branch. The steps are the same as in step 4. You don't have to select individual changes. Instead, just merge all changes up to the last code change set that you submitted to the Main branch.

## Update build environments

Always deploy binary updates and platform updates by using LCS package deployment.

Don't deploy Finance and Commerce customization packages to a build environment.

:::image type="content" source="./media/1-7-environment-change-history-build.png" alt-text="Screenshot of the environment change history for build.":::

## Compare LCS tile counts

Environments that you use for work on the same release should have the same LCS tile counts. Here are some reasons why the tile counts might differ:

- You didn't deploy and apply the same deployable packages. You can troubleshoot this problem by inspecting and comparing the LCS deployment history.
- The scheduled task that collects the version information from an environment didn't run yet. For development environments, you can force the "LCSDiagnosticsCollector" schedule task to run.
- The counts for the build environment's application updates don't match because X++ packages aren't deployed on build environments. Binary and platform counts are correct.
- The difference is intentional. For example, a developer works with the next version, whereas the rest of the team is still working with a different release. Alternatively, one development environment is kept on an older version in case a production hotfix must be developed, and that production environment uses an older version than current development environments.

After you finish updating an environment, the tile counts for the available updates are lower than they were when you started.

## Move to a new version

To upgrade to a new version (such as 7.2 to 7.3 or 7.3 to 8.0), you must deploy a new environment. You must also run a code upgrade and a database upgrade, if these upgrades are applicable. For more information, see [Code migration home page](../../fin-ops-core/dev-itpro/migration-upgrade/code-migration-home-page.md).

## Tips

- Decide on a good package naming convention for names in the LCS Asset library and for the names of zip packages that you download. In this way, you can more easily determine what package you deployed and where it came from. Avoid spaces in package names. Here are examples of naming conventions:

    - **Platform update packages:** PUXX_MMDDYY, where XX is the number of the platform update
    - **Binary update packages:** BIN_MMDDYY
    - **X++ update packages:** APP_MMDDYY
    - **Built X++ deployable packages:** AX_BRANCH_VERSION, where BRANCH is an appropriate branch name, and VERSION is the Microsoft Azure DevOps version string
    - **Built Retail combined package:** RET_BRANCH_VERSION, where BRANCH is an appropriate branch name, and VERSION is the Azure DevOps version string

- Whenever you start a new item of work, use the **Get latest** option in the Visual Studio source code explorer.
- Use correct and detailed comments that describe the change sets for any code submissions.
- Production go-live procedures are important. Consider including the following items on your go-live checklist. Verify your go-live checklist in a mock go-live or UAT environment. This list isn't exhaustive.

    - After deployment, does LCS show the expected deployment history together with the correct package names?
    - After deployment, do the LCS environment page and Commerce show the correct and expected version numbers?
    - Can Store Commerce app offline mode be used during downtime of Commerce? Package deployments cause downtime. If Store Commerce app offline mode can be used, did you test the procedure? To test the procedure, go offline, deploy, go online, synchronize offline transactions, and update the Store Commerce app.
    - Does the Environment reprovisioning tool have to be run if a database was moved?
    - You must reenable batch jobs for CDX synchronization by setting them to **Waiting**.
    - The "Initialize Commerce scheduler" job should be run.
    - Does other data have to be set up in addition to the deployable packages (for example, screens, buttons, receipt layouts, the Microsoft Entra ID setup, Commerce shared parameters, the tax configuration, other batch processes, and DIXF recurring jobs)?
    - Is a synchronization of the CDX data jobs required?
    - Is a full synchronization of CDX data jobs required?
    - Does a deployment require that store components also be updated?
    - If the store components had to be updated, do they show the new version numbers?
    - Are the correct experts available during the deployment (for example, partners, ISVs, and customers)?

## Additional resources

[Set up new environments, Azure DevOps, and branches for Commerce projects](./new-environments-visual-studio-teams-branch-retail-projects.md)

[Testing and performance issues](./retail-implementation-testing-performance.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
