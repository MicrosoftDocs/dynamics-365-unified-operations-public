---
# required metadata

title: Client disconnects
description: This topic explains what to do if the customer is disconnected from the environment.
author: twheeloc
ms.date: 08/19/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
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

# Client disconnects


[!INCLUDE [PEAP](../includes/peap-2.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

**Environment details** 

This issue can occur in all environments.
 
**Symptom** 

The customer is disconnected from the environment and doesn't know why. The customer receives one of the following error messages:

- We've lost your connection. Click Close to continue working.
- It appears you lost network connectivity, click Retry to try again.

**Red flag**

This issue often occurs when users are in the implementation stage, are comparing information across production and test environments, and forget that they are moving between sessions. If users are at this stage, they will most likely experience this issue.

**Issue** 

**Browser types:** Google Chrome, Internet Explorer, and Microsoft Edge

Microsoft Dynamics 365 Human Resources disconnects users when two different sessions are open at the same time for the same user and the same browser type. (For example, user A is viewing both environment 1 and environment 2 in Chrome.) It doesn't matter whether the users open different browser windows or different tabs. If the same user credentials are used to sign in to both environment 1 and environment 2 at the same time and in the same browser type, Human Resources disconnects one of the sessions.

**Solution**

Make sure that only one environment is open at a time for a given browser type. Users can open multiple sessions to the same environment (that is, multiple tabs in the same browser).

Users who want to jump between two environments at the same time should open each environment in a different browser type. (For example, user A can view environment 1 in Chrome and environment 2 in Microsoft Edge.)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
