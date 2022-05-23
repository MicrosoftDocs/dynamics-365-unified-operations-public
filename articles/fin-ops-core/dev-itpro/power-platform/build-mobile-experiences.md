---
# required metadata

title: Building mobile experiences
description: This topic describes the high level steps needed to build mobile experiences in Power Apps using Finance and Operations app data 
author: jasongre
ms.date: 05/23/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.dyn365.ops.version: 
ms.search.validFrom: 2023-06-01

---

# Building mobile experiences over Finance and Operations data 

[!include [banner](../includes/banner.md)]

In today's digital world, organizations may have business processes within one or more of their Finance and Operations apps that need to be available on mobile devices to allow their users to be productive wherever they are. With the deprecation of the Finance and Operations (Dynamics 365) mobile app (see [Removed or deprecated platform features](../get-started/removed-deprecated-features-platform-updates.md#finance-and-operations-dynamics-365-mobile-application-and-mobile-platform)), the recommended way for building mobile experiences over Finance and Operations data is utilizing the tools available with the Power Platform integration, namely virtual tables and Power Apps.  

## Implementation steps
To build a mobile experience on top of Finance and Operations data, follow these high-level steps: 
1.  Ensure [virtual tables](virtual-entities-overview.md) exist covering the data and actions needed for your mobile experience. These may exist out-of-the-box, or you may need to create your own virtual table. This is important to allow your mobile experience to fetch the appropriate data from your Finance and Operations apps and to execute any actions needed for your mobile experience. 
2.  [Create a new app](https://docs.microsoft.com/en-us/power-apps/maker/) on Power Apps that connects to the desired virtual table(s).
3.  Once you have a mobile experience created on Power Apps, you can directly [run your canvas app or model-driven app on Power Apps mobile](https://docs.microsoft.com/en-us/power-apps/mobile/run-powerapps-on-mobile).


