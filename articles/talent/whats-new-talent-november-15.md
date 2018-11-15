---
# required metadata

title: What's new or changed in Dynamics 365 for Talent Core HR (November 15, 2018)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent Core HR.
author: Darinkramer
manager: AnnBe
ms.date: 11/15/2018
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
ms.search.validFrom: 2018-11-15
ms.dyn365.ops.version: Talent

---
# "What's new or changed in Dynamics 365 for Talent Core HR (November 15, 2018)"

[!include [banner](includes/banner.md)]

**Build 8.1.2045**

This topic describes features that are either new or changed in Core HR.

## Other changes/fixes

### Not possible to change employee´s current position to a future open position

A change has been made to enable position transfers when the position is only avialble in the future. 

### Position does not display when creating a new employee.

A change has been made to display all open positions that are available for assignment when hiring new employees in Talent. This includes historical positions or if they have been future dataed. Positions will now appear correctly based on the employment start date entered. 

### Termination date is displaying based on user settings

A change has been made to the past employees list to account for any timezone offsets for the employees preferred timezone when viewing the termination date.

### Work Items Assigned to me links not displaying the correct information

This issue only occured with advanced security options. With this change, navigation to the details of the individual work items in the list will display the correct information for the item selected.


### Known issue
- **Issue**: When adding a new attachment to a worker, the **New** and **Edit** buttons are grayed out. 
- **Workaround:** Before opening the attachment page, make sure that the FactBoxes on the **Worker** page are closed. If the FactBoxes are closed when the **Worker** page is loaded, the attachments buttons will be enabled. (This issue will be fixed in the next platform update.)
