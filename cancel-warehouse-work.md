---
# required metadata

title: Cancel warehouse work for exception handling
description: This topic describes the scope of the "cancel work" functionality that allows warehouse supervisors to handle blocked work.
author: omulvad
manager: AnnBe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSTroubIeshootingSeIfService
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: omulvad
ms.search.validFrom: 2019-10-1
ms.dyn365.ops.version: 10.0.5

---

# Cancel warehouse work for exception handling

[!include [banner](../includes/banner.md)]

"Cancel work" functionality in Dynamics 365 Supply Chain Management enables the admin user to cancel specific warehouse work that is currently in progress but is blocked by the system or cannot be completed due to some exceptional circumstances. The cancel functionality is an attractive and secure alternative to SQL corrective scripts that are typically requested from IT professionals to fix inconsistent data, and can be employed by the company’s users with admin rights.


## Warehouse work that can be cancelled

You can access the **Cancel work** menu from **Warehouse management** \> **Periodic tasks** \> **Clean up**.

During warehouse picking operations, a worker may encounter situations where, after having registered quantities as picked from a storage location to their user location, they cannot proceed with registering the put operation. Inconsistent warehouse data is often, though not always, the reason that work gets blocked.

The **Cancel work** function does not have a pre-condition for the last completed work line to be of type "put", like the standard **Cancel** button that is accessible directly from the work header does. In other words, it does not require item quantity on a work line to be on a non-user location to execute cancel logic. 

   > [!NOTE]
   > Warehouse users must continue to use the regular **Cancel** action on the work page for work that needs to be canceled for operational reasons.

Only work of type **Sales**, **Transfer issue**, **Raw material picking**, or **Replenishment** can be canceled by this job. Cancellation will not be executed for frozen raw material picking work or work that can be canceled by a regular cancel function (see the note above). 

To unblock the work, the system will cancel any remaining work lines and fix the warehouse data that is associated with the work ID specified by the user. This will allow any regular warehouse-handling operations that involve the impacted item quantity to resume. To place the impacted item in a specific location after the work is canceled, the user must utilize inventory movement or quantity adjustment operation on a mobile device.
