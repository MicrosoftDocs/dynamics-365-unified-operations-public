---

# required metadata

title: Dynamics 365 Human Resources infrastructure merge known issues
description: This article lists issues that can occur during the Microsoft Dynamics 365 Human Resources infrastructure merge.
author: twheeloc
ms.date: 10/27/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-10-13
ms.dyn365.ops.version: Human Resources

---
# Dynamics 365 Human Resources infrastructure merge known issues

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

## Shared Dataverse

The Dual Write framework doesn't support linking two finance and operations app environments to the same Dataverse.  
If you have a Dataverse environment that is shared with both:
 - a finance and operations app  
 - a current Human Resources environment
  
 You'll need to either duplicate or split the Dataverse environment.   

## Environment type requirements 

The following are the required environment types needed before migrating:     

 - If you don't have any Sandbox standalone environments, you'll need to create one to validate the migration. 
 - If you have multiple Production standalone environments, one of the environments can be migrated. Reach out to Microsoft Support to mark the other environments as sandboxes. 


## Teams Integration 

The existing Human Resources app in Teams is in the process of being shifted to a Power Platform solution. For more information, see [Human Resources app in Teams](hr-admin-teams-leave-app.md).  

## Licensing  

There are no changes to licensing for Dynamics 365 Human Resources including:  

 - Minimum number of purchase licenses requirement  
 - License(s) to a production and a sandbox environment: If you have existing standalone Human Resources license(s) that includes one production and one sandbox 
 environment, the same will be available on the finance and operations infrastructure. 
 - Additional sandbox license(s): If you have purchased additional sandbox license(s) for the standalone Human Resources, the same number of licenses will be available for sandbox environments on the finance and operations infrastructure.  
