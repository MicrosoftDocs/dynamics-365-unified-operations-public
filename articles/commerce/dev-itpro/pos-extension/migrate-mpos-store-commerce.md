---
title: Migrate Modern POS to Store Commerce
description: This article explains how to migrate from Microsoft Dynamics 365 Commerce Modern POS (MPOS) to the Microsoft Dynamics 365 Commerce Store Commerce app.
author: josaw1
ms.date: 08/22/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2022-05-24

---

# Migrate Modern POS to Store Commerce

[!include [banner](../../includes/banner.md)]

This article explains how to migrate from Microsoft Dynamics 365 Commerce Modern POS (MPOS) to the Microsoft Dynamics 365 Commerce Store Commerce app. 

The [Store Commerce app](../store-commerce.md) replaces Modern point of sale (MPOS) as the POS application for Dynamics 365 Commerce. The Store Commerce app shares complete feature parity with MPOS, including integrated hardware support and offline mode. The Store Commerce app also offers improved performance, and better deployment and management options. For more information about the benefits of Store Commerce, see [Store Commerce app](../store-commerce.md). 

> [!IMPORTANT]
> - Microsoft will deprecate MPOS in October 2023, and recommends that you use the Store Commerce app or Store Commerce for web (CPOS) for all new deployments. Existing customers should plan to migrate from MPOS to Store Commerce before October 2023.
> - If you are deploying the [Retail hybrid apps](../hybridapp.md) for Android and/or iOS, those apps will also be deprecated in favor of the Store Commerce apps for iOS and Android. For more information, see [Store Commerce app for mobile platforms](../store-commerce-mobile.md).

## Setup and configuration differences between MPOS and Store Commerce

| Features | Store Commerce | MPOS |
| ------ | ------ |------ |
| System requirements | Windows 11 (Pro, Enterprise, Enterprise LTSC, and IOT Enterprise), Windows 10 (Pro, Enterprise, Enterprise LTSC, and IoT Enterprise LTSC) with the latest available updates, Windows Server 2022 (Standard, Essentials) and Windows Server 2019 (Standard, Essentials) with the latest available updates. | Windows 11 (Pro, Enterprise and Enterprise LTSC), Windows 10 (Pro, Enterprise, Enterprise LTSC, and IoT Enterprise) with the latest available updates, or Windows Server 2019. |
| Offline | Yes. SQL Express, SQL Standard, and SQL Enterprise are supported. | Yes. SQL Express, SQL Standard, and SQL Enterprise are supported. |
| Local or Dedicated HWS support | Yes | Yes |
| Device setup in Dynamics 365 Commerce headquarters | On the **Devices** page in Commerce headquarters, use the application as Store Commerce. | On the **Devices** page in Commerce headquarters, use the application as Retail Modern POS. |
| Installer | Download from the [Shared asset library in Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/V2/SharedAssetLibrary). On the **Shared asset library** page, select **Retail Self-service package** as the asset type, and then find the file that ends with **Store Commerce**. | Download from the [LCS Shared asset library](https://lcs.dynamics.com/V2/SharedAssetLibrary). On the **Shared asset library** page, select **Retail Self-service package** as the asset type, and then find the file that ends with **Modern POS (SEALED)**. |
| Installation context | User or machine | User |
| Deployment modes | In-app, hybrid | In-app |
| Device activation | Not required when upgrading from MPOS. | Required |
| Extensions | [Commerce SDK](https://github.com/microsoft/Dynamics365Commerce.InStore) | [Retail SDK](../retail-sdk/retail-sdk-overview.md) for non-sealed MPOS and [Commerce SDK](https://github.com/microsoft/Dynamics365Commerce.InStore) for sealed MPOS |

## Migrate to the Store Commerce app from MPOS

1. Synchronize all your transaction and custom data from the channel database to Commerce headquarters. This data includes any offline transaction and custom data.
1. Post all the statements to Commerce headquarters, and ensure that there are no pending transactions to synchronize or post.
1. [Create a new device in Commerce headquarters](../../tasks/create-associate-device.md). Alternatively, to migrate an existing device, select the device and change the application type to **Store Commerce** on the **Devices** page in headquarters, and then run the **1070 (Channel configuration)** and **1090 (Registers)** jobs.
1. Uninstall MPOS. You don't have to uninstall the offline database.
1. Download the Store Commerce installer from the [LCS Shared asset library](https://lcs.dynamics.com/V2/SharedAssetLibrary). On the **Shared asset library** page, select **Retail Self-service package** as the asset type, and then find the file that ends with **Store Commerce**.
1. Install the Store Commerce app. For a list of install parameters and related details, see [Store Commerce app](../store-commerce.md).

    > [!NOTE]
    > Store Commerce supports seamless upgrade from Modern POS, which allows you to bypass activation of Store Commerce after installation. For more information, see the `--InPlaceUpgradeFromModernPOS`, `--SkipEnhancedModernPOSUpgradeValidation`, and `--SkipUninstallModernPOSAfterUpgrade` install parameters in [Store Commerce app](../store-commerce.md). 

1. After the app is installed, open it from the **Start** menu in Windows, and activate it. For information about how to activate the app, see [Point of sale (POS) device activation](../retail-device-activation.md).
1. After the app is activated, sign in to it by using your employee credentials.

You can perform silent installation and servicing updates for the Store Commerce app. For more information, see [Mass deployment of sealed Commerce self-service installers](../enhanced-mass-deployment.md).  

## Migrate extensions

For information about how to migrate extensions, see [Migrate a POS extension to the independent packaging model](migrate-pos-extension.md).
