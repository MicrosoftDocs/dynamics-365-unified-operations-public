---
# required metadata

title: What's new or changed in Dynamics 365 Talent - Core HR (November 27, 2018)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent - Core HR.
author: Darinkramer
manager: AnnBe
ms.date: 11/27/2018
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
ms.search.validFrom: 2018-11-27
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent - Core HR (November 27, 2018)

**Build 8.1.2064**

This topic describes features that are either new or changed in Core HR.


## Changes

### Unable to create a note in Case Management

A change has been made for an issue when attempting to edit or create a note in the case log of Case Management.

### Misspelled word on the analytics tab in the compensation workspace 

A change has been made to correct the spelling of 'Ethnic Origin' in the compensation analytics chart in the compensation workspace.

### Employee self-service workspace not displaying when a user isn't assigned to a worker 

A change has been made when the **Employee self-service** workspace is selected as the initial page on startup for a user who is not assigned to a worker. In this situation, the default dashboard will be displayed.

### Leave and Absence error: Object reference not set to an instance of an object

Changes have been made to Leave and Absence to correct this error after approving leave and absence records in the **Work items assigned to me** list.

### Unable to recall an image workflow

After recalling an image workflow, the workflow will be set to "cancelled" and the existing request can be deleted in the employee self-service workspace.

### Rehired employees or contractors show up multiple times after termination 

With this update, terminated employees that are rehired will only display one time in the exited list. 

## Known issue

- **Issue**: When adding a new attachment to a worker, the **New** and **Edit** buttons are grayed out. 
- **Workaround:** Before opening the attachment page, make sure that the FactBoxes on the **Worker** page are closed. If the FactBoxes are closed when the **Worker** page is loaded, the attachments buttons will be enabled. (This issue will be fixed in the next platform update.)
