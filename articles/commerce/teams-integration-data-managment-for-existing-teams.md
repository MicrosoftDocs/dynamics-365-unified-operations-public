---
# required metadata
title: [Dynamics 365 Commerce and Microsoft Teams integration - FAQs doc]
description: [In a better together strategy, Dynamics 365 Commerce is integrating with Microsoft Teams. This document helps managing stores and corresponding teams in Microsoft Teams mapping, in case if your organization has teams for corresponding stores already created in Microsoft Teams before enabling the integration between Dynamics 365 Commerce and Teams. ]
author: [gvrmohanreddy]
manager: jeffbl
ms.date: 03/04/2021
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


#Overview
Your organization may have teams created for some or all of your stores before using Dynamics 365 Commerce and Microsoft Teams. In that case to establish tasks synchronization between POS and Teams applications, you must provide the mapping of Store and corresponding team in Dynamics 365 Commerce headquarters using following steps:    

1. Go to **System Administration** -> **Workspace** -> **Data management**
2. Choose **Export**, add entity **Teams mapping between source and team** and use **CSV** as format: (refer to below screenshot) 

![Dynamics 365 Commerce - Data Management](media/d365-commerce-data-mgmt-export-entity.png)


3. Then click **add**, and then click **Export now**. 
4. In the CSV file you get, fill in SOURCETYPE, SOURCEID, and TEAMID values as follows:
	1. SOURCETYPE as **RetailStore** , 
	2. SOURCEID as the **store number** (e.g. 000135 for San Francisco store, you can find this @  **Retail and Commerce \> Channels \> Stores** )
	3. TEAMID as the corresponding **team ID from Microsoft teams** e.g. 5f8bc92b-6aa8-451e-85d1-3949c01ddc6c (you can find this info from admin.teams.microsoft.com.)
5. Then click import, add entity "Teams mapping between source and team" and upload the CSV:
6. Click **Import now** to establish relationship between store and existing teams.


[!Note: Once you complete the above steps, follow through [Link POS and Teams for Tasks Management]() steps to enable synchronizing task management.] 



