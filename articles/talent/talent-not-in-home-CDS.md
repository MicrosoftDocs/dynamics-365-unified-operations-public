---
# required metadata

title: Talent doesn't appear among the Microsoft Dynamics 365 apps (Common Data Service 1.0)
description: This topic explains what to do if the customer doesn't see the Microsoft Dynamics 365 Talent app among the Microsoft Dynamics 365 apps.
author: andreabichsel
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
ms.reviewer: anbichse
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2018-11-02
ms.dyn365.ops.version: Talent

---

# Talent doesn't appear among the Microsoft Dynamics 365 apps (Common Data Service 1.0)

[!include [banner](includes/banner.md)]

**Issue**

The customer doesn't see the Microsoft Dynamics 365 Talent app among the Microsoft Dynamics 365 apps.

**Resolution**

The user must be added to the Environment Maker role for the environment in Microsoft PowerApps.

1. The admin user who has a PowerApps Plan 2 license must open the [PowerApps Admin portal](https://preview.admin.powerapps.com/).
2. Select **Environments**, and select the correct environment for Talent.
3. On the **Security** tab, on the **Environment roles** tab, select **Environment Maker**.

    ![Environment roles tab](media/environment-roles.png)

4. On the **Users** tab, add the user or your organization.

    ![Users tab](media/environment-maker.png)

5. Select **Save**.
6. The user must now sign in to [Microsoft Dynamics 365](https://home.dynamics.com/).
7. Select **Sync** to update the user apps.

    ![Sync button](media/get-more.png)

    After synchronization is completed, Talent will appear on the home page.
