---
# required metadata

title: Talent app doesn't appear in Microsoft Dynamics 365 apps (CDS1.0)
description: The customer isn't seeing the Talent app in Microsoft Dynamics 365 apps
author: Darinkramer
manager: AnnBe
ms.date: 11/02/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2018-11-02
ms.dyn365.ops.version: Talent

---

# Talent app doesn't appear in Microsoft Dynamics 365 apps (CDS1.0)

[!include [banner](includes/banner.md)]


**Problem:**

Customer is not seeing the Talent app in Microsoft Dynamics 365 apps.

**RESOLUTION:**

User doesn't belong to Environment Maker role for the environment in PowerApps.

1.  The admin user who has PowerApps Plan 2 license will need to go to PowerApps
    Admin portal

<https://preview.admin.powerapps.com/>

1.  Click on Environments and select the correct environment for Talent

2.  Select the security tab

3.  Click on Environment roles \> Environment Maker

![](media/environment-roles.png)

1.  Add the user or your organization.

![](media/environment-maker.png)

1.  Click on Save

2.  Now, user must go to [https://home.dynamics.com/](https://home.dynamics.com/)

3.  Click on Sync button to update user apps. Once complete Talent will now show
    up in the Home Page.

![](media/get-more.png)
