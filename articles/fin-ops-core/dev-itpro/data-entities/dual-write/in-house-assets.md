---
# required metadata

title: In-house assets for servicing
description: This topic describes how you can use Microsoft Dtnamics 365 Field Service to service both customer assets and in-house assets.
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

Microsoft Dynamics 365 Field Service is designed to service customer assets. Asset management for Dynamics 365 Supply Chain Management is designed to maintain in-house assets. Integration of these two apps on assets lets you use Field Service to service both customer assets and in-house assets. You can also classify the assets, based on functional location or hierarchy, and track the servicing at a detailed level.

For more information, see [Integrate Dynamics 365 Field Service and Supply Chain Management](https://docs.microsoft.com/dynamics365/field-service/supply-chain-field-service-integration).

## Templates

In-house-assets include a collection of core entity maps that work together during data interaction, as shown in the following table.

| Finance and Operations apps | Model-driven apps in Dynamics 365 | Description |
|-----------------------------|-----------------------------------|-------------|
| Asset management asset lifecycle models | msdyn\_assetlifecyclemodels | |
| Asset management asset lifecycle states | msdyn\_assetlifecyclestates | |
| Asset management assets | msdyn\_customerassets | |
| Asset management asset types | msdyn\_customerassetcategories | |
| Asset management functional location lifecycle models | msdyn\_functionallocationlifecyclemodels | |
| Asset management functional location lifecycle states | msdyn\_functionallocationlifecyclestates | |
| Asset management functional locations | msdyn\_functionallocations | |
| Asset management functional location types | msdyn\_functionallocationtypes | |
| Asset management manufacturers | msdyn\_manufacturers | |
| Asset management models | msdyn\_models | |
| Asset management warranty | msdyn\_warranties | |

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
