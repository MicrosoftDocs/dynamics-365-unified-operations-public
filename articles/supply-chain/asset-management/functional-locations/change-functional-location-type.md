---
# required metadata

title: Change functional location type
description: This article explains how to change the functional location type on a functional location.
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

# Change functional location type

[!include [banner](../../includes/banner.md)]

This article explains how to functional location type on a functional location.

On the **All Functional locations** list page or details page (**Asset management** \> **Functional locations** \> **All functional locations**), you can change use the **Functional location type** function in the toolbar located in the **Maintain** field group to change to the functional location type on one or more selected functional locations. 

For information about the functional location types, see [Functional location types](../setup-for-functional-locations/functional-location-types.md). 

1. Select **Asset management** \> **Functional locations** \> **All functional locations**.
2. On the **All functional locations** list page, select one or more functional locations for which you want to change functional location type. Note, that if you want to change the functional location type for multiple functional locations, then you need to make sure that the selected functional locations have the same functional location type. .
3. Select **Change functional location type** from the **Maintain** field group in the toolbar. 
4. In the **Change functional location type** dialog, set the following fields:
    - **New functional location type** - Select the new functional location type for the selected functional locations.
    
    - In the **Append** group, select the following fields:
        - **Attributes** - Select, if the attributes types associated the new functional location type, should be appended to the selected functional locations.
        - **Asset attribute requirements** - Select, if the asset attribute requirements associated the new functional location type, should be appended to the selected functional locations.
         **Maintenance plans** - Select, if the maintenance plans associated the new functional location type, should be appended to the selected functional locations.
    - In the **Run in background** group, select **Batch processing** if you want the process of changing asset types as a batch job.
5. Select **OK** in the **Change asset type** dialog, to confirm the update of the new asset type.

> [!NOTE]
> On the functional location type you defined which supporting data is applicable for functional locations. This is information such as Asset types, Maintenance plans, and Asset attribute requirements. Be aware that when you change the functional location type, you might introduce an inconsistency between supporting data for existing functional locations and the supporting data on the functional location type. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]