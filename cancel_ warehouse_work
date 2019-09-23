---
# required metadata

title: Cancel warehouse work 
description: This topic describes the scope of the Cancel work function that allows warehouse supervisors to handle blocked work.
author: omulvad
manager: AnnBe
ms.date: 9/24/2019
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
[!include [banner](../includes/pivate-preview-banner.md)]

The Cancel work feature enables the admin user to cancel specific warehouse work that is currently in progress but is blocked by the system or cannot be completed due to some exceptional circumstances. It is an attractive and secure alternative to SQL corrective scripts that are typically requested from IT professionals to fix inconsistent data that can now be employed by the company’s users with admin rights.


## What warehouse work can be cancelled

**Cancel work** menu item is accessible from **Warehouse management** \> **Periodic tasks** \> **Clean up**.

During warehouse picking operations, a worker may encounter situations where after having registered (on their mobile devices) quantities as picked from a storage location to their user location, they cannot proceed with registering the put operation. Inconsistent warehouse data is often, though not always, the reason for a work to get blocked.

Unlike the standard **Cancel** button that is accessible directly from the Work header, the **Cancel work** function does not have a pre-condition for the last completed work line to be of type *Put*. In other words, to execute cancel logic it does not require item quantity on a work line to be on a non-user location. 

   > [!NOTE]
     > Warehouse users must continue to use the regular **Cancel** action on the work page for work that needs to be canceled for operational reasons.

Only work of type **Sales**, **Transfer issue**, **Raw material picking**, or **Replenishment** can be canceled by this job. Cancellation will not be executed for frozen raw material picking work or work that can be canceled by a regular cancel function (see Note above). 

To unblock the work, the system will cancel any remaining work lines and fix the warehouse data that is associated with the work ID specified by the user. This will allow any regular warehouse-handling operations that involve the impacted item quantity to resume. To place the impacted item in a specific location after the work is canceled, the user must utilize inventory movement or quantity adjustment operation on a mobile device.


