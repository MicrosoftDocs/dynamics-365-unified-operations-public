---
# required metadata

title: User can access Human Resources but not Onboard or Attract
description: This topic explains how to resolve the issue where a user can access Microsoft Dynamics 365 Talent - Human Resources, but can't access Attract or Onboard.
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

# User can access Human Resources but not Onboard or Attract

[!include [banner](includes/banner.md)]

**Environment details**

- The Microsoft Dynamics Lifecycle Services (LCS) deployment was done by user A.
- User A added user B as a user to Microsoft Dynamics 365 Human Resources.

**Issue**

User B can access Human Resources, but can't access the Talent: Attract or Talent: Onboard app. When the user tries to go to **Experience apps**, he or she is taken to a trial environment instead.

**Solution**

User B must be assigned the rights to view the Microsoft Power Apps environment that user A created during the provisioning process.

For information, see the "Granting access to the environment" section in [Provision Talent](https://docs.microsoft.com/dynamics365/unified-operations/talent/provisioning-talent).

**Long-term solution**

Microsoft is considering automatically assigning the appropriate rights to Onboard and Attract when a user is added to Human Resources.
