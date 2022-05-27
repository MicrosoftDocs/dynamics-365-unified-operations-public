---
title: Migrate
description: This topic explains how to migrate from Microsoft Dynamics 365 Commerce Modern POS (MPOS) to the Microsoft Dynamics 365 Commerce Store Commerce app.
author: mugunthanm
ms.date: 05/27/2022
ms.topic: overview
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: v-chgriffin

ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 05-24-2022
ms.dyn365.ops.version: AX 10.0.25
---

# Migrate Modern POS to Store Commerce

[!include [banner](../../includes/banner.md)]
[!include [banner](../../includes/preview-banner.md)]

This topic explains how to migrate from Microsoft Dynamics 365 Commerce Modern POS (MPOS) to the Microsoft Dynamics 365 Commerce Store Commerce app. The Store Commerce app offers all the functionalities of Modern POS including integrated hardware support and offline mode.

To learn more about Store Commerce app, see [Store Commerce app](../store-commerce.md).

## Setup and configuration differences between MPOS and Store Commerce

| Features | Store Commerce | MPOS |
| ------ | ------ |------ |
| System requirements | Windows 11, Windows 10 (Pro, Enterprise, LTSC, and IOT Enterprise editions) with the latest available updates, or Windows Server 2019 | 	Windows 11, Windows 10 (Pro, Enterprise, LTSC, and IOT Enterprise editions) with the latest available updates, or Windows Server 2019 |
| GitHub | Yes, supports SQL Express, SQL Standard, and SQL Enterprise. | Yes, supports SQL Express, SQL Standard, and SQL Enterprise. |
| Local or Dedicated HWS support | Yes | Yes |	
| Device setup in Dynamics 365 Commerce headquarters | 	In the headquarters devices page, use the application as Store Commerce. | In the headquarters devices page, use the application as Retail Modern POS. |
| Device activation | Required | Required |
| Installer | Download from the [LCS Shared asset library](https://lcs.dynamics.com/V2/SharedAssetLibrary). On the **Shared asset library** page, select **Retail Self-service package** as the asset type, and then find the file that ends with **Store Commerce**. | 	Download from the [LCS Shared asset library](https://lcs.dynamics.com/V2/SharedAssetLibrary). On the **Shared asset library** page, select **Retail Self-service package** as the asset type, and then find the file that ends with **Modern POS (SEALED)**. |
| Extensions | 	[Commerce SDK]( https://github.com/microsoft/Dynamics365Commerce.InStore) | [Retail SDK](../retail-sdk/retail-sdk-overview.md) for non-sealed MPOS and [Commerce SDK]( https://github.com/microsoft/Dynamics365Commerce.InStore) for sealed MPOS. |
	
## To migrate to the Store Commerce app from MPOS, follow these steps.

1. Synchronize all your transaction and custom data from the channel database to Commerce headquarters, including any offline transaction and custom data.
1. Post all the statements to Commerce headquarters and ensure that there are no pending transactions to synchronize or post.
1. [Create a new device in headquarters](../../tasks/create-associate-device.md), or if you want to migrate an existing device, select the device and change the application type to **Store Commerce** on the headquarters **Devices** page and then run the **Registers (1070)** and **Channel configuration (1090)* jobs.
1. Uninstall MPOS. You don’t have to uninstall the offline database.
1. Download the Store Commerce installer from [LCS Shared asset library](https://lcs.dynamics.com/V2/SharedAssetLibrary). On the **Shared asset library** page, select **Retail Self-service package** as the asset type, and then find the file that ends with **Store Commerce**.
1. Install the Store Commerce app by passing the required parameters and related details. For information on offline mode setup and installation, see [Store Commerce app](../store-commerce). 

    [!NOTE]
    The existing offline database can be updated by passing the correct SQL instance in the installer parameter, or you can also create a new offline database. These steps are only required if you need offline mode.

1. After installing the app, launch the app from the start menu and then activate the app. For instructions on activating the app, see [Point of sale (POS) device activation](../retail-device-activation).
1. After activation, sign in to the app using your employee credentials.

## Migrate extensions

For steps on migrating extensions, see [Migrate a POS extension to the independent packaging model](migrate-pos-extension.md).
