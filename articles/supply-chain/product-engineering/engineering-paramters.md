---
# required metadata

title: Project Oaktree parameters
description: This topic describes how to configure product engineering features for Supply Chain Management.
author: t-benebo
manager: tfehr
ms.date: 07/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-07-31
ms.dyn365.ops.version: Release 10.0.13
---

# Project Oaktree parameters

[!include [banner](../includes/banner.md)]

<!-- KFM: Provide an intro that describes what this page is for, in general. -->
Project Oaktree parameters contains setup parameters that will modify the default behavior related to the release product structure and the engineering change management processes.

## Open the Project Oaktree parameters page

To open the **Project Oaktree parameters** page, go to **Project Oaktree > Setup > Project Oaktree parameters**. Then make the settings described in the other sections of this topic.

## The Release control tab

<!-- KFM: Provide an intro that describes what this tab is for, in general. -->
The parameters in this section will affect the Release product structure process.

The following table describes the settings available on the **Release control** tab of the **Project Oaktree parameters** page.

| Setting | Description |
| --- | --- |
| **Item number rule** | <!-- KFM: Describe how to use this setting. --> |
| **BOM name rule** | <!-- KFM: Describe how to use this setting. --> |
| **Route name rule** | <!-- KFM: Describe how to use this setting. --> |
| **Run BOM check** | <!-- KFM: Describe how to use this setting. --> |
| **Release behavior of inactive BOM** | <!-- KFM: Describe how to use this setting. --> |
| **Release behavior of inactive route** | <!-- KFM: Describe how to use this setting. --> |
| **Product acceptance** | Indicates if an additional step for acceptance is needed before the product is released in the legal entity. For adding the acceptance step, choose Manual. The products will be shown in the Open product releases page. When Automatic is chosen, after a product is released with the release product structure, the product will be directly shown in the Released products page in the target legal entity |

## The Engineering change management tab

<!-- KFM: Provide an intro that describes what this tab is for, in general. -->

The following table describes the settings available on the **Engineering change management** tab of the **Project Oaktree parameters** page.

| Setting | Description |
| --- | --- |
| **Category** | <!-- KFM: Describe how to use this setting. --> |
| **Priority** | <!-- KFM: Describe how to use this setting. --> |
| **Severity rule** | <!-- KFM: Describe how to use this setting. --> |
| **Re-release impacted products** | <!-- KFM: Describe how to use this setting. --> |
| **BOM levels to release** | It indicates the depth of the BOM level to be released. If the BOM is deeper -has more levels- than the BOM levels to release, only the first levels until the BOM levels to release will be released. |
