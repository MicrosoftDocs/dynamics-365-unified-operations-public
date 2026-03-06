---
# required metadata

title: Leave bank transaction entity
description: This article provides details and an example query for the Leave bank transaction entity in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 05/10/2024
ms.topic: how-to
ms.reviewer: twheeloc

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# Leave bank transaction entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Leave bank transaction entity for Dynamics 365 Human Resources.

Physical name: mshr_leavebanktransactionentities

## Description

This entity provides information about the payroll position details.

## Properties 

| Property | Physical name | Type | Use |
|---|---|---|---|
| Amount | mshr_Amount | Real | Read-only |
| LeavePlan | mshr_LeavePlan | Int64 | Read-only |
| LeaveType | mshr_LeaveType | Int64 | Read-only |
| TransactionDate | mshr_TransactionDate | Datetime offset | Read-only |
| TransactionNumber | mshr_TransactionNumber | Real | Read-only |
| TransactionType | mshr_TransactionType | Enum | Read-only |
| Worker | mshr_Worker | Int64 | Read-only |
| Type | mshr_LeaveTypeId | String | Read-only |
| PersonnelNumber | mshr_PersonnelNumber | String | Read-only |
| Name | Mshr_LeavePlanId | String | Read-only |
| HalfDayDefinition | mshr_HalfDayDefinition | Enum | Read-only |
| Comment | mshr_Comment | String | Read-only |
| ReasonCode | mshr_ReasonCode | Int64 | Read-only |
| ReasonCodeId | mshr_ReasonCodeId | String | Read-only |

## Example query for the Leave bank transaction entity

Entity name: mshr_leavebanktransactionentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mshr_leavebanktransactionentities.xml_
```

**Response**

```JSON
{  
    "mshr_amount": 0,  
    "mshr_leaveplan": 5637145327,  
    "mshr_leaveplan_bigint": 5637145327,  
    "mshr_transactiondate": "2017-01-01T00:00:00Z",  
    "mshr_transactionnumber": 1,  
    "mshr_transactiontype": 200000003,  
    "mshr_leavetypeid": "Bereavement",  
    "mshr_personnelnumber": "000001",  
    "mshr_leaveplanid": "Bereavement",  
    "mshr_halfdaydefinition": 200000000,  
    "mshr_comment": "",  
    "mshr_reasoncodeid": "",  
}
```
