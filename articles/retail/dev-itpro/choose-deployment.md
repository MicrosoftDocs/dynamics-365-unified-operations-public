---
# required metadata

title: Deployment options
description: This topic explains the differences in the retail functionality between Dynamics 365 for Retail and Dynamics 365 for Finance and Operations.
author: ashishmsft 
manager: AnnBe
ms.date: 10/11/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
# ms.reviewer: sericks
ms.search.scope: Retail, Operations 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: retail
ms.author: asharchw
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: Retail July 2017 update 
---

# Deployment options

Retail functionality is available in the following products:
 
- Dynamics 365 for Retail
- Dynamics 365 for Finance and Operations
 
Dynamics 365 for Retail contains core retail functionality that is typically used by most retailers. This tailored functionality improves productivity and helps to ease the on-boarding and training processes for your employees.

With Dynamics 365 for Retail, you also have the option to enable additional functionality, which means that you have the full functional footprint of Dynamics 365 Finance and Operations.
 
The following table lists of the some key differences between Dynamics 365 for Retail and Dynamics 365 for Finance and Operations.

| Capability   |  Dynamics 365 for Retail   |  Dynamics 365 for Finance and Operations  |
|--------------|----------------------------|-------------------------------------------|
|Seamless app model updates, which do not need to be compiled or merged with your customizations. | Yes | No|
|Seamless retail channel component updates (Retail POS, Channel database, Retail Server), which do not need to be merge with your customizations. | Yes | Yes |
|Retail essentials scope and enhanced seed data initialization. | Yes (Enabled by default) | Yes (Available) |
|Fully-functional footprint for a wide range of business processes. | Yes (Available - requires Unified Operations license or P1 license) | Yes (Enabled by default) |

When you first visit Lifecycle Services (LCS) after acquiring the necessary licenses for your tenant, you will be prompted to choose an implementation project type (Dynamics 365 for Retail or Dynamics 365 for Finance & Operations). You can use the above considerations to choose the right product to implement.
 
If you choose to implement Dynamics 365 for Retail, and have the necessary licenses, you will also have the option, at environment deployment time, to configure it for tailored retail functionality, or **Retail + Operations** functionality. 
 
![Deployment settings](media/Deployment-settings.png)
