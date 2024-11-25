---
# required metadata

title: Payroll position details entity
description: This article provides details and an example query for the Payroll position details entity in Microsoft Dynamics 365 Human Resources.
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

# Payroll position details entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Payroll position details entity (payintv1payrollpositiondetailsentities) for Dynamics 365 Human Resources.

Physical name: mserp_payintv1payrollpositiondetailsentities

## Description

This entity provides information about the payroll position details.

## Properties

| Property | Physical name | Type | Use |
|---|---|---|---|
| IsSalaryGenerated | mserp_IsSalaryGenerated | Enum | Read-only |
| DefaultEarningCode | mserp_DefaultEarningCode | Int64 | Read-only |
| InsuranceBenefit | mserp_InsuranceBenefit | Int64 | Read-only |
| AreEarningsGeneratedFromSchedule | mesrp_areEarningsGeneratedFromSchedule | Enum | Read-only |
| LegalEntity | mserp_LegalEntity | Int64 | Read-only |
| PayCycle | mserp_PayCycle | Int64 | Read-only |
| AnnualRegularHours | mserp_AnnualRegularHours | Real | Read-only |
| PayPeriodOvertimeHours | mserp_PayPeriodOvertimeHours | Real | Read-only |
|Positions| mserp_Positions | Int64 | Read-only |
| Schedule| mserp_Schedule | String | Read-only |
| ScheduleLegalEntity | mserp_ScheduleLegalEntity |String | Read-only |
| ValidFrom| mserp_ValidFrom |Datetime offset | Read-only |
| ValidTo| mserp_ValidTo |  Datetime offset | Read-only |
| BenefitId| mserp_BenefitId | String | Read-only |
| PaidByLegalEntity| mserp_PaidByLegalEntity | String | Read-only |
| DefaultEarningCodeId| mserp_DefaultEarningCodeId  | String | Read-only |
| PayCycleId| mserp_PayCycleId | String | Read-only |
| PositionId | mserp_PositionId | String | Read-only |

## Example query for the Payroll position details entity

Entity name: mserp_payintv1payrollpositiondetailsentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1payrollpositiondetailsentities
```

**Response**

```JSON
{  
    "mserp_issalarygenerated": 200000000,  
    "mserp_areearningsgeneratedfromschedule": 200000001,  
    "mserp_paycycle": 5637145336,  
    "mserp_paycycle_bigint": 5637145336,  
    "mserp_annualregularhours": 2080,  
    "mserp_payperiodovertimehours": 0,  
    "mserp_schedule": "Payroll",  
    "mserp_schedulelegalentity": "USMF",  
    "mserp_validfrom": "2005-01-01T00:00:00Z",  
    "mserp_validto": "2154-12-31T00:00:00Z",  
    "mserp_benefitid": "",  
    "mserp_paidbylegalentity": "USMF",  
    "mserp_defaultearningcodeid": "Regular",  
    "mserp_paycycleid": "w",  
    "mserp_positionid": "000001",  
    "mserp_primaryfield": "000001 | 1/1/2005 | 12/31/2154",  
}
```
