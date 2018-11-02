---
# required metadata

title: Cannot create an environment in the PowerApps Admin center
description: 
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
ms.author: rschloma
ms.search.validFrom: 2018-11-02
ms.dyn365.ops.version: Talent

---

# Can't create an environment in the PowerApps Admin center

[!include [banner](includes/banner.md)]

**Problem:** 

-   The tenant/environment admin is unable to create an environment in the
    PowerApps admin center.

-   The user performing the environment creation is not directly assigned a
    license that gives them rights to do so.

**Solution:** 

-   Ensure the tenant admin has assigned a valid PowerApps P2 license directly
    to the user that will be performing the environment creation step. Here are
    the Dynamics service plans that provide that right:

| **Overall Product SKU**              | **PowerApps P2 service plan** |
|--------------------------------------|-------------------------------|
| Dynamics 365 for Operations          | PowerApps for Dynamics 365    |
| Dynamics 365 Plan Enterprise Edition | PowerApps for Dynamics 365    |

>   Note that various Office SKUs also provide the right, along with standalone
>   PowerApps Plan 2 SKUs. The key is that one of these must be present.

-   Navigate to [https://preview.admin.powerapps.com/environments
    ](https://preview.admin.powerapps.com/environments)

-   Create the environments following these instructions:
    <https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/provisioning-talent>.
