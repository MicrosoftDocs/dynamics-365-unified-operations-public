---
title: Migrate
description: This topic explains how to migrate from Modern POS(MPOS) to Store Commerce app.
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

This topic explains how to migrate from Modern POS(MPOS) to Store Commerce app. The Store Commerce offers all the rich functionalities of Modern POS including the integrated Hardware support and Offline.

To learn more about Store Commerce app, refer this [document](https://aka.ms/StoreCommerceDoc).

## Setup and configuration differences between MPOS and Store Commerce

| Features | Store Commerce | MPOS |
| ------ | ------ |------ |
| System requirements | Windows 11, Windows 10 (Pro, Enterprise, LTSC, and IOT Enterprise editions) with the latest available updates are supported or Windows Server 2019 | 	Windows 11, Windows 10 (Pro, Enterprise, LTSC, and IOT Enterprise editions) with the latest available updates are supported or Windows Server 2019 |
| GitHub | Yes, supports SQL Express, Standard and Enterprise | Yes, supports SQL Express, Standard and Enterprise |
| Local or Dedicated HWS support | Yes | Yes |	
| Device setup in Dynamics 365 Commerce HQ | 	In the HQ devices page, use the application as Store Commerce. | In the HQ devices page, use the application as Retail Modern POS. |
| Device activation | Required | Required |
| Installer | Download from [LCS Shared asset library](https://lcs.dynamics.com/V2/SharedAssetLibrary). On the **Shared asset library** page, select **Retail Self-service package** as the asset type, and then find the file that ends with **Store Commerce** | 	Download from [LCS Shared asset library](https://lcs.dynamics.com/V2/SharedAssetLibrary). On the **Shared asset library** page, select **Retail Self-service package** as the asset type, and then find the file that ends with ** Modern POS (SEALED)** |
| Extensions | 	[Commerce SDK]( https://github.com/microsoft/Dynamics365Commerce.InStore) | [Retail SDK](../retail-sdk/retail-sdk-overview.md) for non-sealed MPOS and [Commerce SDK]( https://github.com/microsoft/Dynamics365Commerce.InStore) for Sealed MPOS |
	
## To migrate to the Store Commerce app from MPOS, follow the steps below:

1.	Sync all your transaction and custom data from the channel database to Dynamics 365 Commerce HQ including any offline transaction and custom data.
2.	Post all the statements to Dynamics 365 Commerce HQ and make sure there are no pending transactions to synchronize or post.
3.	[Create a new device in HQ](../../tasks/create-associate-device.md) or if you want to migrate an existing device then select the device and change the application type to Store Commerce in the Commerce HQ devices page and run the Registers (1070) and Channel configuration (1090) jobs.
4.	Uninstall the MPOS, you don’t have to uninstall the offline database.
5.	Download the Store Commerce installer from [LCS Shared asset library](https://lcs.dynamics.com/V2/SharedAssetLibrary). On the **Shared asset library** page, select **Retail Self-service package** as the asset type, and then find the file that ends with **Store Commerce**.
6.	Install the Store Commerce app by passing the required parameters, more details about the parameters, offline setup and installation details can be found in the Store Commerce [document](https://aka.ms/StoreCommerceDoc). 

    The existing offline database can be updated by passing the correct SQL instance in the installer parameter or you can also create a new offline database, this required only if you need offline.

7.	After installing the app, launch the app from the start menu and [activate the app](../dev-itpro/retail-device-activation.md).
8.	After activation login to the app using the employee credentials.

## Migrate extensions

To migrate the extensions follow the steps documented [here](migrate-pos-extension.md).
