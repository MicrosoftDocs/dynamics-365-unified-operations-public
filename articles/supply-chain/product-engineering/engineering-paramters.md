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
| **Item number rule** | It indicates how the item number is defined when the product is released to a legal entity. With Engineering product number, the product number in the receiving legal entity will be the same as in the engineering organization. With Local item number sequence, the product will take the following number in the receiving legal entity number sequence for product number  |
| **BOM name rule** | It indicates how is the BOM name defined when the product is received (released) in a legal entity. It can be chosen between Engineering name or Receiving item number |
| **Route name rule** | It indicates how is the route name defined when the route of a proudct is received (released) in a legal entity. It can be chosen between the Engineering name and the Receiving item number  |
| **Run BOM check** | Choice of if BOM check will be run when the product is received (released) in a legal entity |
| **Release behavior of inactive BOM** | <!-- KFM: Describe how to use this setting. --> |
| **Release behavior of inactive route** | <!-- KFM: Describe how to use this setting. --> |
| **Product acceptance** | Indicates if an additional step for acceptance is needed before the product is released in the legal entity. For adding the acceptance step, choose Manual. The products will be shown in the Open product releases page. When Automatic is chosen, after a product is released with the release product structure, the product will be directly shown in the Released products page in the target legal entity |

## The Engineering change management tab

<!-- KFM: Provide an intro that describes what this tab is for, in general. -->

The following table describes the settings available on the **Engineering change management** tab of the **Project Oaktree parameters** page.

| Setting | Description |
| --- | --- |
| **Category** | Default value of the Category that will be used when an engineering change request is created |
| **Priority** | Default value of the Priority that will be used when an engineering change request is created |
| **Severity rule** | It indicates how the severity of an engineering change order is established. If Manual, the user is expected to enter a value for the Severity field. If Calculate is selected, the system would calculate the value when the option Calculate severity on the top ribbon of the engineering change order is selected using the severity rules established in the Severity rule set form. If calculate automatically is selected, the Severity field will be directly calculated and defaulted according to the severity rule sets |
| **Re-release impacted products** | This parameter is applicable when re-releasing products via an engineering change order. You can choose if all products should be proposed in the re-release dialog or if only the impacted products  |
| **BOM levels to release** | It indicates the depth of the BOM level to be released. If the BOM is deeper -has more levels- than the BOM levels to release, only the first levels until the BOM levels to release will be released |
