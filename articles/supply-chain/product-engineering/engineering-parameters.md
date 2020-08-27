---
# required metadata

title: Project Oaktree parameters
description: This topic describes how to configure engineering change management features for Supply Chain Management.
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

**Project Oaktree parameters** contains setup parameters that modify the default behavior related to the release product structure and the engineering change management processes.

## Open the Project Oaktree parameters page

To open the **Project Oaktree parameters** page, go to **Project Oaktree \> Setup \> Project Oaktree parameters**. Then make the settings described in the other sections of this topic.

## The Release control tab

The following table describes the settings available on the **Release control** tab of the **Project Oaktree parameters** page. These settings affect the release product structure process.

| Setting | Description |
| --- | --- |
| **Item number rule** | Choose how the item number should be defined when the product is released to a legal entity. Select *Engineering product number* if the product number in the receiving legal entity should be the same as in the engineering company. Select *Local item number sequence* if the product should take the following number in the receiving legal entity number sequence for product number.  |
| **BOM name rule** | Choose how is the BOM name is defined when the product is received (released) in a legal entity. Select *Engineering name* or *Receiving item number*. |
| **Route name rule** | Choose how the route name should be defined when the route of a product is received (released) in a legal entity. Select *Engineering name* or *Receiving item number*.  |
| **Run BOM check** | Choose whether a BOM check will be run when the product is received (released) in a legal entity. |
| **Release behavior of inactive BOM** | Choose whether to allow a product to be released when it has an inactive BOM. Options are *Accept*, *Warning only*, and *Not allowed*. |
| **Release behavior of inactive route** | Choose whether to allow a product to be released when it has an inactive route. Options are *Accept*, *Warning only*, and *Not allowed*.|
| **Product acceptance** | Choose whether an additional step for acceptance is needed before the product is released in the legal entity. To add the acceptance step, choose *Manual*, in which case the products will be shown on the **Open product releases** page. Select *Automatic* show the product directly on the **Released products** page in the target legal entity immediately after it is released with the release product structure. |

## The Engineering change management tab

The following table describes the settings available on the **Engineering change management** tab of the **Project Oaktree parameters** page. These settings affect the engineering change process.

| Setting | Description |
| --- | --- |
| **Category** | Default value of the category that will be used when an engineering change request is created |
| **Priority** | Default value of the Priority that will be used when an engineering change request is created |
| **Severity rule** | Choose how the severity of an engineering change order should be established. Select *Manual* if the user is expected to enter a value for the **Severity** field. Select *Calculate* to have the system calculate the value when you select **Calculate severity** from the Action Pane of the engineering change order; the system will use the severity rules established in the **Severity rule set** page. Select *Calculate automatically* do calculate the **Severity** field directly and default according to the severity rule sets. |
| **Re-release impacted products** | This parameter is applicable when re-releasing products via an engineering change order. You can choose if all products should be proposed in the re-release dialog or if only the impacted products  |
| **BOM levels to release** | Indicates the depth of the BOM level to be released. If the BOM is deeper (has more levels) than the value specified here, only the first levels (up to this value) will be released. |
