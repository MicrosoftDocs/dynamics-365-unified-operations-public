---
# required metadata

title: Talent app doesn't appear in Microsoft Dynamics 365 apps (CDS1.0)
description: The customer doesn't see the Talent app with the Microsoft Dynamics 365 apps.
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

The customer doesn't see the Talent app with the Microsoft Dynamics 365 apps.

**Resolution:**

The user doesn't belong to the **Environment Maker** role for the environment in PowerApps.

1.  The admin user who has a PowerApps Plan 2 license must go to the [PowerApps
    Admin portal](https://preview.admin.powerapps.com/).

1.  Click **Environments** and select the correct environment for Talent.

2.  Select the **Security** tab

3.  Click **Environment roles > Environment Maker**.

![](media/environment-roles.png)

1.  Add the user or your organization.

![](media/environment-maker.png)

1.  Click **Save**.

2.  The user must now go to the [Dynamics login](https://home.dynamics.com/).

3.  Click the **Sync** button to update the user apps. Once the sync is complete, Talent will appear in the Home Page.

![](media/get-more.png)
