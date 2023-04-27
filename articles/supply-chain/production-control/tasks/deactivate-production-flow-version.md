--- 
# required metadata 
 
title: Deactivate a production flow version
description: When an active production flow version is no longer needed, it can be deactivated. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LeanProductionFlow   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Deactivate a production flow version

[!include [banner](../../includes/banner.md)]

When an active production flow version is no longer needed, it can be deactivated. You should only use this option if all kanban rules and activities have ended and will not be activated again. Note that the expiry date of all kanban rules related to this production flow version will be updated with the current date and time. 

To modify an active production flow version, consider setting an expiry date for the active version and create a new version. This will allow you to continue your production operations while preparing the new version and related kanban rules. 

To expire an active production flow version, you need to set an expiry date. In that sense, deactivation is more like an exception than a rule. 

For this procedure you need a production flow with a version that can be deactivated. Do not try this in a production environment unless you are 100% positive that the version is fully obsolete.


## Deactivate a production flow version
1. Go to Production control > Setup > Lean production flow > Production flows.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. In the list, find and select the desired record.
5. Click Deactivate.
    * Do not proceed if you are not 100% positive that this production flow version is obsolete. Clicking Ok will expire all active kanban rules and put an immediate stop to all production and replenishment activities of this production flow version.  
6. Click OK.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]