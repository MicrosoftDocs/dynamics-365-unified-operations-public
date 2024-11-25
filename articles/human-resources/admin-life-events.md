---
# required metadata
title: Set administrator rights for life events
description: This article explains how to configure administrator rights for life events in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 08/01/2022
ms.topic: article
# optional metadata
ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Set administrator rights for life events

[!include [banner](../includes/preview-banner.md)]

Administrators can update life event options, depending on configuration settings. On the **Human resource parameters** page, you can configure parameters that allow administrators to make changes to plan selections. You can also fully restrict administrators from making changes.

On the **Human resources parameters** page, you can set up plan change restrictions for confirmed plans and life event options.

If the **Confirmed plans** option is selected, changes can be made only if an enrollment period is active. (Examples of enrollment periods include open enrollment periods, new hire enrollment periods, and life event enrollment periods.) If this option isn't selected, changes can be made at any time.

If the **Life event options** option is selected, plan changes during a life event are restricted by the life event options that are defined on the plan type. If this option isn't selected, plan selections can be changed during a life event.

## Set plan change restrictions

On the **Human resource parameters** page, on the **Benefits management** tab, the following fields are available.

| Field | Description |
|-------|-------------|
| Confirmed plans | Select this option if changes to a plan are allowed only if an enrollment period is active. If this option isn't selected, changes can be made at any time. |
| Life event options | Select this option if plan changes during a life event are restricted by the life event options that are defined on the plan type. If this option isn't selected, plan selections can be changed during a life event. |
