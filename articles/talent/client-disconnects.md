---
# required metadata

title: The client disconnects
description: The customer is getting disconnected form their environment and doesn’t know why.
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

# The client disconnects

[!include [banner](includes/banner.md)]

**Environment details:** 

All
 

**Symptom:** 

The customer is getting disconnected form their environment and doesn’t know why. The customer receives one of the following errors.

-   “We've lost your connection. Click Close to continue working.”

-   “It appears you lost network connectivity, click Retry to try again.”

**Red flag:**

This often happens when users are in the implementation stage since they are
comparing information across Production and Test environments and forget that
they are moving between sessions. If they are at this stage, most likely they
would see this issue.
   

**Problem:** 

Browser type(s) = Chrome, Internet Explorer, Edge

The Talent platform disconnects users when two different sessions are opened at
the same time for the same user and browser type. (e.g. User A is looking at
Environment 1 and Environment 2 within Chrome) It doesn't matter if they open in
in different browser windows or just different tabs, if it is the same user
credentials logging into environment 1 and environment 2 at the same time from
the same browser, Talent will disconnect one of the sessions.

**Solution:** 

Ensure only one environment is open at a time for a given browser type. Users
can open multiple sessions (tabs within the same browser) to the same
environment.

If users want to jump between two different environments at the same time, open
each one in a different browser type. (e.g. User A can look at Environment 1 in
Chrome, and Environment 2 in Edge.)
