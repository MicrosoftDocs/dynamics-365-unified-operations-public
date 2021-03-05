---
# required metadata
title: [Dynamics 365 Commerce and Microsoft Teams integration - FAQs doc]
description: [In a better together strategy, Dynamics 365 Commerce is integrating with Microsoft Teams. This document helps frequently asked questions around integration with Teams and making seamless task mgmt. experience. ]
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

This topic provides answers to frequently asked questions about the Microsoft Dynamics 365 Commerce and Teams integration.


##How to make a regional manager or a user in Headquarters as a communications manager? 

Organization employees those needs to be a communication manager, to have an ability creating and publishing task-list in Microsoft Teams,  needs to have **Retail task manager** role in Dynamics 365 Head Quarters.

To configure permissions for an employee, follow these steps:.

1. Go to **Retail and Commerce \> Employees \> Users**.
1. Select an employee.
1. On the **User's roles** FastTab, select **Assign roles**.
1. In the **Assign roles to user** dialog box, select the **Retail task manager** role, and then select **OK**.


##How to make a specific organization hierarchy available to upload into Microsoft Teams?

In Dynamics 365 Headquarters, every organization hierarchy is associated with one or more purposes. Make sure the hierarchy that you want to provision into Microsoft Teams has retail reporting purpose associated with it. 
Refer to below screenshot
![Dynamics 365 Commerce - Organization hierarchies purpose](media/d365-commerce-organization-hierarchies-purpose.png)


##How to enable retails store workers to login with AAD into POS?

Refer to [Enable Azure Active Directory authentication for POS sign-in - Commerce](https://docs.microsoft.com/en-us/dynamics365/commerce/aad-pos-logon)


##How to link existing teams for retails stores from Microsoft Teams into Dynamics 365 Commerce?


Refer to Data mgmt. for existing Teams customers


##How to clear the graph API token stored in the session storage?

User who logs in into POS with AAD account, to view the tasks, should logout from POS or close the application to invalidate the session storage. 

![Tip:  recommendation is to always lock the computer or logout from the session when store worker is not using the computer, do not leave the computer unlocked.] 
