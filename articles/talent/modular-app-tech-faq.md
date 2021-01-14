---
# required metadata

title: Provision Onboard
description: This topic provides information about how to provision the standalone Dynamics 365 Talent - Onboard app.
author: andreabichsel
manager: AnnBe
ms.date: 04/16/2019
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
ms.reviewer: anbichse
# ms.search.scope: Core, Talent
# ms.tgt_pltfrm: 
ms.custom: 17271
ms.assetid: ba1ad49d-8232-400e-b11f-525423506a3f
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2018-03-20
ms.dyn365.ops.version: Talent March 2018 update
---

#  Provision Onboard

[!include [banner](includes/banner.md)]

The full version of Microsoft Dynamics 365 Talent includes core human resources (HR) capabilities plus Attract and Onboard, which provide recruiting and onboarding experiences for your organization. You can also purchase a standalone version of the Onboard app. Depending on whether you purchase the full version of Talent or the standalone Onboard app, the provisioning experience is slightly different.

The Onboard app is automatically provisioned when you start a trial or purchase it online. The full version of Talent requires Microsoft Dynamics Lifecycle Services (LCS) for provisioning, but the standalone Onboard app doesn't require LCS.

With the standalone Onboard app, you don't select the exact location where it should be provisioned. Instead, the following factors determine where Onboard is provisioned:

- The location of your organization's existing Microsoft Power Apps environments, if any.
- If no Power Apps environments exist, the location of the organization's existing tenant.
- The data centers that Talent currently supports.

The Onboard app is provisioned only in supported countries or regions. The supported countries and regions are defined in the Microsoft Trust Center for Talent data transparency. For a list of supported countries and regions, see [International availability of Microsoft Dynamics 365](https://docs.microsoft.com/dynamics365/get-started/availability).

The following illustration shows the logic used for provisioning the standalone Onboard app.

[![Provisioning process for the standalone Onboard app, based on country/region](./media/modular-apps-diagram-mod-app-tech.png)](./media/modular-apps-diagram-mod-app-tech.png)

Unlike the full version of Talent, the standalone Onboard app doesn't maintain a list of the environments that each user can access. Users are automatically signed in to the last environment they used. They can then select different environments by using the **Settings** button (the gear symbol).
