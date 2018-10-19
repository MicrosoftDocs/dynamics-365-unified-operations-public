---
# required metadata

title: What's new or changed in Dynamics 365 for Talent Core HR (October 16, 2018)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent Core HR.
author: Darinkramer
manager: AnnBe
ms.date: 10/19/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2018-10-19
ms.dyn365.ops.version: Talent

---
# "What's new or changed in Dynamics 365 for Talent Core HR (October 19, 2018)"

[!include [banner](includes/banner.md)]

**Build 8.1.1067**

This topic describes features that are either new or changed in Core HR.

## Allow managers to update time off requests

Employee time off requests may need to be updated after they are approved through workflow. In many cases, the manager makes these updates on the employee’s behalf. This feature provides the ability for managers to update time off or cancel time off requests on behalf of their employees. This capability is controlled by the work on behalf parameter that can be set by company in the Human Resource Parameters form. 
 
## Allow HR to update time off requests

Similar to "Allow managers to update time off requests" Employee time off requests may need to be updated after they are approved through workflow. In many cases, the HR person makes these updates on the employee’s behalf. This featur provides the ability for HR users to update time off requests. This is enabled in the people workspace and on the worker form with a new option called "View time off". In these pages HR can view requests and leave transactions with the ability to update.

The security duty that controls access to this functionality:
	Duty: Maintain worker-specific leave and absence processes
	Privilege: Maintain leave and absence requests for all workers

## Other changes

## Changes to worker hire actions that are "stuck" in "Workflow complete" state
## Employment record can be createed without an employment start date
## Dynamics 365 Talent registration date of Course shown in Employee self-service is not correct based on timezone offset
## Import Excel file twice without any changes errors using Employee Entity

## Known issue

**Issue:** When adding a new attachment to a worker, the **New** and **Edit** buttons are grayed out. **Workaround:** Before opening the attachment page, make sure that the FactBoxes on the **Worker** page are closed. If the FactBoxes are closed when the **Worker** page is loaded, the attachments buttons will be enabled. (This issue will be fixed in the next platform update.)
