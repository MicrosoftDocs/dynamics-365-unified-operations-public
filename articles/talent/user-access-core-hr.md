---
# required metadata

title: User can access Core HR but not Onboard or Attract apps
description: A user is able to access Core HR, but not the Attract or Onboard apps.
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

# User can access Core HR but not Onboard or Attract apps

[!include [banner](includes/banner.md)]



**Environment details**

LCS deployment performed by User A

User A added User B as a user to Core HR

**Problem:**

>   User B is able to access Core HR, but not the Attract or Onboard apps.

>   When navigating to Experience apps, User B is taken to a trial environment
>   instead.

**Solution:**

>   User B does not have rights to view the PowerApps environment created by
>   User A during the provisioning process.

See the ‘Granting access to the environment’ section in these instructions: <https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/provisioning-talent>.

**Long-term solution:**

We are looking at automatically assigning the appropriate rights to Onboard and Attract when adding a user to Core HR.
