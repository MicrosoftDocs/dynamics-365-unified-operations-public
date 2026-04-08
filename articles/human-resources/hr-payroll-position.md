---
# required metadata

title: Payroll position details entity
description: This article provides details and an example query for the Payroll position details entity in Microsoft Dynamics 365 Human Resources.
author: avanish2821
ms.date: 03/25/2026
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
ms.author: twheeloc
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# Payroll position details entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Payroll position details entity for Dynamics 365 Human Resources.

Physical name: mshr_payrollpositiondetailsentities

## Description

This entity provides information about the payroll position details.

## Properties

| Property | Physical name | Type | Use |
|---|---|---|---|
| IsSalaryGenerated | mshr_IsSalaryGenerated | Enum | Read-only |
| DefaultEarningCode | mshr_DefaultEarningCode | Int64 | Read-only |
| InsuranceBenefit | mshr_InsuranceBenefit | Int64 | Read-only |
| AreEarningsGeneratedFromSchedule | mshr_areEarningsGeneratedFromSchedule | Enum | Read-only |
| LegalEntity | mshr_LegalEntity | Int64 | Read-only |
| PayCycle | mshr_PayCycle | Int64 | Read-only |
| AnnualRegularHours | mshr_AnnualRegularHours | Real | Read-only |
| PayPeriodOvertimeHours | mshr_PayPeriodOvertimeHours | Real | Read-only |
|Positions| mshr_Positions | Int64 | Read-only |
| Schedule| mshr_Schedule | String | Read-only |
| ScheduleLegalEntity | mshr_ScheduleLegalEntity |String | Read-only |
| ValidFrom| mshr_ValidFrom |Datetime offset | Read-only |
| ValidTo| mshr_ValidTo |  Datetime offset | Read-only |
| BenefitId| mshr_BenefitId | String | Read-only |
| PaidByLegalEntity| mshr_PaidByLegalEntity | String | Read-only |
| DefaultEarningCodeId| mshr_DefaultEarningCodeId  | String | Read-only |
| PayCycleId| mshr_PayCycleId | String | Read-only |
| PositionId | mshr_PositionId | String | Read-only |

## Example query for the Payroll position details entity

Entity name: mshr_payrollpositiondetailsentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mshr_payrollpositiondetailsentities
```

**Response**

```JSON
{  
    "mshr_issalarygenerated": 200000000,  
    "mshr_areearningsgeneratedfromschedule": 200000001,  
    "mshr_paycycle": 5637145336,  
    "mshr_paycycle_bigint": 5637145336,  
    "mshr_annualregularhours": 2080,  
    "mshr_payperiodovertimehours": 0,  
    "mshr_schedule": "Payroll",  
    "mshr_schedulelegalentity": "USMF",  
    "mshr_validfrom": "2005-01-01T00:00:00Z",  
    "mshr_validto": "2154-12-31T00:00:00Z",  
    "mshr_benefitid": "",  
    "mshr_paidbylegalentity": "USMF",  
    "mshr_defaultearningcodeid": "Regular",  
    "mshr_paycycleid": "w",  
    "mshr_positionid": "000001",  
    "mshr_primaryfield": "000001 | 1/1/2005 | 12/31/2154",  
}
```
