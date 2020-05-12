---
# required metadata

title: Human Resources doesn't appear in Microsoft Dynamics 365 apps
description: This article explains what to do if the customer doesn't see the Microsoft Dynamics 365 Human Resources app among the Microsoft Dynamics 365 apps.
author: andreabichsel
manager: AnnBe
ms.date: 02/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-human-resources
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Human Resources doesn't appear in Microsoft Dynamics 365 apps

**Issue**

The customer doesn't see Dynamics 365 Human Resources among the Microsoft Dynamics 365 apps.

**Resolution**

The user must be added to the Environment Maker role for the environment in Microsoft Power Apps.

1. The admin user who has a Power Apps Plan 2 license must open the [Power Apps Admin portal](https://preview.admin.powerapps.com/).

2. Select **Environments**, and select the correct environment for Human Resources.

3. On the **Security** tab, on the **Environment roles** tab, select **Environment Maker**.

    ![Environment roles tab](media/environment-roles.png)

4. On the **Users** tab, add the user or your organization.

    ![Users tab](media/environment-maker.png)

5. Select **Save**.

6. The user must now sign in to [Microsoft Dynamics 365](https://home.dynamics.com/).

7. Select **Sync** to update the user apps.

    ![Sync button](media/get-more.png)

    After synchronization is completed, Human Resources will appear on the home page.
