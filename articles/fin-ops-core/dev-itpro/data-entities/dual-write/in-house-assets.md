---
# required metadata

title: In-house assets for servicing
description: 
author: ramasri
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
ms.author: 
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

[!include [](includes/AssetManagementAssetLifecycleModels-msdyn-assetlifecyclemodels.md)]

[!include [](includes/AssetManagementAssetLifecycleStates-msdyn-assetlifecyclestates.md)]

[!include [](includes/AssetManagementAssets-msdyn-customerassets.md)]

[!include [](includes/AssetManagementAssetTypes-msdyn-customerassetcategories.md)]

[!include [](includes/AssetManagementFunctionalLocationLifecycleModels-msdyn-functionallocationlifecyclemodels.md)]

[!include [](includes/AssetManagementFunctionalLocationLifecycleStates-msdyn-functionallocationlifecyclestates.md)]

[!include [](includes/AssetManagementFunctionalLocations-msdyn-functionallocations.md)]

[!include [](includes/AssetManagementFunctionalLocationTypes-msdyn-functionallocationtypes.md)]

[!include [](includes/AssetManagementManufacturers-msdyn-manufacturers.md)]

[!include [](includes/AssetManagementModels-msdyn-models.md)]

[!include [](includes/AssetManagementWarranty-msdyn-warranties.md)]



### FO.AssetManagementAssetLifecycleModels to CDS.msdyn_assetlifecyclemodels
Source field | Map type | Destination field
---|---|---
ACTIVELIFECYCLESTATEID | = | msdyn_activelifecyclestate.msdyn_assetlifecyclestate_id
INBOUNDLIFECYCLESTATEID | = | msdyn_inboundlifecyclestate.msdyn_assetlifecyclestate_id
INSTORAGELIFECYCLESTATEID | = | msdyn_instoragelifecyclestate.msdyn_assetlifecyclestate_id
LIFECYCLEMODELID | = | msdyn_assetlifecyclemodel_id
NAME | = | msdyn_name
ONLOANLIFECYCLESTATEID | = | msdyn_onloanlifecyclestate.msdyn_assetlifecyclestate_id
OUTBOUNDLIFECYCLESTATEID | = | msdyn_outboundlifecyclestate.msdyn_assetlifecyclestate_id
RECEIVEDLIFECYCLESTATEID | = | msdyn_receivedlifecyclestate.msdyn_assetlifecyclestate_id

### FO.AssetManagementAssetLifecycleStates to CDS.msdyn_assetlifecyclestates
Source field | Map type | Destination field
---|---|---
DELETEOPENCALENDARLINES | >< | msdyn_deleteopencalendarlines
LIFECYCLESTATEID | = | msdyn_assetlifecyclestate_id
LINE | = | msdyn_line
MAINTENANCEASSETACTIVE | >< | msdyn_maintenanceassetactive
NAME | = | msdyn_name

### FO.AssetManagementAssets to CDS.msdyn_customerassets
Source field | Map type | Destination field
---|---|---
ACQUISITIONCOST | = | msdyn_acquisitioncost
ACQUISITIONDATE | = | msdyn_acquisitiondate
ACTIVEFROM | = | msdyn_activefrom
ACTIVETO | = | msdyn_activeto
FUNCTIONALLOCATIONID | = | msdyn_functionallocation.msdyn_functionallocation_id
MAINTENANCEASSETLIFECYCLESTATEID | = | msdyn_assetlifecyclestate.msdyn_assetlifecyclestate_id
MODELID | = | msdyn_model.msdyn_model_id
MODELPRODUCTID | = | msdyn_model.msdyn_manufacturer.msdyn_manufacturer_id
MODELYEAR | = | msdyn_modelyear
NAME | = | msdyn_name
NOTES | = | msdyn_notes
PURCHASEORDERID | = | msdyn_purchaseorderid
REPLACEMENTDATE | >< | msdyn_replacementdate
REPLACEMENTVALUE | = | msdyn_replacementvalue
SERIALID | = | msdyn_serialid
VENDACCOUNT | = | msdyn_vendaccount
WARRANTYDATEFROMVEND | = | msdyn_warrantydatefromvend
WARRANTYID | = | msdyn_warranty.msdyn_warranty_id
WRKCTRID | = | msdyn_wrkctrid
FIXEDASSETID | = | msdyn_fixedassetid
MAINTENANCEASSETID | = | msdyn_maintenanceassetid
PARENTMAINTENANCEASSETID | = | msdyn_parentasset.msdyn_maintenanceassetid
MAINTENANCEASSETTYPEID | = | msdyn_customerassetcategory.msdyn_maintenanceassettypeid
PRODUCTID | = | msdyn_manufacturer.msdyn_manufacturer_id

### FO.AssetManagementAssetTypes to CDS.msdyn_customerassetcategories
Source field | Map type | Destination field
---|---|---
LIFECYCLEMODELID | = | msdyn_lifecyclemodel.msdyn_assetlifecyclemodel_id
MAINTENANCEASSETTYPEID | = | msdyn_maintenanceassettypeid
NAME | = | msdyn_name
CALCULATEKPITOTAL | >< | msdyn_calculatekpitotal

### FO.AssetManagementFunctionalLocationLifecycleModels to CDS.msdyn_functionallocationlifecyclemodels
Source field | Map type | Destination field
---|---|---
LIFECYCLEMODELID | = | msdyn_functionallocationlifecyclemodel_id
NAME | = | msdyn_name

### FO.AssetManagementFunctionalLocationLifecycleStates to CDS.msdyn_functionallocationlifecyclestates
Source field | Map type | Destination field
---|---|---
ALLOWDELETELOCATION | >< | msdyn_allowdeletelocation
ALLOWNEWSUBLOCATIONS | >< | msdyn_allownewsublocations
ALLOWRENAMELOCATION | >< | msdyn_allowrenamelocation
FUNCTIONALLOCATIONACTIVE | >< | msdyn_functionallocationactive
LIFECYCLESTATEID | = | msdyn_functionallocationlifecyclestate_id
NAME | = | msdyn_name
ALLOWINSTALLMAINTENANCEASSETS | >< | msdyn_allowinstallmaintenanceassets
CREATELOCATIONMAINTENANCEASSET | >< | msdyn_createlocationmaintenanceasset
MAINTENANCEASSETLIFECYCLESTATEID | = | msdyn_assetlifecyclestate.msdyn_assetlifecyclestate_id

### FO.AssetManagementFunctionalLocations to CDS.msdyn_functionallocations
Source field | Map type | Destination field
---|---|---
FUNCTIONALLOCATIONID | = | msdyn_functionallocation_id
INVENTORYLOCATIONID | = | msdyn_inventorylocationid
INVENTORYSITEID | = | msdyn_inventorysiteid
NAME | = | msdyn_name
NOTES | = | msdyn_notes
PARENTFUNCTIONALLOCATIONID | = | msdyn_parentfunctionallocation.msdyn_functionallocation_id
FUNCTIONALLOCATIONLIFECYCLESTATEID | = | msdyn_functionallocationlifecyclestate.msdyn_functionallocationlifecyclestate_id
FUNCTIONALLOCATIONTYPEID | = | msdyn_functionallocationtype.msdyn_functionallocationtype_id

### FO.AssetManagementFunctionalLocationTypes to CDS.msdyn_functionallocationtypes
Source field | Map type | Destination field
---|---|---
ALLOWMULTIPLEINSTALLEDASSETS | >< | msdyn_allowmultipleinstalledassets
FUNCTIONALLOCATIONTYPEID | = | msdyn_functionallocationtype_id
NAME | = | msdyn_name
UPDATEASSETDIMENSION | >< | msdyn_updateassetdimension
LIFECYCLEMODELID | = | msdyn_lifecyclemodelid.msdyn_functionallocationlifecyclemodel_id
MAINTENANCEASSETTYPEID | = | msdyn_maintenanceassettype.msdyn_maintenanceassettypeid

### FO.AssetManagementManufacturers to CDS.msdyn_manufacturers
Source field | Map type | Destination field
---|---|---
DESCRIPTION | = | msdyn_description
PRODUCTID | = | msdyn_manufacturer_id

### FO.AssetManagementModels to CDS.msdyn_models
Source field | Map type | Destination field
---|---|---
DESCRIPTION | = | msdyn_description
MODELID | = | msdyn_model_id
PRODUCTID | = | msdyn_manufacturer.msdyn_manufacturer_id
MAINTENANCEASSETTYPEID | = | msdyn_maintenanceassettype.msdyn_maintenanceassettypeid

### FO.AssetManagementWarranty to CDS.msdyn_warranties
Source field | Map type | Destination field
---|---|---
NAME | = | msdyn_name
WARRANTYID | = | msdyn_warranty_id



