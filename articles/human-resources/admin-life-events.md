---
# required metadata
title: Set administrator restrictions for life events
description: Configure administrator rights for life events in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 08/01/2022
ms.topic: article
ms.prod: 
ms.technology: 
# optional metadata
ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources
---

# Set administrator rights for life events


[!INCLUDE [PEAP](../includes/peap-2.md)]

Administrators can update the **Life event options** based on configuration setting. On the **Human resource parameters** page, 
you can configure parameters to allow administrators to make changes in plan selections. It is also possible to restrict the admin fully.   

On the **Human resources parameters** page, you have the option to set up **Plan change restrictions** for the **Confirmed plans** and **Life event options**.  

If the **Confirmed plans** option is selected, changes can't be made unless an enrollment period (like open enrollment, new hire enrollment period, or life event 
enrollment period) is active. If this option is not selected, changes can be made at any time.  

If **Life event options** is selected, plan changes during a life event are restricted by the life event options defined on the plan type. If not selected, 
changes are permitted to plan selections during a life event.  


## Set Plan change restrictions 

On the **Human resource parameters** page, on the **Benefits management** tab, the following fields are available: 

| Field |  Description|
|-------|-------------|
|**Confirmed plans**| Select this option if changes to a plan are not allowed unless an enrollment period is active. If this option is not selected, changes can be 
made at any time.|
|**Life event options**|Select this option if the plan changes during a life event are restricted by the life event options defined on the plan type. If this option is 
not selected, plan selections can be changed during a life event.| 

 

