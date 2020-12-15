---
# required metadata

title: When to reset a data mart
description: This topic explains how to prepare data from external systems so that it can be imported into Microsoft Dynamics 365 Finance.
author: jinniew
manager: AnnBe
ms.date: 12/15/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
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

Data mart reset can be time consuming and are sometimes not the actual solution you may need. Please consider these questions before doing a data mart reset.
 
1.	When do you need to do a data mart reset?
a.	The application database was restored, but the data mart database wasn't restored.
b.	You see incorrect data for a period, and you've determined that the issue isn't a report design issue.
c.	You see incorrect data for a period, and records appear under integration attempts on report designer integration status page (start the report designer and select Tools > Integration status).
d.	Support instructs you to reset the data mart as part of a troubleshooting step.
 
2.	When you shouldn’t do a data mart reset?
a.	Anytime your reason isn’t in the "When do you need to do a data mart reset?".
b.	If it’s a performance issue with the data sync, a reset is unlikely to help.
c.	If you have a recurring reset pattern due to any one of the reasons below: 
i.	“Missing data” - First eliminate report design issues and data sync timing issues (e.g., you observe fact map hasn’t run since missing data was posted).
ii.	“Stuck” integration state.  If the integration is slow or seems stuck, a data mart reset is unlikely to resolve the issue.
iii.	If there are high number of attempts and missing data, work with support to analyze the needs for the resets prior to doing a data mart reset
iv.	Stale records alone isn’t a good reason to run a reset.  A large data set will take a long time to reset with no functional improvement.
 
3.	What happens during a reset? 
a.	A reset will only start when existing tasks are complete to ensure old data isn’t inserted.  At this point you may see a message like this: “The data mart reset was unable to be processed because of an active task. Please try again later.”
b.	The reset will disable the integration tasks and delete all the data mart data. The integration is re-enabled.
c.	Please note: 
i.	Resets do not clear report designs.
ii.	Resets do not clear company or user data unless selected.
