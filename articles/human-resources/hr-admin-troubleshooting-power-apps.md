---
# required metadata

title: Can't create an environment in the Power Apps Admin center
description: This article explains what to do if the admin can't create an environment in the Microsoft Power Apps Admin center.
author: andreabichsel
manager: AnnBe
ms.date: 02/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-human-resources
ms.technology: 

# optional metadata

# ms.search.form: SystemAdministrationWorkspaceForm
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

# Can't create an environment in the Power Apps Admin center

**Issue**

- The tenant/environment admin can't create an environment in the Microsoft Power Apps Admin center.
- A licence that gives users the right to perform the environment creation step hasn't been assigned directly to the user who is performing that step.

**Solution**

Make sure that the tenant admin has assigned a valid Power Apps P2 license directly to the user who will perform the environment creation step. Here are the Microsoft Dynamics service plans that provide that right.

| Overall product stock keeping unit (SKU)       | Power Apps P2 service plan  |
|------------------------------------------------|----------------------------|
| Microsoft Dynamics 365 for Operations          | Power Apps for Dynamics 365 |
| Microsoft Dynamics 365 Plan Enterprise Edition | Power Apps for Dynamics 365 |

Note that various Microsoft Office SKUs also provide the right, together with standalone Power Apps Plan 2 SKUs. The important point is that one of these SKUs must be present.

1. Go to [https://preview.admin.powerapps.com/environments](https://preview.admin.powerapps.com/environments).
2. Create the environments by following the instructions in [Provision Human Resources](https://docs.microsoft.com/dynamics365/unified-operations/talent/provisioning-talent).
