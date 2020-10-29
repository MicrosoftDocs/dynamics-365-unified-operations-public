---
# required metadata
title: Manage Finance and Operations updates and your custom code lifecycle
description: This document describes application lifecycle scenarios for managing your source code development branches, applying the next version of a Microsoft service update, and applying a new version of your custom code.
author: rbadawy
manager: AnnBe
ms.date: 10/22/2020
ms.topic: article
ms.service: dynamics-ax-platform
audience: Developer
ms.reviewer: rhaertle
ms.search.scope: Operations
ms.search.region: Global
ms.author: robadawy
ms.search.validFrom: 2020-10-22
ms.dyn365.ops.version: Platform update 10
---


# Manage Finance and Operations updates and your custom code lifecycle, including Dynamics 365 Commerce

This document describes application lifecycle use cases for Finance and Operations implementations and focuses on the following scenarios:

+ Manage your source code development branches.
+ Apply the next version of a Microsoft service update.
+ Apply a new version of your custom code.

This topic applies to Dynamics 365 Finance, Dynamics 365 Supply Chain Management, Dynamics 365 Commerce, and Dynamics 365 Project Operations.

The **main** goal is to illustrate the following tasks:

+ Stay current and manage Microsoft service updates (or quality updates) for Finance and Operations apps and Dynamics 365 Commerce in incremental phases independently from the lifecycle of your own customization. This simplifies the update process and reduces the cost and risk of regressions associated with all-in-one upgrade projects.
+ Capitalize on the use of source code branches for version control of your custom code. Using version control, you can isolate the rollout of critical changes and hotfixes from development of new features and capabilities.

The document does not go into the mechanics of how to use the different Azure DevOps and Lifecycle Services (LCS) tools. Instead, it focuses on processes and best practices. The sections [Apply the next version of a Microsoft service update](#apply-the-next-version-of-a-microsoft-service-update) and [Apply a new version of your custom code](#apply-a-new-version-of-your-custom-code) contain both an overview of the stages and the steps of the process.

+ [Environments](#environments)
    + [Environments running your current release](#current-environments)
    + [Environments running the next version of your custom code](#next-environments)
+ [Manage source code branches](#manage-source-code-branches)
+ [Apply the next version of a Microsoft service update](#apply-next-update)
    + [Backwards compatibility of Microsoft updates](#compatibility)
        + [Runtime compatibility](#runtime-compatibility)
        + [Design-time compatibility](#design-compatibility)
    + [Phase 1: Update the Finance and Operations implementation](#phase-1)
        + [Track 1: Update your runtime environments](update-finops-runtime)
            + [Update Test 1](#update-test-1), [Update UAT](#update-uat), [Update Prod](#update-prod)
        + [Track 2: Update your development environments](#update-finops-dev)
        + [Error situations](#error-situations)
            + [Case 1](#case-1), [Case 2](#case-2), [Case 3](#case-3)
    + [Phase 2: Update Commerce Scale Unit (CSU) to 10.0.11](#phase-2)
        + [Phase 2 prerequisites](#phase2-prerequisites)
        + [Track 1: Update your Commerce Scale Unit](#track-1:-update-your-commerce-scale-unit)
            + [Update Test 1](#update-test-1-csu), [Update UAT](#update-uat-csu), [Update Prod](#update-prod-csu)
        + [Track 2: Update your development environments](#update-csu-dev)
    + [Phase 3: Update POS to 10.0.11](#phase-3)
        + [Phase 3 prerequisites](#phase3-prerequisites)
        + [Update your Commerce Development Environment](#update-your-commerce-development-environment)
        + [Option 1: Store Component updates with only runtime changes](#option-1:-store-component-updates-with-only-runtime-changes)
        + [Option 2: Store Component updates with runtime and custom changes](#option-2:-store-component-updates-with-runtime-and-custom-changes)
        + [Update Process](#update-process)
            + [Update Test 1](#update-test-1), [Update UAT](#update-uat), [Update Prod](#update-prod)
+ [Apply a new version of your custom code](#apply-new-custom-code)
    + [Create a hotfix of your code](#create-hotfix)
    + [Update your custom code from N to N+1](#update-custom-code)
+ [Upload, update, and deploy Store components](#upload-store-components)

## <a id="environments"></a>Environments

The ALM scenarios in this topic rely on a collection of Finance and Operations environments described in the following image. These are the environments in your current release. This is a typical configuration for organizations with implementations that rely on custom code (extensions), including customizations provided by independent software vendors (ISVs).

### <a id="current-environments"></a>Environments running your current release

These are the environments in your current release.

:::image type="content" source="media/uguide-environments.png" alt-text="Environments running your current release":::

+ **Dev 1** is a development environment that is running the same Finance and Operations version as the Prod environments. It uses Azure DevOps for version control of custom code. It is connected to the current release branch of your custom code. For more information, see [manage source code branches](#manage-source-code-branches) in this topic.

    - There are many options for development environment, both cloud and on-premises. For more information, see [Deploy and access development environments](../dev-tools/access-instances.md).
    - For build automation, use the new Azure DevOps Hosted Agents functionality. For more information, see [Build automation that uses Microsoft-hosted agents and Azure Pipelines](../dev-tools/hosted-build-automation.md).

- **Test 1** is a tier 1 test environment used for functional and configuration testing. It is running the same Finance and Operations version as the production environment. It is also running the latest release version of your custom code extensions.

+ **UAT** is a pre-production environment us for user acceptance testing. This is a tier 2 (Standard Acceptance Test) or better environment. It is running the same Finance and Operations version as the production environment. It is also running the latest release version of your custom code extensions. UAT is typically connected to a copy of the production database.

+ **Prod** is your live production environment running on your production database.

### <a id="next-environments"></a>Environments running the next version of your custom code

These are the environments running the next version of your custom code.

:::image type="content" source="media/uguide-next-environments.png" alt-text="Environments running the next version of your custom code":::

- **Dev 2** is a development environment used for development of the next version of your custom code extensions. It uses Azure DevOps for version control of custom code. It is connected to the development (the **main**) branch of your custom code. For more information, see [Manage source code branches](#manage-source-code-branches) in this topic.

- **Test 2** is a functional test environment used for testing of the next version of your custom code extensions.

## Manage source code branches

It is important to follow best practices in managing branches of custom code to minimize the cost and ensure quality of your releases and updates.

:::image type="content" source="media/uguide-branches.png" alt-text="Manage source code branches":::

The **main** branch (development branch) contains the latest functioning version of the next release of your code.

When working on new features, create a new **feature** branch out of the **main** branch and integrate back into the **main** branch when the feature work is complete.

The release branches contain the code base of your official releases. The image above assumes you only have one release branch **release/2020-April**. **2020-April** is not a build, it is a source code branch. You will make changes and produce builds out of this release branch because you will probably be creating hotfixes for your release.

- Do not use a release branch to develop new features. Only use it for critical fixes or changes needed on your live environment.
- When you make a change in a release branch, integrate it back into the **main** branch to make sure your next release also contains the fix.
- Using the environments example described earlier, **Dev 1** is connected to the **release/2020-April** branch.

When you are ready to release a new version of your custom code, create a new release branch based on the **main** branch. In this example, you would create a new release branch named **2020-July** based on **main**.

You may have private branches that individual developers will be working on when working on a specific work item based on a particular branch of your code. Private branches are merged back into their parent branch when the work is complete. For more information, see [Learn about branching strategies for Team Foundation Version Control (TFVC) and how to select an effective strategy](https://docs.microsoft.com/azure/devops/repos/tfvc/branching-strategies-with-tfvc).

## <a id="apply-next-update"></a>Apply the next version of a Microsoft service update

Maximize the efficiency of taking service updates by following a phased approach. Each phase updates one component of your implementation.

1. Phase 1: Update of your Finance and Operation environments.

    Your current version of Commerce Scale Unit (CSU) and POS will function properly with the new Finance and Operation update. For example, CSU version 10.0.7 is compatible with Finance and Operations 10.0.11.

2. Phase 2: Update the Commerce Scale Unit (CSU).

3. <a id="phase-3"></a>Phase 3: Update the Commerce POS.

When you take a Microsoft update, you don't have to update your custom code to the next version. Taking Microsoft updates without bundling them with custom code updates simplifies the update process and reduces the cost and risk of regressions associated with all-in-one upgrade projects.

### <a id="compatibility"></a>Backwards compatibility of Microsoft updates

It’s important to understand what Microsoft means by backwards compatibility of service updates to set some context for the next sections. Service and quality updates are *run-time* backwards compatible. Updates are not always *design-time* (compile-time) backwards compatible.

#### <a id="runtime-compatibility"></a>Run-time compatibility

All Microsoft updates are intended to be run-time backwards-compatible. This compatibility covers both binary compatibility and functional compatibility. Runtime compatibility means that customizations that exist in production and sandbox environments will continue to work after Microsoft service updates are deployed to those environments. These updates include service updates and quality updates.

Runtime compatibility also means that Microsoft updates are backward-compatible with customizations that were compiled on an earlier platform.

Binary compatibility is backwards only. You can compile a customization on an older application and platform version, and deploy it to an environment that is running a later version. You cannot deploy code compiled on a later version than the one running on the environment you deploy to.

#### <a id="design-compatibility"></a>Design-time compatibility

Design-time (Compile-time) backward compatibility means that developers can apply updates to their development environments and successfully compile their code without having to make any changes.

Microsoft also aims for design-time compatibility. However, some updates may include changes that are not compatible at design time but are (binary) compatible. After an update is applied, new errors or warnings might occur when your code is compiled. Here are some examples of these changes:

+ Microsoft makes an enumeration extensible.
+ Microsoft marks an API as obsolete or internal.
+ Microsoft introduces a new compiler error to help avoid unsafe coding practices.

All these changes may require work on your solution. Design-time breaking changes that are binary-compatible don't require a 12-month deprecation notice, and are documented with each service update. For more information, see [What's new and changed in Platform updates](../get-started/whats-new-home-page.md).

### <a id="phase-1"></a>Phase 1: Update the Finance and Operations implementation

This section summarizes the process of updating your Finance and Operations implementation to the latest service update. For the sake of example, the description assumes you are updating from version 10.0.7 to 10.0.11.

This phase is divided into 2 tracks that can happen in parallel.

- Track 1: Updating your runtime environments.
- Track 2: Updating your development environments.

You are live on 10.0.11 after completing Track 1, unless you run into one of the error situations described in [Error situations](#error-situations) in this topic.

#### <a id="update-finops-runtime"></a>Track 1: Update your runtime environments

By completing track 1, you will practically complete your Finance and Operations update to 10.0.11 because your production environment will be live on 10.0.11. There is no need to recompile your custom code as part of this track.

##### Update Test 1

Test 1 is running version 10.0.7 with the latest released version of your custom extension. Updating test 1 is not a prerequisite in this flow but is recommended. It adds an additional level of functional verification and predictability and should be completed before the UAT environment is updated. The sooner you update and validate on Test 1, the more predictable your "real" update (UAT and Prod) will be.

1. Apply Finance and Operations version 10.0.11 to Test 1.
2. Sign off on functional scenarios. You can use the [Regression Suite Automation Tool](../perf-test/rsat/rsat-overview.md) to automate user acceptance testing on test and UAT environments.
3. If regressions are encountered, see [Error situations](#error-situations) in this topic.

##### Update UAT

UAT is running version 10.0.7 with a released version of your custom extension. (The UAT is the same as Prod).

1. Apply Finance and Operations version 10.0.11 to the UAT environment.

    Your UAT environment may be configured to be automatically updated by Microsoft, but you can always pull the update as soon as it is available.

2. Complete user acceptance testing and sign-off.
3. If regressions are encountered, see [Error situations](#error-situations) in this topic.

##### Update Prod

1. Apply version Finance and Operations 10.0.11 to Prod (that is, your production environment).

    Your UAT production may be configured to be automatically updated by Microsoft, but you can always pull the update as soon as it is available.

2. Sign-off.

#### <a id="update-finops-dev"></a>Track 2: Update your development environments

The purpose of Track 2 is to update Dev 1 to 10.0.11. Dev 1 is your **main** development environment connected to the current release branch of your custom code. Dev 1 is running Finance and Operations version 10.0.7. By completing Track 2, you make sure that Dev 1 is running 10.0.11 with your latest release and that it is ready for any future hotfixes to your code when needed.

1. Apply Finance and Operations version 10.0.11 to Dev 1.
2. Compile your custom code and test.
3. Make any required changes to your custom code.
4. Check in code changes to the release branch.
5. If you have more than one development environment:

    - Apply Finance and Operations version 10.0.11 to the development environment.
    - Synchronize and compile your latest custom code from the target code branch.

#### Error situations

##### Case 1

A bug is found during Track 1, and the bug requires a Microsoft quality update. If Microsoft releases the update in a timely manner, complete Track 1 with the new Microsoft update instead of the original service update.

##### Case 2

A bug is found during Track 1, and the bug requires a Microsoft service update that cannot be shipped in a timely manner.

Microsoft proposes a change to your custom code to work around the problem.

1. Modify your code on Dev 1 (Release branch) and test your updates.
2. Check-in to the release branch.
3. Create a new deployable package out of the release branch.
4. Apply the new deployable package on Test 1 and/or UAT.

> [!NOTE]
> Custom code that is compiled on version 10.0.7 can be deployed on any runtime environment that is running 10.0.7 or later. This means you do not need (yet) to update Dev 1 to 10.0.11 unless you have already done so as part of Track 2.

##### Case 3

A bug is found during Track 1 that requires a change to your custom code. This could be a bug in your code or the ISV code.

1. Modify your code on Dev 1 (the release branch) and test your updates.
2. Check-in to the release branch.
3. Create a new deployable package out of the release branch.
4. Apply the new deployable package on Test 1 and/or UAT.

### <a id="phase-2"></a>Phase 2: Update Commerce Scale Unit (CSU) to 10.0.11

This section summarizes the process of updating your Commerce Scale Units to the latest service update. For the sake of example, the description assumes you are updating from release 10.0.7 (Commerce version 9.17) to release 10.0.11 (Commerce version 9.21).

#### <a id="phase2-prerequisites"></a>Phase 2 prerequisites

Update the HQ environments (Finance and Operations) to the same or later release before updating the Commerce Scale Unit(s). In this example, that is 10.0.11.

This phase is divided into 2 tracks that can happen in parallel.

- Track 1: Updating your CSU runtime environments.
- Track 2: Updating your development environments.

You are live on 10.0.11 (9.21) after completing Track 1, unless you run into one of the error situations described in phase 1.

#### Track 1: Update your Commerce Scale Unit (Update Commerce Scale Unit)

By completing track 1, you will practically complete your Commerce Scale Unit update to 10.0.11 because your production environment will be live on 10.0.11. There is no need to recompile your custom code as part of this track.

##### <a id="update-test-1-csu"></a>Update Test 1 (Track 1)

The SaaS components of Commerce are not currently supported on Tier 1 environments (Dev/Test environments). Each Tier 1 environment has a copy of Retail Server running locally, and the deployment of both Microsoft code for Retail Server and retail customizations will be done through the legacy system of Application Binary package and Retail Deployable Package against the IaaS instance.

###### <a id="update-uat-csu"></a>Update UAT (Track 1)

UAT is running CSU corresponding to release 10.0.7 with the same version of your Retail extension as production

1. Go through the update workflow under Commerce Scale Unit – selecting the "9.21 (10.0.11)" version as the target.
2. Complete user acceptance testing and sign-off.
3. If regressions are encountered, see [Error situations](#error-situations) in this topic.

###### <a id="update-prod-csu"></a>Update Prod (Track 1)

1. Go through the update workflow under Commerce Scale Unit – selecting the "9.21 (10.0.11)" version as the target.
2. Sign-off.

#### <a id="update-csu-dev"></a>Track 2: Update your development environments (Update Commerce Scale Unit)

1. Get the latest version of the Retail SDK.

    - Apply Finance and Operations service update for release 10.0.11 to Dev 1.
    - Get the updated version of the Retail SDK from `%ServiceDrive%\RetailSDK\Update\<newest directory>`

2. On your **main** (development) branch, update the Retail artifacts from the new SDK.
3. Compile. The new version should be backwards compatible and should not need any changes in your code.
4. Commit the change with the Retail SDK update.
5. Make any required changes to your custom code.
6. Commit code changes to the target branch.
7. (Optional) If you have more than one development environment, then merge the latest changes from step 4 and compile the latest custom code.

### Phase 3: Update POS to 10.0.11

This section summarizes the process of updating your Store Components such as Modern Point of Sale and Hardware Station to the latest service update. For the sake of example, the description assumes you are updating from release 10.0.7 (Commerce version 9.17) to release 10.0.11 (Commerce version 9.21).

Unlike HQ (Finance and Operations) and CSU, the updates for store components are delivered in the same packages. After updating HQ and CSU you have the following options:

- Option 0 (no operation needed): Leave the store components in their previous release if the version is supported and in-policy.
- Option 1: Update the store components runtime (Microsoft code) to match the same release as CSU.
- Option 2: Update the store component runtime (Microsoft code) and customization together.

The rest of this section will assume that you want or need to update the store components (Option 1 or 2).

After this phase you'll be live on 10.0.11 (9.21) for store components, unless you run into one of the error situations described below.

#### <a id="phase2-prerequisites"></a>Phase 3 prerequisites

The prerequisites for Phase 3 are:

- The HQ components (Finance and Operations) should have been updated to the same or later release before updating the Commerce Scale Unit(s). In this example, the version is 10.0.11.
- The Commerce Scale Units should have been updated to the same or later release than the store components. In this example, that is 10.0.11.

#### Update your Commerce Development Environment

See the steps for [updating your development environment for CSU](#track-2-update-your-development-environments-1).

#### Option 1: Store Component updates with only runtime changes

This option generates a new retail deployable package containing you store components, with changes only to the Microsoft code

1. Update your release branch (with the code that is currently being used in production) to the Retail SDK matching your target release. In this example, the is version 10.0.11(9.21). See the steps for [updating your development environment for CSU](#track-2-update-your-development-environments-1).

2. Generate a new build for the Retail Deployable Package. It contains same set of customizations currently in production + 10.0.11 (9.21) Microsoft code.

#### Option 2: Store Component updates with runtime and custom changes

This option will generate a new retail deployable package containing you store components, with changes from both Microsoft code and customizations.

1. Update your release branch (with the code that is currently being used in production) to the Retail SDK matching your target release. In this example, the version is 10.0.11(9.21). See the steps for [updating your development environment for CSU](#track-2-update-your-development-environments-1)

2. Commit changes.
3. Update custom code for store components, or update references to ISV updated components.
4. Generate a new build for the Retail Deployable Package. The build contains updated custom code + 10.0.11 (9.21) Microsoft code.

#### Update Process

##### Update Test 1 (Update process)

The SaaS components of Dynamics 365 Commerce are not currently supported on dev or test One-boxes environments. Each dev or test One-box has a copy of Retail Server running locally, and the deployment of both Microsoft code for Retail Server and retail customizations will be done through the legacy system of Application Binary package and Retail Deployable Package against the IaaS instance.

Test 1 is running version 10.0.11 HQ and local version of RCSU (from previous phases). Updating test 1 is not a prerequisite in this flow. Given there is no CSU in this environment this step is mostly for verification.

1. Upload, Update and Deploy the Store Components. For more information, see [Upload, update, and deploy Store components](#upload-store-components) in this topic.
2. Sign-off on functional scenarios.
3. If regressions are encountered, see Error situations below.

##### Update UAT (Update process)

Clients pointing to UAT are running applications (e.g. MPOS) for release 10.0.7 (the same version as currently in production).

1. Upload, update and deploy the Store components. For more information, see [Uploading, updating, and deploying Store components](#uploading-updating-deploying-store-components) in this topic.
2. Sign-off on functional scenarios.
3. If regressions are encountered, see [Error situations](#error-situations) in this topic.

##### Update Prod (Update process)

1. Upload, update, and deploy the Store components.
2. Sign-off.

## <a id="apply-new-custom-code"></a>Apply a new version of your custom code

This section describes the recommended flow of 2 use cases that require updating your UAT and/or Prod environments with a new build of your custom extension.

### <a id="create-hotfix"></a>Create a hotfix of your code

When a critical bug is found on UAT or Prod, fix the bug in the release branch (not in the **main** or development branch) and follow the standard process of applying a deployable package to UAT and Prod.

:::image type="content" source="media/uguide-hotfix.png" alt-text="Process for hotfix":::

1. Make the code fix in the release branch, on the Dev 1 environment. If the required fix is in ISV code, ask the ISV to send you a new build of their current release and not their next version of the solution.
2. Compile and test.
3. Create a new deployable package out of the release branch.
4. Deploy on Test 1 and sign-off if needed.
5. Follow the standard process of deploying custom code to UAT then Prod.
6. Integrate the code fix with your **main** code branch.

### <a id="update-custom-code"></a>Update custom code from N to N+1

When you are ready to release the next version of your custom code, follow this process to create and deploy the new release.

:::image type="content" source="media/uguide-custom-code.png" alt-text="Update custom code from N to N+1":::

1. Complete development in the **main** branch, on the Dev 2 environment (or other environments connected to the **main** branch).
2. Deploy and test on Test 2.
3. Repeat 1 and 2 until new version is signed-off.
4. Create a **new** release branch.
5. Create a new deployable package out of the **new** release branch.
6. Follow the standard process of deploying custom code to UAT then Prod.
7. Retire the old release branch.

## <a id="upload-store-components"></a>Upload, update, and deploy Store components

1. Upload the resulting Retail Deployable Package to LCS.
2. Update AOS with the latest client.
3. Upload Retail Deployable Package to your asset library.

    + Legacy: Software Deployable Package
    + New (10.0.11+) : Retail Self-Service Installers for 10.0.11+ deployments

4. Update HQ with the new self-service installers for store components.

    + Legacy: Deploy the Retail Deployable Package to HQ via LCS
    + New (10.0.11+): In HQ go to the "Commerce parameters" form, "Channel deployment" tab and click on "Check for package updates" – this will bring in the packages available in LCS Asset library under "Retail Self-service package"

5. Assign the client versions to your devices.
6. Download the installers for the desired client type and device.
7. Install in target device.
8. Test and validate.
