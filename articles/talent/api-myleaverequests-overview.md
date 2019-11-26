---
# required metadata

title: MyLeaveRequests overview
description: This article provides a reference for the MyLeaveRequests entity.
author: gboyko
manager: AnnBe
ms.date: 11/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: 
ms.author: gboyko
ms.search.validFrom: 2019-11-15
ms.dyn365.ops.version: Talent

---

# MyLeaveRequests overview

[!include [banner](includes/banner.md)]

The MyLeaveRequests entity in Microsoft Dynamics 365 Talent provides the list of Leave Requests in the system, scoped (limited) to the requests accessible to the current user querying the entity.

## Key

  | Property Name | Data Type |
  |---------------|-----------|
  | dataAreaId    | String    |
  | RequestId     | String    |
  | LeaveType     | String    |
  | LeaveDate     | Date      |
  
## Properties

  | Property Name     | Data Type | Required |
  |-------------------|-----------|----------|
  | dataAreaId        | String    | X        |
  | RequestId         | String    | X        |
  | LeaveType         | String    | X        |
  | LeaveDate         | Date      | X        |
  | ReasonCodeId      | String    |          |
  | PersonnelNumber   | String    | X        |
  | RequestDate       | Date      | X        |
  | Comment           | String    |          |
  | Status            | Enum      | X        |
  | Amount            | Real      |          |
  | HalfDayDefinition | Enum      |          |

## Actions

 | Action Name                               | Description                                     |
 |-------------------------------------------|-------------------------------------------------|
 | [submit](api-myleaverequests-submit.md)   | Submit the request to be processed by workflow. |

## See also

[Submit a leave request to workflow](api-myleaverequests-submit.md)