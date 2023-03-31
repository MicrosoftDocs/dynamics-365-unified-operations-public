--- 
# required metadata 
 
title: Define an expiry date for a production flow version
description: To end the validity and the processing of a production flow version on a given date, or to plan replacement of an active version with a new version, you have to set an expiry date on the version. 
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
# Define an expiry date for a production flow version

[!include [banner](../../includes/banner.md)]

To end the validity and the processing of a production flow version on a given date, or to plan replacement of an active version with a new version, you have to set an expiry date on the version. It is not necessary to deactivate the version.


## Set an expiration date to end a production flow version
1. Go to Production control > Setup > Lean production flow > Production flows.
2. In the list, find and select the desired record.
    * Select any production flow that has a version that is already defined.  
3. In the list, click the link in the selected row.
4. Click Edit.
5. In the list, mark the selected row.
6. In the Expiration date field, enter a date and time.
    * For the expiration date, a new version will not start or become activated. It will also no longer be possible to create or start jobs for this production flow. You can still complete started jobs after the expiration date.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]