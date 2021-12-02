---
# required metadata

title: Engineering change management parameters
description: This topic explains how to configure engineering change management features for Microsoft Dynamics 365 Supply Chain Management.
author: t-benebo
ms.date: 09/28/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-09-28
ms.dyn365.ops.version: 10.0.15
---

# Engineering change management parameters

[!include [banner](../includes/banner.md)]

The **Engineering change management parameters** page contains setup parameters that change the default behavior that is related to the release product structure and engineering change management processes.

## Open the Engineering change management parameters page

To open the **Engineering change management parameters** page, go to **Engineering change management \> Setup \> Engineering change management parameters**. You can then set the fields as described in the remaining sections of this topic.

## Release control tab

The following table describes the fields that are available on the **Release control** tab of the **Engineering change management parameters** page. These fields affect the release product structure process.

| Field | Description |
|---|---|
| Item number rule | Select how the item number should be defined when the product is released to a legal entity. Select *Engineering product number* if the product number in the receiving legal entity should match the product number in the engineering company. Select *Local item number sequence* if the product should take the next number in the number sequence for product numbers in the receiving legal entity. |
| BOM name rule | Select how the name of the bill of materials (BOM) is defined when the product is received (released) in a legal entity. Select either *Engineering name* or *Receiving item number*. |
| Route name rule | Select how the route name should be defined when the route of a product is received (released) in a legal entity. Select either *Engineering name* or *Receiving item number*. |
| Run BOM check | Select whether a BOM check will be run when the product is received (released) in a legal entity. |
| Release behavior of inactive BOM | Select whether a product can be released if it has an inactive BOM. Select *Accept*, *Warning only*, or *Not allowed*. |
| Release behavior of inactive route | Select whether a product can be released if it has an inactive route. Select *Accept*, *Warning only*, or *Not allowed*.|
| Product acceptance | Select whether an additional step for acceptance is required before the product can be released in the legal entity. Select *Manual* to add the acceptance step. In this case, the **Open product releases** page will show the products. Select *Automatic* to show the product directly on the **Released products** page in the target legal entity immediately after the product is released together with its release product structure. |

## Engineering change management tab

The following table describes the fields that are available on the **Engineering change management** tab of the **Engineering change management parameters** page. These settings affect the engineering change management process.

| Field | Description |
|---|---|
| Category | The default category that will be used when an engineering change request is created. |
| Priority | The default priority that will be used when an engineering change request is created. |
| Severity rule | Select how the severity of an engineering change order should be established. Select *Manual* if the user is expected to enter a value in the **Severity** field. Select *Calculate* to have the system calculate the value of the **Severity** field when you select **Calculate severity** on the Action Pane of the engineering change order. In this case, the system will use the severity rules that are defined on the **Severity rule set** page. Select *Calculate automatically* to have the value of the **Severity** field automatically calculated and filled in according to the severity rule sets. |
| Re-release impacted products | This field is applicable when you re-release products via an engineering change order. You can select whether all products or only the affected products should be proposed in the **Releases** dialog box. |
| BOM levels to release | The depth of the BOM level to release. If the BOM has more levels (that is, if it's deeper) than the value that is specified here, only the levels up through the specified value will be released. |


[!INCLUDE[footer-include](../../includes/footer-banner.md)]