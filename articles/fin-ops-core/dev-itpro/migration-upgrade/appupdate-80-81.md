---
title: Update environments from version 8.0 to 10.0.X
description: Learn about the steps required to update existing finance and operations 8.0 environments to 10.0.X application releases.
author: laneswenka
ms.author: laswenka
ms.topic: how-to
ms.date: 03/17/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-10-31
ms.search.form: 
ms.dyn365.ops.version: 10.0.0
---

# Update environments from version 8.0 to 10.0.X

[!include [banner](../includes/banner.md)]

This article explains the steps required to update existing finance and operations 8.0 environments to 10.0.X application releases.

## Background

Traditionally, moving to a newer application version involves a rigorous upgrade that includes deployment of additional virtual machines, code upgrade, data upgrade, and scheduling several days in advance with the Microsoft Dynamics Service Engineering (DSE) team. You notice that Microsoft is making the uptake of the latest version simpler, and this experience continues to improve over time.

> [!NOTE]
> Microsoft supports an update experience as compared to a full upgrade. This support is possible because there are **no Data Upgrade or Code Upgrade** steps between the 8.0 and 10.0.X application schema. The update process updates the target environments just like you apply a platform update.

The high-level process to update from version 8.0 to 10.0.X includes the following steps:

1. Deploy 10.0.X developer and build environments.
1. Branch in version control and remove any application hotfixes.
1. Recompile custom extensions and ISV solutions.
1. Produce a single software deployable package.
1. Merge a deployable package with the 10.0.X binary update package.
1. Deploy to target environments for validation.
1. Deploy to production.

## Deploy 10.0.X developer and build environments
By using Lifecycle Services, deploy at least one developer environment and a single, new build environment on application 10.0.X release.

On average, this deployment takes 3-4 hours and you can do it simultaneously. For the build environment, **create a new agent pool** and assign it to this environment on the **Advanced options** screen.

In Azure DevOps, visit your existing Build Definition and ensure that it isn't using your new agent pool for 10.0.X. This configuration step keeps your new build agent from trying to compile older application code.

### Apply the latest binary update to your build and development servers
In Lifecycle Services, go to the **build server** that you deployed in step 1. Using the **Update** tiles at the bottom of the **Environment details** page, get the latest updates and store them in your project's **Asset Library** by using the **Save package** button. For example, you might save the 10.0 Platform update 24 package to the **Asset Library**.

Apply this same package to the build server where you saved the package, and to any new 10.0.X developer environments you deployed.

> [!NOTE]
> Get the latest updates, such as 10.0 Platform update 24, from the **Update** tiles when you deploy your 10.0 Platform update 24 build server. If your tiles show a count of `0` on the build server, you can pull the related package from the shared asset library for your version. If your tiles show a count greater than 0, use that package.

## Begin branch work for version control and remove any application hotfixes
While the new environments are deploying, start the branching work for your update. Use the following branch structure in version control as an example. Branching design varies for each customer, so adjust your steps accordingly based on how your branches are set up.

:::image type="content" source="./media/VersionControl.png" alt-text="Screenshot of the version control branch structure example.":::

### Prepare by using Visual Studio
On any other development machine (other than the new ones being deployed), open Visual Studio and go to the Source Control Explorer. Create a new branch that's isolated for the 10.0.X update.

:::image type="content" source="./media/BranchFor81.png" alt-text="Screenshot of the branch for 8.1 in Visual Studio Source Control Explorer.":::

Next, delete any Microsoft package folders in this branch. You might have packages, such as ApplicationSuite, checked in from applying hotfixes on 8.0 that you need to remove. When only your custom packages or ISVs remain, check these changes in to the branch.

>[!IMPORTANT]
> It's critical to do this step before you map version control workspaces on your new development environments. This step avoids the deletion of the Microsoft hotfixes cascading to your working environment and deleting untouched 10.0.X application code.

## Recompile custom extensions and ISV solutions
Now you're ready to map this branch to a new development environment and compile your extensions and ISV solutions if they provide you with source code. If your ISVs only provide binary packages, you can check them in to source control. The build environment merges the binaries with your extension package to produce a single software deployable package. For more information, see [Deployable packages from third parties](../dev-tools/manage-runtime-packages.md#deployable-packages-from-third-parties). This process helps when you merge your package with the 10.0.X binary update.

> [!NOTE]
> This **step is necessary** because the 10.0.X application code isn't backward compatible with 8.0 from a binary level. In future application releases, this step is optional.

## Produce a single software deployable package
After you compile in a developer environment and resolve all errors, start a build in Azure DevOps by using your new 10.0.X build environment agent. When the build finishes, it attaches a deployable package artifact to your build results. Download this package and upload it to the Lifecycle Services Asset Library. This single package should include all your extensions and ISV solutions.

## Merge the deployable package with the 10.0.X binary update package
In your project's **Asset Library**, locate both your new 10.0.X software deployable package (your customization package that includes your ISVs) and the 10.0-X PU2X binary update package that you saved in Step 1 at the beginning of the article. Select both packages and choose **Merge**. This action combines the files into a merged update package. You can now apply this package to your various test environments.

> [!NOTE]
> You can't move this merged package between different Lifecycle Services projects. The merge operation references other packages in your Asset library, and those packages aren't available in a different project.

## Deploy to target environments for validation
Use the merged update package to deploy to your various test environments. For more information, see [Apply updates to cloud environments](../deployment/apply-deployable-package-system.md). You can deploy this merged update package to your Tier-1/OneBox environments as well as Tier-2 sandboxes. At a minimum, you must deploy this package to the sandbox Tier-2 environment that comes with your subscription. After you finish validation, mark the merged update package as a release candidate.

## Deploy to production
After you mark the release candidate in your Asset Library, you can schedule the deployment to your production environment. This process follows the same steps as applying other software deployable packages.

## Known issues

### GlobalUpdate script for service model: AOSService with error 'The specified module 'C:\Program Files\Microsoft Security Client\MpProvider' 
This error is transient and you can ignore it. To bypass the error, select the **Resume** button in Lifecycle Services.

### Deploying the 10.0.X binary update to developer environments causes ApplicationSuite compilation errors
You can apply this package to your 8.0 environments to update your source code. It shouldn't affect compiling your extension packages. If you used overlayering and removed objects from the ApplicationSuite package, you might encounter errors when you try to recompile it. To resolve this problem, redeploy your developer environments on 10.0.X and sync your source code from version control.

### Can't find 10.0.X binary update package on the All Binary Updates tile on the My environment details page
This article originally stated that you can find the package on the **All Binary Updates** tile. To prevent customers who want to get the latest binaries for release 8.0 from accidentally updating to release 10.0.X, Microsoft moved the binary package to the Shared Asset Library. This article reflects that change.

### Deployment of my environment fails with error on duplicate objects
By default, in Visual Studio when you extend an object, you create it with a name of `Object.Extension1`. This name could clash if Microsoft introduces new extensions of the same object. If this name clash occurs, your deployment fails with an error similar to the following error message:

```Console
Exception calling "CreateRuntimeProvider" with "1" argument(s): "Runtime metadata is invalid because the same metadata artifact has been defined in multiple assemblies. \nFirst 10 conflicting names: SystemAdministration.Extension1. \nSee metadata events for complete list."
```

To prevent this problem, compile your extensions on a 10.0.X developer machine. To resolve this problem, rename any of your extension objects by using a vanity extension naming convention, such as `SystemAdministration.Customer`.

### Deployment on my environment fails with error on DVTs or ETWs
There's a known problem where IIS and application pools don't fully restart when the DVT or ETW step runs. The failure happens because the DVTs try to connect to your environment's URL. To resolve this problem, select **Resume** on your deployment in LCS to retry the step.  The product team is working to add a timer and automatic retry to resolve this problem.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
