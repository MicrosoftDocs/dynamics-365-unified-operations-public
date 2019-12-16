---
# required metadata

title: MyLeaveRequests overview
description: 
author: andreabichsel
manager: AnnBe
ms.date: 02/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-01
ms.dyn365.ops.version: Human Resources April 2020 update

---

# MyLeaveRequests overview

**Status**

| Description | Status | Notes |
| --- | --- | --- |
| Draft | In progress |  |
| Verify procedures |  |  |
| Change links |  |  |
| Update screenshots | NA |  |
| Add See also links | Complete |  |
| Run Acrolinx | Yes |  |
| Review |  |  |
| Edit |  |  |
| Ready to publish |  |  |

**Notes for Reviewers**

| Description | Comments |
| --- | --- |
| From existing topic? | [MyLeaveRequestsOverview](https://docs.microsoft.com/en-us/dynamics365/talent/api-myleaverequests-overview) |
| Review document location | (link) |

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