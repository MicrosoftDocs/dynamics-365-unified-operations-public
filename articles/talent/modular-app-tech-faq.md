---
# required metadata

title: Provision Microsoft Dynamics 365 for Talent Modular Apps
description: ynamics 365 for Talent includes Core HR capabilities and functionality that provides additional experiences such as Attract and Onboard. Such functionality may also be available for purchase as a standalone modular application. 
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
# Provision Microsoft Dynamics 365 for Talent Modular Apps

[!include [banner](includes/banner.md)]

Dynamics 365 for Talent includes core human resources capabilities and functionality that provide additional experiences such as Attract and Onboard. Such functionality may also be available for purchase as a standalone modular application through web-direct (for example, Dynamics 365 for Talent: Attract or Dynamics 365 for Talent: Onboard SKUs). There are some experience differences when purchasing full Talent versus the modular applications.  

Modular applications will automatically provision upon initiation of a trial or purchase of the services through web-direct. Lifecycle Services (LCS), which is used to provision Dynamics 365 for Talent, is not used with the modular applications. Customers can sign up for a trial for Attract or Onboard independently.

Customers do not select specifically where their modular applications will provision, rather provisioning of modular applications is determined by: 

 > + location of the organization’s existing PowerApps environments;
 > + location of the organization’s existing tenant if no PowerApps environments exist; and
 > + the data centers currently supported by Dynamics 365 for Talent 

Modular applications will provision only in supported geographies (as defined in the Microsoft Trust Center for Talent data transparency), according to the logic below: 

[![Geographies for modular applications](./media/modular-apps-diagram-mod-app-tech.png)](./media/modular-apps-diagram-mod-app-tech.png)

Unlike Dynamics 365 for Talent, the modular applications do not maintain a list of environments accessible by each user. When using the modular applications service users, will automatically log into the last environment used, and can select alternate environments through the gear menu. 
