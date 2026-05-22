---
title: Manage finance and operations updates and your custom code lifecycle
description: Learn about how to manage finance and operations updates and your custom code lifecycle, including overviews on various environments.
author: josaw1
ms.author: josaw
ms.topic: how-to
ms.date: 03/17/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2020-10-22
ms.dyn365.ops.version: Platform update 10
---


# Manage finance and operations updates and your custom code lifecycle

This article describes application lifecycle use cases for finance and operations implementations. It's focused on the following scenarios:

+ Managing your source code development branches
+ Applying the next version of a Microsoft service update
+ Applying a new version of your custom code

This article applies to Microsoft Dynamics 365 Finance, Dynamics 365 Supply Chain Management, Dynamics 365 Human Resources, Dynamics 365 Commerce, and Dynamics 365 Project Operations.

The main goal is to show how to complete the following tasks:

+ Stay up to date and manage Microsoft service updates (or quality updates) for finance and operations apps (including Dynamics 365 Commerce) in incremental phases, independently of the lifecycle of your own customization. This approach simplifies the update process, and reduces the cost and risk of regressions that are associated with all-in-one upgrade projects.
+ Take advantage of source code branches for version control of your custom code. By using version control, you can isolate the rollout of critical changes and hotfixes from the development of new features and capabilities.

This article doesn't explain how to use the different tools in Azure DevOps and Microsoft Dynamics Lifecycle Services (LCS). Instead, it's focused on processes and best practices. The [Apply the next version of a Microsoft service update](#apply-next-update) and [Apply a new version of your custom code](#apply-new-custom-code) sections contain both an overview of the phases and the steps of the process.

This article includes the following sections:

+ [Environments](#environments)

    + [Environments that run your current release](#current-environments)
    + [Environments that run the next version of your custom code](#next-environments)

+ [Manage source code branches](#manage-source-code-branches)
+ [Apply the next version of a Microsoft service update](#apply-next-update)

    + [Backward compatibility of Microsoft updates](#compatibility)

        + [Runtime compatibility](#runtime-compatibility)
        + [Design-time compatibility](#design-compatibility)

    + [Phase 1: Update the finance and operations implementation](#phase-1)

        + [Track 1: Update your runtime environments](#update-finops-runtime)

            + [Update Test 1](#update-test-1)
            + [Update UAT](#update-uat)
            + [Update Prod](#update-prod)

        + [Track 2: Update your development environments](#update-finops-dev)
        + [Error situations](#error-situations)

            + [Case 1](#case-1)
            + [Case 2](#case-2)
            + [Case 3](#case-3)

    + [Phase 2: Update CSU to version 10.0.11](#phase-2)

        + [Phase 2 prerequisites](#phase2-prerequisites)
        + [Track 1: Update your CSU runtime environments](#update-csu)

            + [Update Test 1](#update-test-1-csu)
            + [Update UAT](#update-uat-csu)
            + [Update Prod](#update-prod-csu)

        + [Track 2: Update your development environments](#update-csu-dev)

    + [Phase 3: Update POS to version 10.0.11](#phase-3)

        + [Phase 3 prerequisites](#phase3-prerequisites)
        + [Update your Commerce development environment](#update-your-commerce-development-environment)
        + [Option 1: Store component updates that include only runtime changes](#store-runtime-only)
        + [Option 2: Store component updates that include runtime and custom changes](#store-runtime-custom)
        + [Update Process](#update-process)

            + [Update Test 1](#update-test-1)
            + [Update UAT](#update-uat)
            + [Update Prod](#update-prod)

+ [Apply a new version of your custom code](#apply-new-custom-code)

    + [Create a hotfix of your code](#create-hotfix)
    + [Update your custom code from release N to release N+1](#update-custom-code)

+ [Upload, update, and deploy store components](#upload-store-components)

## <a id="environments"></a>Environments

This section describes the collection of finance and operations environments that the application lifecycle management (ALM) scenarios in this article rely on. This configuration is typical for organizations that have implementations that rely on custom code (extensions). This custom code includes customizations that independent software vendors (ISVs) provide.

### <a id="current-environments"></a>Environments that run your current release

The following environments run your current release:

+ **Dev 1** – A development environment that runs the same version of finance and operations apps as the production environment. The Dev 1 environment uses Azure DevOps for version control of custom code. It's connected to the current release branch of your custom code. For more information, see the [Manage source code branches](#manage-source-code-branches) section.

    - Many options are available for development environments, both cloud and on-premises. For more information, see [Deploy and access development environments](../dev-tools/access-instances.md).
    - For build automation, use the new Azure DevOps Hosted Agents functionality. For more information, see [Build automation that uses Microsoft-hosted agents and Azure Pipelines](../dev-tools/hosted-build-automation.md).

+ **Test 1** – A Tier-1 test environment that you use for functional and configuration testing. The Test 1 environment runs the same version of finance and operations apps as the production environment. It also runs the latest release version of your custom code extensions.
+ **UAT** – A pre-production environment that you use for user acceptance testing. The UAT environment is a Tier-2 (Standard Acceptance Test) or higher environment. It runs the same version of finance and operations apps as the production environment. It also runs the latest release version of your custom code extensions. You typically connect this environment to a copy of the production database.
+ **Prod** – Your live production environment that runs on your production database.

:::image type="content" source="media/uguide-environments.png" alt-text="Environments that run your current release.":::

### <a id="next-environments"></a>Environments that run the next version of your custom code

The following environments run the next version of your custom code:

- **Dev 2** – A development environment that you use for development of the next version of your custom code extensions. It uses Azure DevOps for version control of custom code. It's connected to the development branch (**main** branch) of your custom code. For more information, see the [Manage source code branches](#manage-source-code-branches) section.
- **Test 2** – A functional test environment that you use for testing of the next version of your custom code extensions.

:::image type="content" source="media/uguide-next-environments.png" alt-text="Environments that run the next version of your custom code.":::

## Manage source code branches

It's important to follow best practices when you manage branches of custom code. By following these practices, you help minimize cost and ensure the quality of your releases and updates.

:::image type="content" source="media/uguide-branches.png" alt-text="Manage source code branches.":::

The **main** branch (development branch) contains the latest functioning version of the next release of your code.

When you work on new features, create a new feature branch from the **main** branch. Then, when you complete the feature work, integrate the feature branch back into the **main** branch.

The release branches contain the code base of your official releases. In the preceding illustration, the assumption is that you have only one release branch, **release/2020-April**. **2020-April** isn't a build. It's a source code branch. Because you probably create hotfixes for your release, you make changes and produce builds from this release branch.

- Don't use release branches to develop new features. Use them only for critical fixes or changes that are required in your live environment.
- After you make a change in a release branch, integrate the branch back into the **main** branch. By using this approach, you ensure that your next release also contains the fix.
- Among the example environments that were described earlier, the Dev 1 environment connects to the **release/2020-April** branch.

When you're ready to release a new version of your custom code, create a new release branch from the **main** branch. For this example, create a new release branch from **main** and name it **2020-July**.

You might have private branches that individual developers work in while they work on a specific work item that's based on a specific branch of your code. Merge private branches back into their parent branch when the work is completed. For more information, see [Learn about branching strategies for Team Foundation Version Control (TFVC) and how to select an effective strategy](/azure/devops/repos/tfvc/branching-strategies-with-tfvc).

## <a id="apply-next-update"></a>Apply the next version of a Microsoft service update

By using a phased approach, you help maximize the efficiency of service updates. Each phase updates one component of your implementation.

1. **Phase 1** – Update your finance and operations environments.

    Your current version of Commerce Scale Unit (CSU) and Point of Sale (POS) works correctly with the new finance and operations update. For example, version 10.0.7 of CSU is compatible with version 10.0.11 of finance and operations apps.

1. **Phase 2** – Update CSU.
1. **Phase 3** – Update POS.

When you take a Microsoft update, you don't need to update your custom code to the next version. By taking Microsoft updates without bundling them with custom code updates, you help simplify the update process. You also help reduce the cost and risk of regressions that are associated with all-in-one upgrade projects.

### <a id="compatibility"></a>Backward compatibility of Microsoft updates

It's important that you understand what Microsoft means by *backward compatibility of service updates*, so that you have context for the next sections of this article. Service and quality updates are *runtime* backward-compatible. However, they're not always *design-time* (*compile-time*) backward-compatible.

#### <a id="runtime-compatibility"></a>Runtime compatibility

All Microsoft updates are intended to be runtime backward-compatible. This compatibility covers both binary compatibility and functional compatibility. Runtime compatibility means that customizations that exist in production and sandbox environments continue to work after Microsoft service updates are deployed to those environments. Those updates include service updates and quality updates. Runtime compatibility also means that Microsoft updates are backward-compatible with customizations that were compiled on an earlier platform.

Binary compatibility is backward only. You can compile a customization on an older application version and platform version, and deploy it to an environment that's running a later version. However, you can't deploy code to an environment that's running a version that is earlier than the version that you compiled on.

> [!IMPORTANT]
> Runtime compatibility covers personalizations, so they continue to work after Microsoft service updates are deployed to these environments. Because of this, reimporting all personalizations after a service update (or at any other time) is unnecessary and highly discouraged.   

#### <a id="design-compatibility"></a>Design-time compatibility

Design-time (compile-time) backward compatibility means that developers can apply updates to their development environments and successfully compile their code without having to make any changes.

Microsoft aims for design-time compatibility. However, some updates might include changes that aren't compatible at design time, but that are binary-compatible. Therefore, after an update is applied, new errors or warnings might occur when you compile your code. Here are some examples of these changes:

+ Microsoft makes an enumeration extensible.
+ Microsoft marks an API as obsolete or internal.
+ Microsoft introduces a new compiler error to help prevent unsafe coding practices.

All these changes might require work on your solution. Design-time breaking changes that are binary-compatible don't require a 12-month deprecation notice. These breaking changes are documented for each service update. For more information, see [What's new and changed in Platform updates](../get-started/whats-new-home-page.md).

### <a id="phase-1"></a>Phase 1: Update the finance and operations implementation

This section summarizes the process that you use to update your finance and operations implementation to the latest service update. An update from version 10.0.7 to version 10.0.11 is used as an example.

This phase is divided into two tracks. These tracks can occur in parallel.

- **Track 1** – Update your runtime environments.
- **Track 2** – Update your development environments.

After you complete track 1, you're live on version 10.0.11, unless you encounter one of the error situations that are described in the [Error situations](#error-situations) section.

#### <a id="update-finops-runtime"></a>Track 1: Update your runtime environments

By completing track 1, you essentially complete your finance and operations update to version 10.0.11, because your production environment is live on version 10.0.11. You don't have to recompile your custom code as part of this track.

##### Update Test 1

The Test 1 environment runs version 10.0.7 together with the latest released version of your custom extension. Although an update of Test 1 isn't a prerequisite in this flow, it's recommended, because it adds another level of functional verification and predictability. Complete this update before you update the UAT environment. The sooner that you update Test 1 and validate on it, the more predictable your "real" update (that is, the update of the UAT and Prod environments) is.

1. Apply version 10.0.11 of finance and operations apps to Test 1.
1. Sign off on functional scenarios. You can use the [Regression Suite Automation Tool](../perf-test/rsat/rsat-overview.md) to automate user acceptance testing on test and UAT environments.
1. If you encounter regressions, see the [Error situations](#error-situations) section.

##### Update UAT

The UAT environment runs version 10.0.7 together with a released version of your custom extension. The UAT environment is the same as the Prod environment.

1. Apply version 10.0.11 of finance and operations apps to UAT.

    You might configure your UAT environment so that Microsoft automatically updates it. However, you can always pull the update as soon as it's available.

1. Complete user acceptance testing, and sign off.
1. If you encounter regressions, see the [Error situations](#error-situations) section.

##### Update Prod

1. Apply version 10.0.11 of finance and operations apps to Prod.

    You might configure your Prod environment so that Microsoft automatically updates it. However, you can always pull the update as soon as it's available.

1. Sign off.

#### <a id="update-finops-dev"></a>Track 2: Update your development environments

The purpose of track 2 is to update the Dev 1 environment to version 10.0.11. Dev 1 is your **main** development environment that is connected to the current release branch of your custom code. It runs version 10.0.7 of finance and operations apps. By completing track 2, you ensure that Dev 1 runs version 10.0.11 together with your latest release, and that it's ready for any future hotfixes that are required for your code.

1. Apply version 10.0.11 of finance and operations apps to Dev 1.
1. Compile your custom code, and run tests.
1. Make any required changes to your custom code.
1. Check code changes into the release branch.
1. If you have more than one development environment, follow these steps for each environment:

    1. Apply version 10.0.11 of finance and operations apps to the development environment.
    1. Sync and compile your latest custom code from the target code branch.

#### Error situations

##### Case 1

During track 1, you find a bug that requires a Microsoft quality update. If Microsoft releases the update in a timely manner, use the new Microsoft update instead of the original service update to complete track 1.

##### Case 2

During track 1, you find a bug that requires a Microsoft service update. However, Microsoft can't release the update in a timely manner.

As a workaround for this issue, Microsoft proposes a change to your custom code.

1. Modify your code in Dev 1 (in the release branch), and test your updates.
1. Check code changes into the release branch.
1. Create a new deployable package from the release branch.
1. Apply the new deployable package to Test 1 and/or UAT.

> [!NOTE]
> You can deploy custom code that is compiled on version 10.0.7 to any runtime environment that's running version 10.0.7 or later. Therefore, you don't need to update Dev 1 to version 10.0.11 yet. However, you might already update Dev 1 as part of track 2.

##### Case 3

During track 1, you find a bug that requires a change to your custom code. This bug might be in either your code or the ISV code.

1. Modify your code in Dev 1 (in the release branch), and test your updates.
2. Check code changes into the release branch.
3. Create a new deployable package from the release branch.
4. Apply the new deployable package to Test 1 and/or UAT.

### <a id="phase-2"></a>Phase 2: Update CSU to version 10.0.11

This section summarizes the process that you use to update your Commerce Scale Units to the latest service update. An update from release 10.0.7 (Commerce version 9.17) to release 10.0.11 (Commerce version 9.21) is used as an example.

#### <a id="phase2-prerequisites"></a>Phase 2 prerequisites

Before you update your CSUs, update the Commerce headquarters environments (in the finance and operations app) to the same release or a later release. For this example, use release 10.0.11.

This phase is divided into two tracks. These tracks can occur in parallel.

- **Track 1** – Update your CSU runtime environments.
- **Track 2** – Update your development environments.

After you complete track 1, you're live on release 10.0.11 (Commerce version 9.21), unless you encounter one of the [error situations](#error-situations) that were described for phase 1.

#### <a id="update-csu"></a>Track 1: Update your CSU runtime environments

When you complete track 1, you complete your CSU update to version 10.0.11. Your production environment is live on version 10.0.11. You don't need to recompile your custom code as part of this track.

##### <a id="update-test-1-csu"></a>Update Test 1

The software as a service (SaaS) components of Commerce aren't currently supported in tier-1 environments (development/test environments). A copy of Retail Server runs locally in each tier-1 environment, and you deploy both Microsoft code for Retail Server and retail customizations through the previous system. You apply application binary packages and retail deployable packages against the infrastructure as a service (IaaS) instance.

###### <a id="update-uat-csu"></a>Update UAT

The UAT environment runs CSU that corresponds to release 10.0.7, together with the same version of your retail extension that the production environment is running.

1. Update the Commerce Scale Unit. Select **9.21 (10.0.11)** as the target version. For more information, see [Phase 2: Update CSU to version 10.0.11](#phase-2).
1. Complete user acceptance testing, and sign off.
1. If you encounter regressions, see the [Error situations](#error-situations) section.

###### <a id="update-prod-csu"></a>Update Prod

1. Update the Commerce Scale Unit. Select **9.21 (10.0.11)** as the target version. For more information, see [Phase 2: Update CSU to version 10.0.11](#phase-2).
1. Sign off.

#### <a id="update-csu-dev"></a>Track 2: Update your development environments

1. Get the latest version of the Retail software development kit (SDK).

    1. Apply the finance and operations service update for release 10.0.11 to Dev 1.
    1. Get the updated version of the Retail SDK from **%ServiceDrive%\\RetailSDK\\Update\\\<newest directory\>**.

1. In your **main** (development) branch, update the Retail artifacts from the new version of the Retail SDK.
1. Compile. The new version should be backward-compatible and shouldn't require any changes to your code.
1. Commit the change that includes the Retail SDK update.
1. Make any required changes to your custom code.
1. Commit code changes to the target branch.
1. Optional: If you have more than one development environment, merge the latest changes from step 4, and compile the latest custom code.

### <a id="phase-3"></a>Phase 3: Update POS to version 10.0.11

This section summarizes the process that you use to update your store components, such as Modern POS (Store Commerce in the newer versions) and Hardware Station, to the latest service update. This section uses an update from release 10.0.7 (Commerce version 9.17) to release 10.0.11 (Commerce version 9.21) as an example.

Unlike updates for Commerce headquarters (in the finance and operations app) and CSU, updates for store components are delivered in the same packages. After you update Commerce headquarters and CSU, you have the following options:

- **Option 0 (no operation is required)** – Leave the store components in their previous release if the version is supported and in-policy.
- **Option 1** – Update the store components runtime (Microsoft code) so that it matches the same release as CSU.
- **Option 2** – Update the store components runtime (Microsoft code) and customization together.

In the rest of this section, the assumption is that you want or need to update the store components (option 1 or option 2).

After you complete this phase, you're live on release 10.0.11 (Commerce version 9.21) for store components, unless you encounter one of the [error situations](#error-situations) that are described for phase 1.

#### <a id="phase3-prerequisites"></a>Phase 3 prerequisites

Phase 3 has the following prerequisites:

- You updated the Commerce headquarters components (in the finance and operations app) to the same release or a later release before you updated the CSUs. In this example, the version is 10.0.11.
- You updated the CSUs to the same release as, or a later release than, the store components. In this example, the release is 10.0.11.

#### Update your Commerce development environment

Follow the steps in the [Track 2: Update your development environments](#update-csu-dev) section.

#### <a id="store-runtime-only"></a>Option 1: Store component updates that include only runtime changes

This option generates a new retail deployable package that contains your store components. It includes changes only from the Microsoft code.

1. Update your release branch, which has the code that is currently used in the production environment, to the Retail SDK that matches your target release. In this example, the version is 10.0.11 (9.21). Follow the steps in the [Track 2: Update your development environments](#update-csu-dev) section.
1. Generate a new build for the retail deployable package. This build contains the same set of customizations that is currently in the production environment, plus version 10.0.11 (9.21) of the Microsoft code.

#### <a id="store-runtime-custom"></a>Option 2: Store component updates that include runtime and custom changes

This option generates a new retail deployable package that contains your store components. It includes changes from both the Microsoft code and customizations.

1. Update your release branch, which has the code that is currently used in the production environment, to the Retail SDK that matches your target release. In this example, the version is 10.0.11 (9.21). Follow the steps in the [Track 2: Update your development environments](#update-csu-dev) section.
1. Commit changes.
1. Update custom code for store components, or update references to ISV-updated components.
1. Generate a new build for the retail deployable package. This build contains updated custom code plus version 10.0.11 (9.21) of the Microsoft code.

#### Update process

##### Update Test 1

The SaaS components of Commerce aren't currently supported in development or test one-box environments. A copy of Retail Server runs locally in each development or test one-box environment, and the deployment of both Microsoft code for Retail Server and retail customizations is done through the previous system, where application binary packages and retail deployable packages are applied against the IaaS instance.

The Test 1 environment runs version 10.0.11 of Commerce headquarters and a local version of CSU from previous phases. An update of Test 1 isn't a prerequisite in this flow. Because there's no CSU in this environment, this step is mostly for verification.

1. Upload, update, and deploy the store components. For more information, see the [Upload, update, and deploy store components](#upload-store-components) section.
1. Sign off on functional scenarios.
1. If you encounter regressions, see the [Error situations](#error-situations) section.

##### Update UAT

Clients that point to the UAT environment run applications (for example, Modern POS) for release 10.0.7 (the same version that is currently running in the production environment).

1. Upload, update, and deploy the store components. For more information, see the [Upload, update, and deploy store components](#upload-store-components) section.
1. Sign off on functional scenarios.
1. If you encounter regressions, see the [Error situations](#error-situations) section.

##### Update Prod

1. Upload, update, and deploy the store components.
1. Sign off.

## <a id="apply-new-custom-code"></a>Apply a new version of your custom code

This section describes the recommended flow for two use cases that require that you update your UAT and production environment with a new build of your custom extension.

### <a id="create-hotfix"></a>Create a hotfix of your code

When you find a critical bug in the UAT or production environment, fix the bug in the release branch (not in the **main** or development branch). Then, use the standard process to apply a deployable package to UAT and production.

:::image type="content" source="media/uguide-hotfix.png" alt-text="Process for a hotfix.":::

1. In Dev 1, make the code fix in the release branch. If the required fix is in ISV code, ask the ISV to send you a new build of the current release, not the next version of the solution.
1. Compile and test.
1. Create a new deployable package from the release branch.
1. Deploy on Test 1, and sign off if sign-off is required.
1. Use the standard process to deploy custom code first to UAT and then to production.
1. Integrate the code fix with your **main** code branch.

### <a id="update-custom-code"></a>Update your custom code from release N to release N+1

When you're ready to release the next version of your custom code, use the following process to create and deploy the new release.

:::image type="content" source="media/uguide-custom-code.png" alt-text="Update custom code from N to N+1":::

1. In the Dev 2 environment, or another environment that is connected to the **main** branch, complete development in the **main** branch.
1. Deploy and test on Test 2.
1. Repeat steps 1 through 2 until you get sign-off on the new version.
1. Create a **new** release branch.
1. Create a new deployable package from the **new** release branch.
1. Use the standard process to deploy custom code first to UAT and then to production.
1. Retire the old release branch.

## <a id="upload-store-components"></a>Upload, update, and deploy store components

1. Upload the retail deployable package to LCS.
1. Update Application Object Server (AOS) with the latest client.
1. Upload the retail deployable package to your Asset library:

    + **Older deployments (earlier than version 10.0.11):** Software deployable package
    + **New deployments (version 10.0.11 and later):** Retail self-service installers

1. Update Commerce headquarters with the new self-service installers for store components:

    + **Older deployments (earlier than version 10.0.11):** Deploy the retail deployable package to Commerce headquarters via LCS.
    + **New deployments (version 10.0.11 and later):** In Commerce headquarters, on the **Commerce parameters** form, on the **Channel deployment** tab, select **Check for package updates**. This update brings in the packages that are available on the **Retail Self-service package** tab in the LCS Asset library.

1. Assign the client versions to your devices.
1. Download the installers for the desired client type and device.
1. Install in target device.
1. Test and validate.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

