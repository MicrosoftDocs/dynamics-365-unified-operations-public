--- 
# required metadata 
 
title: Add an existing activity to a production flow version
description: When creating new versions of production flows, you can choose to add activities created for the older versions, to the new version. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LeanProductionFlow, PlanActivity, PlanActivityAddExisting, PlanActivityAddExistingLookup   
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
# Add an existing activity to a production flow version

[!include [banner](../../includes/banner.md)]

When creating new versions of production flows, you can choose to add activities created for the older versions, to the new version. This procedure shows how a new version is created for an existing production flow, without copying the activities. In the next step, an existing activity is added to the new version. 

This task requires production flow with version and activities already created.


## Create a new production flow version
1. Go to Production control > Setup > Lean production flow > Production flows.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. Click Edit.
5. In the list, mark the selected row.
6. In the Expiration date field, enter a date and time.
    * Note that before you create a new production flow version, make sure to check the expiration date and time of the active version. The new version will be created with an effective start date, which connects to the expiry date of the selected version.  
7. Click Add.
8. Select No in the Copy from version field.
    * Select No to start with an empty version if most of the activities of the copied version will be replaced by new activities. Add the unchanged activities to the Add existing function in the activity form manually.  
9. Select No in the Duplicate kanban rules field.
    * When the activities are not copied to the new version, it is not possible to copy the kanban rules at the time of creation of the new version.   Instead you will use the create replacement kanban function later in the kanban rule form, to replace kanban rules of the old production flow version with kanban rules using the activities of the new version.  
10. Click OK.
11. In the list, find and select the desired record.

## Add an existing activity
1. Click Activities.
2. Click Add existing to open the drop dialog.
    * Find and select an existing activity to be added to the new production flow version.  Note that the list shows all activities that have been created for this production flow for all previous versions of the flow.  
3. In the Activity field, enter or select a value.
4. Click OK.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]