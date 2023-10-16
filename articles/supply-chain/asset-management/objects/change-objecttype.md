---
# required metadata

title: Change asset type
description: This article explains how to change the asset type on an asset.
author: johanhoffmann
ms.date: 10/16/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Change asset type

[!include [banner](../../includes/banner.md)]

This article explains how to change the asset type on an asset.

On the **All Assets** list page or details page (**Asset management** \> **Assets** \> **All assets**), you can change use the **Change asset type** function in the toolbar located in the **Maintain** field group to change to asset type on one or more selected assets. 

For information about the asset type, see [Asset types](../setup-for-objects/object-types.md). 

1. Select **Asset management** \> **Assets** \> **All assets**.
2. On the **All assets** list page, select one or more asset for which you want to change asset type. Note, that if you want to change asset type for multiple assets, then you need to make sure that the selected assets have the same asset type. .
3. Select **Change asset type** from the **Maintain** field group in the toolbar. 
4. In the **Change asset type** dialog, set the following fields:
    - **New asset type** - Select the new asset type for the selected assets.
    
    - In the **Append** group, select the following fields:
        - **Attributes** - Select, if the attributes types associated the new asset type, should be appended to the selected assets.
        - **Maintenance plans** - Select, if the maintenance plans associated the new asset type, should be appended to the selected assets.
    - In the **Run in background** group, select **Batch processing** if you want the process of changing asset types as a batch job.
5. Select **OK** in the **Change asset type** dialog, to confirm the update of the new asset type.

> [!NOTE]
> On the asset type you defined which supporting data is allowed to use for the asset. This is information such as Maintenance job types, Counters, and Attribute types. Be aware that when you change the asset type, you might introduce an inconsistency between supporting data for existing entities and the supporting data on the new asset type. Consider following example: Asset A1 is associated Asset type AT1. AT1 has two selected Maintenance job types JT1 and JT2. Work orders are created for A1 and the maintenance jobs types are JT1 and JT2 are selected for those work orders. The asset type on asset A1 is now changed to AT2. AT2 has the selected Maintenance job types JT3 and JT4. In this case you will have work orders with Maintenance job types that are not associated with the Asset type of the asset for the work order.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]