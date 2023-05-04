---
# required metadata

title: Download updates from Lifecycle Services (LCS)
description: This article covers what updates you should expect to see and how you can get the updates from Lifecycle Services (LCS).
author: AngelMarshall
ms.date: 09/24/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 56171
ms.assetid: 61069cf2-6c3f-4ebc-bbee-b21b1c99626a
ms.search.region: Global
# ms.search.industry: 
ms.author: tsmarsha
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Download updates from Lifecycle Services (LCS)

[!include [banner](../includes/banner.md)]

This article covers what updates you should expect to see and how you can get the latest updates using Lifecycle Services (LCS).

## Get updates

To view available updates:
1. Sign in to LCS using your credentials.
2. In the LCS project, select an environment.
3. On the **Environment** page, scroll down to see the **Available updates**.

## Types of updates

- **Binary updates** are precompiled and cumulative. Every subsequent binary update includes all previous updates. These updates don't have to be compiled in a development environment, and they can be applied directly to a nondevelopment environment from LCS.
        
    If you're running an environment that has Commerce functionality and a customized instance of Cloud point of sale (POS), you must complete the additional steps that are listed under the SDK packaging. For Microsoft Dynamics 365 Commerce, all updates, even updates for application models, are released as binary updates.    
    

    For all versions of Commerce and finance and operations apps that are version 8.1 and later, all updates, including updates for application models, are released as binary updates.


- **X++ updates** include updates to specific application functionality in application models. These updates can be independently downloaded and applied. You can select specific X++ updates to apply to your environment. Dependent X++ updates are automatically selected and downloaded. X++ updates are source code updates. Before they can be applied to a nondevelopment environment, X++ updates must be compiled in a developer environment and merged with any customizations. X++ updates apply only to version 8.0 and earlier. 

## Update option by product and version
Based on your product and version, you will have different update options from Lifecycle Services.  



### Finance and operations apps
- **Application version 8.1 and later (One Version)** - All updates for version 8.1 and later will have the One Version service update experience. It will be a cumulative, combined binary update of all of the application and platform updates. There will be no granular X++ updates starting with this release.  

     Based on your environment version and the [service update availability](../../fin-ops/get-started/public-preview-releases.md), you will have the option to choose the updates available to your environment. Each update option is associated with a version number and a build number.  

    You may see one or more of the following update options. 

   | Update        | Description           | Availability  |
   | ------------- |-------------| -----|
   | Quality update      | A quality update is a cumulative, roll-up build that contains fixes for known issues that are specific to the service update. | A quality update is available when your environment is running the same version of the current service update (n), or when your environment is running on one version older than the current service update (n-1). For example, if the current service update is version 10.0.2, you will have the option to choose a quality update if you’re running version 10.0.2, or if you’re running one version older, which is 10.0.1.<br><br>There will be no quality update available for any version that’s older than two versions of the current service update. You will have to apply the latest service update to stay current. |
   | Service update     | A service update is the version currently automatically applied to customer environments based on the LCS project update settings.<br><br>A service update is a cumulative, roll-up build that contains new features, functionality, and the related quality update that is generally available. | A service update is available if your environment has not been updated to the current service update version available for auto-update.<br><br>Only the designated sandbox or production environment will be auto-updated if you have configured the update settings for the LCS project. However, you can manually apply the current service update version to other sandbox environments or your cloud-hosted environments.|
   | Upcoming service update | An upcoming service update is the latest version that is generally available for self-update.<br><br>An upcoming service update is a cumulative, roll-up build that contains new features, functionality, and the related quality update that is generally available. | An upcoming service update is made generally available for self-deployment approximately two weeks prior to when Microsoft starts automatically applying this version based on your update settings for the LCS project.|

- **Application version 7.3 with Platform update 4 and later** - This release will still have the granular X++ updates. Starting with Platform update 4, no overlayering is allowed on the platform modules, which means that the **Platform binary updates** tile is available to provide the platform updates as a cumulative update.
 
   For customers that are on this combination, you will see the following tiles: 
   - **All X++ updates** - This tile shows all the granular X++ updates released by Microsoft. 
        
   - **Critical X++ updates** - This tile shows recommended KBs that are based on the telemetry data in your production environment. This tile will only show Production environments and a subset of the updates shown under the **All X++ updates** tile that are recommended for your environments. 
        
   - **All binary updates** - This tile shows a combined, cumulative binary update for both the Application and Platform.
        
   - **Platform binary updates** - This tile shows only the Platform binary updates. If you want to update only the platform, you can get the update from this tile. 

- **Application version 7.1, 7.2, 8.0, or earlier (except version 7.3) with Platform update 32 and earlier** - The product versions noted here are out of service.  No new X++ updates are available. You can apply the X++ updates that have been released previously but no new X++ update will be published to LCS. 

    Also, a platform update won't be available starting with **Platform update 33**. This means that you won't be able to apply the platform only update package if your application version is 7.1, 7.2, or 8.0 and earlier (except version 7.3). If you're running any of these versions, you need to upgrade to the latest version to stay with the latest feature and functionality. For more information, see [One Version service updates FAQ](../../fin-ops/get-started/one-version.md).

> [!NOTE]
> If you are on a release that is noted above, you need to upgrade as soon as possible. 
>
> For the X++ updates that have been released for these versions, they are available from [Issue Search in Lifecycle Services](../lifecycle-services/issue-search-lcs.md).

  
## Download binary updates
To download binary updates, follow these steps in LCS.

1. Select any of the binary update options, including Quality update, Service update, All binary updates, and Platform binary updates to view the combined list of application and platform binary updates. 
  
2. On the **Binary updates** page, select **Save package**.
   
   > [!NOTE]
   > You won't be able to select Knowledge Base (KB) articles to be saved because binary updates will automatically save all KBs in an update package.        
   
   ![Save Binary Package.](./media/ReviewAndSaveBinaryPackage.jpg)

3. On the **Review and save updates** page, select **Save package**.

4. In the **Save package to asset library**, enter the **Name** and **Description**, and select **Save package**.

5. Select **Done** to return to the environment page.
 
6. You'll see the saved binary package in the asset library. 

## Download X++ updates
To download X++ updates, follow these steps in LCS. 

1. Select the **All X++ updates** tile to view the list of available application updates for an environment, or select the **Critical X++ updates** tile for the application updates that are recommended for your production environment.  
  
2. On the **Add updates** page, select the applicable Knowledge Base (KB) numbers, and then select **Add** to add selected KBs to the download package.

    > [!NOTE]
    > For X++ updates, you can download all available updates at this point. Click **Select all**, and then select **Add** to add all KBs to the download package.

3. Select **Download package**.

4. On the **Review and download hotfixes** page, you can review the hotfixes that you selected, discard the package, return to the hotfix selections, or download the final hotfix package.
    
5. Download the package, and select **Done**.
   

## Additional resources
- [Apply updates to cloud environments](../deployment/apply-deployable-package-system.md)



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
