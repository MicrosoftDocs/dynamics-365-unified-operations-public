---
# required metadata

title: Leave bank transaction entity
description: This article provides details and an example query for the Leave bank transaction entity in Microsoft Dynamics 365 Human Resources.
author: jcart
ms.date: 05/10/2024
ms.topic: article
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
ms.author: jcart
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# Leave bank transaction entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Leave bank transaction entity (payintv1leavebanktransactionentities) for Dynamics 365 Human Resources.

Physical name: mserp_payintv1leavebanktransactionentities

## Description

This entity provides information about the payroll position details.

## Properties 

| Property | Physical name | Type | Use |
|---|---|---|---|
| Amount | mserp_Amount | Real | Read-only |
| LeavePlan | mserp_LeavePlan | Int64 | Read-only |
| LeaveType | mserp_LeaveType | Int64 | Read-only |
| TransactionDate | mserp_TransactionDate | Datetime offset | Read-only |
| TransactionNumber | mserp_TransactionNumber | Real | Read-only |
| TransactionType | mserp_TransactionType | Enum | Read-only |
| Worker | mserp_Worker | Int64 | Read-only |
| Type | mserp_LeaveTypeId | String | Read-only |
| PersonnelNumber | mserp_PersonnelNumber | String | Read-only |
| Name | Mserp_LeavePlanId | String | Read-only |
| HalfDayDefinition | mserp_HalfDayDefinition | Enum | Read-only |
| Comment | mserp_Comment | String | Read-only |
| ReasonCode | mserp_ReasonCode | Int64 | Read-only |
| ReasonCodeId | mserp_ReasonCodeId | String | Read-only |

## Example query for the Leave bank transaction entity

Entity name: mserp_payintv1leavebanktransactionentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1leavebanktransactionentities.xml_
```

**Response**

```JSON
{  
    "mserp_amount": 0,  
    "mserp_leaveplan": 5637145327,  
    "mserp_leaveplan_bigint": 5637145327,  
    "mserp_transactiondate": "2017-01-01T00:00:00Z",  
    "mserp_transactionnumber": 1,  
    "mserp_transactiontype": 200000003,  
    "mserp_leavetypeid": "Bereavement",  
    "mserp_personnelnumber": "000001",  
    "mserp_leaveplanid": "Bereavement",  
    "mserp_halfdaydefinition": 200000000,  
    "mserp_comment": "",  
    "mserp_reasoncodeid": "",  
}
```
