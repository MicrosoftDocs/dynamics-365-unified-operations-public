---
# required metadata

title: Can't create an environment in the Power Apps Admin center
description: This topic explains what to do if the admin can't create an environment in the Microsoft Power Apps Admin center.
author: twheeloc
ms.date: 08/19/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: SystemAdministrationWorkspaceForm
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Can't create an environment in the Power Apps Admin center


[!INCLUDE [PEAP](../includes/peap-2.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

**Issue**

- The tenant/environment admin can't create an environment in the Microsoft Power Apps Admin center.
- The user doesn't have a license that gives the right to create environments.

**Solution**

Make sure the tenant admin has assigned a valid Power Apps P2 license to the user creating the environment. The following Microsoft Dynamics service plans provide permissions to create environments:

| Overall product stockkeeping unit (SKU)       | Power Apps P2 service plan  |
|------------------------------------------------|----------------------------|
| Microsoft Dynamics 365 for Operations          | Power Apps for Dynamics 365 |
| Microsoft Dynamics 365 Plan Enterprise Edition | Power Apps for Dynamics 365 |

Note that various Microsoft Office SKUs also provide the right, together with standalone Power Apps Plan 2 SKUs. The important point is that one of these SKUs must be present.

1. Go to [https://preview.admin.powerapps.com/environments](https://preview.admin.powerapps.com/environments).
2. Create the environments by following the instructions in [Provision Human Resources](/dynamics365/unified-operations/talent/provisioning-talent).


[!INCLUDE[footer-include](../includes/footer-banner.md)]
