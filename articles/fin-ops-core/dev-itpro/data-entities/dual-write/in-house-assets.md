---
# required metadata

title: In-house assets for servicing
description: 
author: RamaKrishnamoorthy
manager: AnnBe
ms.date: 01/27/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-01-27

---

# In-house assets for servicing

[!include [banner](../../includes/banner.md)]

[!include [banner](../../includes/preview-banner.md)]

Dynamics 365 Field Service is designed to service customer assets.  Asset Management for Microsoft Dynamics 365 Supply Chain Management is designed to maintain in-house assets. Integrating these two applications on assets helps you use Dynamics 365 Field Service for servicing both customer assets and in-house assets. Also, you can classify the assets based on functional location or hierarchy and track the servicing at a minute level.

For more information, see [Integrate Dynamics 365 Field Service and Supply Chain Management](https://docs.microsoft.com/dynamics365/field-service/supply-chain-field-service-integration).

## Templates

In-house-assets includes a collection of core entity maps that work together during data interaction, as shown in the following table.

Finance and Operations apps | Model-driven app in Dynamics 365 | Description
-----------------------|--------------------------------|---
Asset management asset lifecycle models | msdyn_assetlifecyclemodels |
Asset management asset lifecycle states | msdyn_assetlifecyclestates |
Asset management assets | msdyn_customerassets |
Asset management asset types | msdyn_customerassetcategories |
Asset management functional location lifecycle models | msdyn_functionallocationlifecyclemodels |
Asset management functional location lifecycle states | msdyn_functionallocationlifecyclestates |
Asset management functional locations | msdyn_functionallocations |
Asset management functional location types | msdyn_functionallocationtypes |
Asset management manufacturers | msdyn_manufacturers |
Asset management models | msdyn_models |
Asset management warranty | msdyn_warranties |

[!include [symbols](../../includes/dual-write-symbols.md)]

[!include [lifecycle models](includes/AssetManagementAssetLifecycleModels-msdyn-assetlifecyclemodels.md)]

[!include [lifecycle states](includes/AssetManagementAssetLifecycleStates-msdyn-assetlifecyclestates.md)]

[!include [assets](includes/AssetManagementAssets-msdyn-customerassets.md)]

[!include [asset types](includes/AssetManagementAssetTypes-msdyn-customerassetcategories.md)]

[!include [functional location lifecycle models](includes/AssetManagementFunctionalLocationLifecycleModels-msdyn-functionallocationlifecyclemodels.md)]

[!include [functional location lifecycle states](includes/AssetManagementFunctionalLocationLifecycleStates-msdyn-functionallocationlifecyclestates.md)]

[!include [functional locations](includes/AssetManagementFunctionalLocations-msdyn-functionallocations.md)]

[!include [functional location types](includes/AssetManagementFunctionalLocationTypes-msdyn-functionallocationtypes.md)]

[!include [manufacturers](includes/AssetManagementManufacturers-msdyn-manufacturers.md)]

[!include [models](includes/AssetManagementModels-msdyn-models.md)]

[!include [warranty](includes/AssetManagementWarranty-msdyn-warranties.md)]



