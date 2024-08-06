--- 
title: Define an expiry date for a production flow version
description: To end the validity and the processing of a production flow version on a given date, you have to set an expiry date on the version.
author: johanhoffmann
ms.author: johanho
ms.topic: how-to
ms.date: 08/29/2018
ms.custom:
ms.reviewer: kamaybac   
audience: Application User 
ms.search.form: LeanProductionFlow 
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