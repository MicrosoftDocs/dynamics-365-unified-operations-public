---
# required metadata

title: Provisioning for the Dynamics 365 for Talent modular apps
description: This topic provides information about how to provision the standalone modular applications that can be purchased to provide core human resources (HR) functionality that is included in Microsoft Dynamics 365 for Talent. This functionality provides additional experiences, such as Attract and Onboard.
author: rschloma
manager: AnnBe
ms.date: 03/20/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ROBOTS: 
# ms.search.form: 
# ROBOTS: 
audience: IT Pro 
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: Core, Talent
# ms.tgt_pltfrm: 
ms.custom: 17271
ms.assetid: ba1ad49d-8232-400e-b11f-525423506a3f
ms.search.region: Global
# ms.search.industry: 
ms.author: rschloma
ms.search.validFrom: 2018-03-20
ms.dyn365.ops.version: Talent March 2018 update

---
# Provisioning for the Dynamics 365 for Talent modular apps

[!include [banner](includes/banner.md)]

Microsoft Dynamics 365 for Talent includes core human resources (HR) capabilities and functionality that provide additional experiences, such as Attract and Onboard. This functionality can also be purchased as standalone modular applications through web-direct. Examples include Microsoft Dynamics 365 for Talent: Attract and Microsoft Dynamics 365 for Talent: Onboard SKUs. Depending on whether you purchase full Talent or the modular applications, the experience differs somewhat.

Modular applications are automatically provisioned when you initiate a trial of the services or purchase them through web-direct. Customers can sign up for trials of Attract and Onboard separately.

Although Microsoft Dynamics Lifecycle Services (LCS) is used to provision Talent, it isn't used to provision the modular applications.

Customers don't select the exact location where the modular applications should be provisioned. Instead, the following factors determine where the modular applications are provisioned:

+ The location of the organization's existing Microsoft PowerApps environments
+ If no PowerApps environments exist, the location of the organization's existing tenant
+ The data centers that Talent currently supports

Modular applications will be provisioned only in supported countries or regions. The following illustration shows the logic that is used. (The supported countries and regions are defined in the Microsoft Trust Center for Talent data transparency.)

[![Provisioning process for modular applications, based on country/region](./media/modular-apps-diagram-mod-app-tech.png)](./media/modular-apps-diagram-mod-app-tech.png)

Unlike Talent, the modular applications don't maintain a list of the environments that each user can access. Users are automatically signed in to the last environment that they used. They can then select different environments by using the **Settings** button (the gear symbol).
