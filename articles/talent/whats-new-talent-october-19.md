---
# required metadata

title: What's new or changed in Dynamics 365 Talent - Core HR (October 16, 2018)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent - Core HR.
author: Darinkramer
manager: AnnBe
ms.date: 10/22/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2018-10-22
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent - Core HR (October 16, 2018)

**Build 8.1.1067**

This topic describes features that are either new or changed in Core HR.

## Allow managers to update time off requests

Employee time off requests may need to be updated after they are approved through the workflow. In many cases, the manager makes these updates on the employee’s behalf. This new feature provides the ability for managers to update time off or cancel time off requests on behalf of their employees. This capability is controlled by the **Work on behalf** parameter that can be set on the **Human Resource Parameters** page. 
 
## Allow HR to update time off requests

Similar to the feature above, employee time off requests may need to be updated by HR after they have been previously approved through the workflow. This feature provides the ability for HR users to update time off requests. The capability is enabled in the **People** workspace and on the **Worker** page, using a new option called **View time off**. On those pages, HR users can view requests and update time off transactions, similar to how managers can perform these actions.

The security duty that controls access to this functionality is:
- Duty: Maintain worker-specific leave and absence processes.
- Privilege: Maintain leave and absence requests for all workers.

## Other changes
The following updates have been made in this release:
- Changes to worker hire actions so that they are no longer "stuck" in **Workflow complete** state.
- Employment record can now be created without an employment start date.
- The Dynamics 365 Talent registration date for a course shown in Employee self-service now applies the time zone offset to the date.
- Excel files can be imported multiple times without any errors using **Employee Entity**.

## Known issue

- **Issue**: When adding a new attachment to a worker, the **New** and **Edit** buttons are grayed out. 
- **Workaround:** Before opening the attachment page, make sure that the FactBoxes on the **Worker** page are closed. If the FactBoxes are closed when the **Worker** page is loaded, the attachments buttons will be enabled. (This issue will be fixed in the next platform update.)
