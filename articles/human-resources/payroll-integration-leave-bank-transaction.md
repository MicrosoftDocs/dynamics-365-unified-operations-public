---
# required metadata

title: Leave Bank Transaction entity
description: This article provides details and an example query for the Leave Bank Transaction entity in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 02/20/2026
ms.topic: article

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

# Leave Bank Transaction entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Leave Bank Transaction entity (PayIntV1LeaveBankTransactionEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the leave bank transaction.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Transactiontype | mserp_transactiontype | Enum | Read-only |
| Leaveplanid | mserp_leaveplanid | String | Read-only |
| Leaveplan | mserp_leaveplan | Real | Read-only |
| Transactionnumber | mserp_transactionnumber | Real | Read-only |
| Leaveplan Bigint | mserp_leaveplan_bigint | Int64 | Read-only |
| Comment | mserp_comment | String | Read-only |
| Dataareaid | mserp_dataareaid | String | Read-only |
| Leavetypeid | mserp_leavetypeid | String | Read-only |
| Halfdaydefinition | mserp_halfdaydefinition | Enum | Read-only |
| Transactiondate | mserp_transactiondate | Date time offset | Read-only |
| Amount | mserp_amount | Real | Read-only |
| Reasoncodeid | mserp_reasoncodeid | String | Read-only |
| Personnelnumber | mserp_personnelnumber | String | Read-only |

## Example query for PayIntV1LeaveBankTransactionEntity

Entity name: mserp_payintv1leavebanktransactionentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1leavebanktransactionentities
```

**Response**

```JSON
{  
    "mserp_transactiontype": 200000000,
    "mserp_leaveplanid": "Bereavement",
    "mserp_leaveplan": 5637145327,
    "mserp_transactionnumber": 1,
    "mserp_leaveplan_bigint": 5637145327,
    "mserp_comment": "",
    "mserp_dataareaid": "usmf",
    "mserp_leavetypeid": "Bereavement",
    "mserp_halfdaydefinition": 200000000,
    "mserp_transactiondate": "2024-01-01T00:00:00Z",
    "mserp_amount": 0,
    "mserp_reasoncodeid": "",
    "mserp_personnelnumber": "000001"
}
```
