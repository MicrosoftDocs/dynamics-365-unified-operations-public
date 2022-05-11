---
title: In-house assets for servicing
description: This topic describes how you can use Microsoft Dynamics 365 Field Service to service both customer assets and in-house assets.
author: RamaKrishnamoorthy
ms.date: 01/27/2020
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: tfehr
ms.search.region: global
ms.author: ramasri
ms.search.validFrom: 2020-01-27
---

# In-house assets for servicing

[!include [banner](../../includes/banner.md)]

Microsoft Dynamics 365 Field Service is designed to service customer assets. Asset management for Dynamics 365 Supply Chain Management is designed to maintain in-house assets. Integration of these two apps lets you use Field Service to service both customer assets and in-house assets. You can also classify the assets, based on functional location or hierarchy, and track the servicing at a detailed level.

For more information, see [Integrate Dynamics 365 Field Service and Supply Chain Management](/dynamics365/field-service/supply-chain-field-service-integration).

## Templates

In-house-assets include a collection of core table maps that work together during data interaction, as shown in the following table.

| Finance and operations apps | Customer engagement apps | Description |
|-----------------------------|-----------------------------------|-------------|
[Asset management asset lifecycle models](mapping-reference.md#119) | msdyn_assetlifecyclemodels | |
[Asset management asset lifecycle states](mapping-reference.md#120) | msdyn_assetlifecyclestates | |
[Asset management asset types](mapping-reference.md#124) | msdyn_customerassetcategories | |
[Asset management assets](mapping-reference.md#125) | msdyn_customerassets | |
[Asset management functional location lifecycle models](mapping-reference.md#134) | msdyn_functionallocationlifecyclemodels | |
[Asset management functional location lifecycle states](mapping-reference.md#135) | msdyn_functionallocationlifecyclestates | |
[Asset management functional location types](mapping-reference.md#137) | msdyn_functionallocationtypes | |
[Asset management functional locations](mapping-reference.md#136) | msdyn_functionallocations | |
[Asset management manufacturers](mapping-reference.md#153) | msdyn_manufacturers | |
[Asset management models](mapping-reference.md#154) | msdyn_models | |
[Asset management warranty](mapping-reference.md#209) | msdyn_warranties | |

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
