---
# required metadata
title: Configure Microsoft Teams integration with Dynamics 365 Commerce
description: This topics covers the details of opt-in and opt-out of Dynamics 365 Commerce and Microsoft Teams integration.
author: gvrmohanreddy
manager: jeffbl
ms.date: 01/15/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 
# optional metadata
# ms.search.form:  
#ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2021-01-15
ms.dyn365.ops.version: 10.0.18
---

# Opt-in for Microsoft Teams Integration 

In order to provision Microsoft Teams with information from Dynamics 365 Commerce and Synergize the Task Management features between POS application and Microsoft Teams, you need to opt-in for integration features. 

Note that when you opt-in for Microsoft Teams integration you consent to share your data with Microsoft Teams. Data shared with Microsoft Teams may reside in a different geography than your Dynamics 365 Commerce data and ay be subject to different compliance standards. Go through [Microsoft Trust Center ](https://www.microsoft.com/en-us/trust-center) to learn more.  Your privacy is important to us. To learn more read our [Privacy Statement] (http://aka.ms/privacy).

## Enable Microsoft Teams integration 

To enable Microsoft Teams integration with Dynamics 365 commerce you need to first register Microsoft Teams application with your tenant at Azure portal.

1. Go through Quickstart: Register an app in the Microsoft identity platform to register Microsoft Teams application with your tenant at Azure portal
1. After registering Microsoft Teams, per Register an application process,  retrieve Application ID from overview section in Azure Portal 
1. Add a client secret per Add credentials process and retrieve the application key. 
1. Go to **Retail and Commerce \> Channel setup \> Microsoft Teams Integration Configuration**.
    1. Select **Edit** on the menu bar.
    1. Set **Enable Microsoft Teams Integration** to **Yes**.
    1. For **Application ID** and **Application Key**, enter the values you have obtained from steps 2 and 3 above. 
    1. Select **Save** on the menu bar.

![Dynamics 365 Commerce - Teams integration configuration](media/D365-Commerce-Microsoft-Teams-Configuration_with_disclaimer.png)

## Opt-out to cancel Microsoft Teams Integration 

Should you decide to stop using Microsoft Teams integration with Dynamics 365 Commerce, you can follow below steps to opt-out of it:

1. Go to **Retail and Commerce \> Channel setup \> Microsoft Teams Integration Configuration**.
2. Select **Edit** on the menu bar.
3. Set **Enable Microsoft Teams Integration** to **No**.
4. For **Application ID** and **Application Key**, delete the values entered when enabling. 
5. Select **Save** on the menu bar.

> [!NOTE]
> Once you opt-out of Microsoft Teams integration with Dynamics 365 Commerce, POS will not show tasks published from Teams application anymore. 
