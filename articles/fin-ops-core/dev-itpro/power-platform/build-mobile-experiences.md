---
title: Building mobile experiences
description: Learn about the high level steps needed to build mobile experiences in Power Apps using finance and operations app data.
author: jasongre
ms.author: jasongre
ms.topic: article
ms.date: 06/08/2022
ms.custom: 
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.dyn365.ops.version: 
ms.search.form: 
ms.search.validFrom: 2023-06-01
---

# Building mobile experiences over finance and operations data 

[!include [banner](../includes/banner.md)]

In today's digital world, organizations may have business processes within one or more of their finance and operations apps (Dynamics 365 for Finance, Supply Chain Management, Commerce, Project Operations, and Human Resources) that need to be available on mobile devices to allow their users to be productive wherever they are. With the deprecation of the finance and operations (Dynamics 365) mobile app (see [Removed or deprecated platform features](../get-started/removed-deprecated-features-platform-updates.md#finance-and-operations-dynamics-365-mobile-application-and-mobile-platform)), the recommended way for building mobile experiences over finance and operations data is utilizing the tools available with the Power Platform integration, namely virtual tables and Power Apps. 

## Implementation steps
To build a mobile experience on top of finance and operations data, follow these high-level steps: 
1.  Ensure [virtual tables](virtual-entities-overview.md) exist covering the data and actions needed for your mobile experience. These may exist out-of-the-box, or you may need to create your own virtual table. This is important to allow your mobile experience to fetch the appropriate data from your finance and operations apps and to execute any actions needed for your mobile experience. 
2.  [Create a new app](/power-apps/maker/) on Power Apps that connects to the desired virtual table(s). 
3.  Once you have a mobile experience created on Power Apps, you can directly [run your canvas app or model-driven app on Power Apps mobile](/power-apps/mobile/run-powerapps-on-mobile).
4.  For a seamless mobile experience, you can optionally [wrap your Power Apps application](/power-apps/maker/common/wrap/overview) as a custom-branded Android and iOS app for native distribution to end users. This option is currently only available for canvas apps.

## Other useful links
-  [Using the Power Platform to extend finance and operations apps](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-series-using-the-power-platform-to-extend-finance-and-operations-apps) Tech Talk series
-  [Planning your Power Apps project](/power-apps/guidance/planning/introduction)
-  [Building your first model-driven app](/power-apps/maker/model-driven-apps/build-first-model-driven-app)



