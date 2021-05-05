---
# required metadata

title: When to reset a data mart
description: This topic lists the circumstances that might be improved by resetting a data mart and circumstances in which resetting your data mart is unlikely to help.
author: jinniew
ms.date: 12/15/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jiwo
ms.search.validFrom: 2020-12-15
ms.dyn365.ops.version: 10.0.15

---

# When to reset a data mart

Resetting a data mart can be time consuming. Depending on the circumstances, this action may not be the solution that's needed. This topic lists the circumstances that might be improved by resetting a data mart, as well as circumstances in which resetting your data mart is unlikely to help.  

## When do you need to do a data mart reset?
Consider the following questions before resetting a data mart. Answering yes to one or more questions might indicate that your organization can benefit by resetting the data mart.

- Was the application database was restored?
- If you've opened a support incidenth has a support engineer instructed you to reset the data mart as part of a troubleshooting step?
 
## When it's not appropriate to reset a data mart?
There are some circumstances when we don't recommend resetting a data mart. These include the following. 

- You're experiencing performance issues that are associated with a data sync. 
- If you have a recurring reset pattern due to any of the following reasons: 
  - **Missing data** 
  - **Stuck integration state** 
  - **Stale records** - Stale records by themselves don't necessarily justify resetting the data mart. If you have a large data set, the reset process will take some time to run, but is unlikely to result in improvement.
 
## What a data mart reset does do  
- A reset will only start when existing tasks are complete. This ensures that old data is not inserted. At this point you may see a message such as, “The data mart reset was unable to be processed because of an active task. Please try again later.”
- The reset will disable the integration tasks and delete all the data mart data. The integration is re-enabled.

## Data Mart Reset FAQ
If I reset the data mart, will I lose reports that I've already designed? 
 - No, your reports are stored in SQL tables that are not impacted by a reset of the data mart. If you are concerned about losing any reports you've designed, you can back up the designs that you don't want to lose. To back them up, open Report Designer and going to **Company > Companies > Building Blocks > Export**.
 
Is it necessary for all users to exit the system to reset the data mart?
 - No, users can continue working in the system during the data mart reset. However, they won’t be able to access any reports that were created with Financial Reporter until the reset is finished. 



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
