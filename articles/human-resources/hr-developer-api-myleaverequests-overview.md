---
# required metadata

title: MyLeaveRequests overview
description: The MyLeaveRequests entity in Microsoft Dynamics 365 Human Resources provides the list of Leave Requests.
author: twheeloc
ms.date: 07/09/2024
ms.topic: overview
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 

ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ajitchandran
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# MyLeaveRequests overview



[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

The MyLeaveRequests entity in Microsoft Dynamics 365 Human Resources provides the list of Leave Requests in the system, scoped (limited) to the requests accessible to the current user querying the entity.

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
 | [submit](hr-developer-api-myleaverequests-submit.md)   | Submit the request to be processed by workflow. |

## See also

- [Submit a leave request to workflow](hr-developer-api-myleaverequests-submit.md)
- [Authentication](hr-developer-api-authentication.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
