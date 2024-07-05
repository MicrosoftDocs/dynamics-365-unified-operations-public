---
title: Download updates from Lifecycle Services (LCS)
description: Learn about what updates you should expect to see, and how you can get the updates from Lifecycle Services, including an overview on types of updates.
author: AngelMarshall
ms.author: tsmarsha
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 06/24/2024
ms.reviewer: twheeloc
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 61069cf2-6c3f-4ebc-bbee-b21b1c99626a
---

# Download updates from Lifecycle Services (LCS)

[!include [banner](../includes/banner.md)]

This article covers what updates you should expect to see, and how you can get the latest updates by using Microsoft Dynamics Lifecycle Services.

## Get updates

To view the available updates, follow these steps.

1. Sign in to Lifecycle Services by using your credentials.
2. In the Lifecycle Services project, select an environment.
3. On the **Environment** page, scroll down to **Available updates**.

## Types of updates

- **Binary updates** are precompiled and cumulative. Therefore, every binary update includes all previous updates. In addition, these updates don't have to be compiled in a development environment but can be applied directly to a nondevelopment environment from Lifecycle Services.

    If you're running an environment that has Commerce functionality and a customized instance of Cloud point of sale (POS), you must complete the additional steps that are listed under the software development kit (SDK) packaging.

    For all versions of Microsoft Dynamics 365 Commerce, and for finance and operations apps that are version 8.1 and later, all updates, including updates for application models, are released as binary updates.

- **X++ updates** include updates to specific application functionality in application models. These updates can be independently downloaded and applied. You can select specific X++ updates to apply to your environment. Dependent X++ updates are automatically selected and downloaded. X++ updates are source code updates. Before they can be applied to a nondevelopment environment, they must be compiled in a development environment and merged with any customizations. X++ updates apply only to version 8.0 and earlier.

## Update options by product and version

Based on your product and version, you have different options for updating from Lifecycle Services.

### Finance and operations apps

- **Application version 8.1 and later (One Version)** – All updates for version 8.1 and later have the One Version service update experience. Each of these updates is a cumulative, combined binary update of all the application and platform updates. As of version 8.1, there are no granular X++ updates.

    Based on your environment version and the [service update availability](../../fin-ops/get-started/public-preview-releases.md), you have the option to select the updates that are available to your environment. Each update option is associated with a version number and a build number.

    You might see one or more of the following update options.

    | Update | Description | Availability |
    |---|---|---|
    | Quality update | A quality update is a cumulative roll-up build that contains fixes for known issues that are specific to the service update. | <p>A quality update is available for any in-service version. For servicing dates by version, see [Service update availability](../../fin-ops/get-started/public-preview-releases.md).</p><p>Quality updates aren't available for any version that has reached its end of service. You must apply the latest service update to stay current. For end-of-service dates by version, see [Service update availability](../../fin-ops/get-started/public-preview-releases.md).</p> |
    | Service update | <p>A service update is the version that's currently automatically applied to customer environments, based on the Lifecycle Services project update settings.</p><p>A service update is a cumulative roll-up build that contains new features and functionality, and also the latest related quality update.</p> | <p>A service update is available if your environment isn't updated to the current service update version that's available for auto-update.</p><p>Only the designated sandbox or production environment is auto-updated if you configured the update settings for the Lifecycle Services project. However, you can manually apply the current service update version to other sandbox environments or your cloud-hosted environments.</p> |
    | Upcoming service update | <p>An upcoming service update is the latest version that's generally available for self-update.</p><p>An upcoming service update is a cumulative roll-up build that contains new features and functionality, and also the latest related quality update.</p> | An upcoming service update is made generally available for self-deployment before Microsoft starts to automatically apply this version based on your update settings for the Lifecycle Services project. The timing of the package release for self-update relative to the production auto-updates varies. To determine the timing of self-update and auto-updates for upcoming releases, see [Targeted release schedule (dates subject to change)](../../fin-ops/get-started/public-preview-releases.md#targeted-release-schedule-dates-subject-to-change). |

- **Application version 7.3 with Platform update 4 and later** – This release still has the granular X++ updates. As of Platform update 4, no overlayering is allowed on the platform modules. Therefore, the **Platform binary updates** tile is available to provide the platform updates as a cumulative update.

    For customers who are on this combination, the following tiles are visible:

    - **All X++ updates** – This tile shows all the granular X++ updates that are released by Microsoft.
    - **Critical X++ updates** – This tile shows recommended Knowledge Base (KB) articles, based on the telemetry data in your production environment. This tile shows only production environments and only those updates from the **All X++ updates** tile that are recommended for your environments.
    - **All binary updates** – This tile shows a combined, cumulative binary update for both the application and the platform.
    - **Platform binary updates** – This tile shows only the platform binary updates. If you want to update only the platform, you can get the update from this tile.

- **Application version 7.1, 7.2, 8.0, or earlier (except version 7.3) with Platform update 32 and earlier** – The product versions that are noted here are out of service. No new X++ updates are available. You can apply the X++ updates that have previously been released, but no new X++ update will be published to Lifecycle Services.

    In addition, as of **Platform update 33**, no platform update is available. Therefore, you can't apply the platform-only update package if your application version is 7.1, 7.2, 8.0, or earlier (except version 7.3). If you're running any of these versions, you must upgrade to the latest version to keep the latest features and functionality. For more information, see [One Version service updates FAQ](../../fin-ops/get-started/one-version.md).

> [!IMPORTANT]
> If you're on one of the previous noted releases, you must upgrade as soon as possible.

> [!NOTE]
> The X++ updates that have been released for these versions are available from [Issue search in Lifecycle Services](../lifecycle-services/issue-search-lcs.md).

## Download binary updates

To download binary updates, follow these steps in Lifecycle Services.

1. Select any of the binary update options, including **Quality update**, **Service update**, **All binary updates**, and **Platform binary updates** to view the combined list of application and platform binary updates.
2. On the **Binary updates** page, select **Save package**.

    > [!NOTE]
    > You can't select KBs to save, because binary updates automatically save all KBs in an update package.

    ![Screenshot that shows the Save package button on the Binary updates page.](./media/ReviewAndSaveBinaryPackage.jpg)

3. On the **Review and save updates** page, select **Save package**.
4. In the **Save package to asset library** dialog box, enter the name and description, and then select **Save package**.
5. Select **Done** to return to the environment page.
6. You should find the saved binary package in the Asset library.

## Download X++ updates

To download X++ updates, follow these steps in Lifecycle Services.

1. Select the **All X++ updates** tile to view the list of available application updates for an environment. Alternatively, select the **Critical X++ updates** tile to view the list of application updates that are recommended for your production environment.
2. On the **Add updates** page, select the applicable KB numbers, and then select **Add** to add the selected KBs to the download package.

    > [!NOTE]
    > For X++ updates, you can download all available updates at this point. Select **Select all**, and then select **Add** to add all KBs to the download package.

3. Select **Download package**.
4. On the **Review and download hotfixes** page, you can review the hotfixes that you selected, discard the package, return to the hotfix selections, or download the final hotfix package.
5. Download the package, and then select **Done**.

## Additional resources

- [Apply updates to cloud environments](../deployment/apply-deployable-package-system.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
