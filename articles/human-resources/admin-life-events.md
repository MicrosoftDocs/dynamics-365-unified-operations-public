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

Administrators are permitted to make changes in the Life Event plan selections based on the configuration setting. Under Human Resource Parameters, 
you can make configurations to allow the administrators to be completely unlimited in making changes in the plan selections and possible to restrict the admin fully, 
if that is desired.  

In the Human Recourse Parameters, you have the option to set up Plan Change Restrictions for the Confirmed Plans and Life events options.  

If the ‘Confirmed Plans’ switch is enabled, admin cannot make changes unless an enrollment period (like open enrollment, new hire enrollment period, or life event 
enrollment period) is active. If disabled, changes can be made at any time.  

If the ‘Life Event Options’ switch is enabled, plan changes during a life event are restricted by the life event options defined on the plan type. If disabled, 
changes are permitted to plan selections during a life event.  


## Set Plan change restrictions 

Benefits management workspace --> Links -- > Human resource Parameters --> Benefits Management 

| Field |  Description|
|-------|-------------|
|**Confirmed Plans**| Select this option if changes to a plan are not allowed unless an enrollment period is active. If this option is not selected, changes can be 
made at any time.|
|**Life Event options**|Select this option if the plan changes during a life event are restricted by the life event options defined on the plan type. If this option is 
not selected, plan selections can be changed during a life event.| 

 

