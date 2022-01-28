---
# required metadata

title: Integration of the Asset management module with the Fixed asset (Russia) module 
description: This topic provides information about integrating the Asset management module with the Fixed asset (Russia) module.
author: v-oloski
ms.date: 01/27/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata
ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 

ms.search.region: Russia
# ms.search.industry: 
ms.author: v-olgaoskina
ms.search.validFrom: 2022-01-27
ms.dyn365.ops.version: 10.0.25

---
# Integration of the Asset management module wtih the Fixed asset (Russia) module

[!include [banner](../includes/banner.md)]

Manufacturers and certain distributors invest and operate assets that help them perform necessary product transformations that add value to the supply chain they are a part of. With the release of Dynamics 365 Finance 10.0.25, substantial additions were made to support various types of maintenance including, predictive, corrective, condition, and preventive. These additions also allow assets-sensitive operations to enroll the base application without investing in additional solutions.

The **Asset management** module has been integrated with **Fixed asset (Russia)** module. With this integration, there is new functionality with allows you to:

-	Relate a fixed asset (Russia) with the asset
-	Create an asset, and view the asset and costs related with the fixed asset from the fixed asset (Russia) record.

1. To relate an asset with a fixed asset (Russia), go to **Asset management** > **Assets** > **All assets**.
2. Select the asset record, and on the **Fixed asset** FastTab, in the **Fixed asset (Russia)** field group, select the fixed asset.

You can create an asset directly from a fixed asset (Russia) and the system will automatically relate the created asset with the fixed asset.

1. Go to **Fixed asset (Russia)** > **Common** > **Fixed assets**.
2. Select the fixed asset record, and on the Action Pane, select **Assets management** > **Create maintenance asset**. 

You can open the asset related to the fixed asset (Russia) from a fixed asset (Russia) record and track the asset cost.

1. Go to **Fixed asset (Russia)** > **Common** > **Fixed assets**.
2. Select the fixed asset record and on the Action Pane, select **Assets management** > **Maintenance asset**/**Maintenance cost**. 

 > [!NOTE]
 > When you create a work order and the investment type is from an asset that's related to the fixed asset (Russia), the system doesn't set this fixed asset in the project that is created. Integration of **Fixed asset (Russia)** with **Project management and accounting** is out of scope.  

## Additional resources

- [Asset management overview](https://docs.microsoft.com/en-us/dynamics365/supply-chain/asset-management), 
- [Functional locations and assets](https://docs.microsoft.com/en-us/dynamics365/supply-chain/asset-management/overview/functional-locations-and-objects), 
- [Functional locations and assets](https://docs.microsoft.com/en-us/dynamics365/supply-chain/asset-management/overview/objects-and-work-orders)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]


