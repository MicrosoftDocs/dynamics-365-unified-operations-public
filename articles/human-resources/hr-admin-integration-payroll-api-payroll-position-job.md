---
# required metadata

title: Payroll position job
description: This article provides details and an example query for the Payroll position job entity in Dynamics 365 Human Resources.
author: jcart
ms.date: 04/07/2021
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
ms.author: jcart
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# Payroll position job



[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Payroll position job entity for Dynamics 365 Human Resources.

### Description

This entity provides the relationship between position and a job for a given fixed compensation plan.

Physical name: mshr_payrollpositionjobentity.

## Properties

| Property</br>**Physical name**</br>***Type*** | Use | Description |
| --- | --- | --- |
| **Position ID**</br>mshr_positionid</br>*String* | Read-only | The ID of the position. |
| **Valid from**</br>mshr_validto</br>*Date Time Offset* | Read-only | That date that the position and job relationship is valid from. |
| **Valid to**</br>mshr_validto</br>*Date Time Offset* | Read-only | The date that the position and job relationship is valid to. |
| **Job ID**</br>mshr_jobid</br>*String* | Read-only | The ID of the job. |
| **Primary field**</br>mshr_primaryfield</br>*String* | System generated | The primary field. |
| **Payroll position job entity ID**</br>mshr_payrollpositionjobentityid</br>*Guid* | System generated. | A system-generated globally unique identifier (GUID) value to uniquely identify the job. |

## Relations

| Property value | Related entity | Navigation property | Collection type |
| --- | --- | --- | --- |
| _mshr_fk_fixedcompplan_id_value | mshr_payrollfixedcompensationplanentity | mshr_FK_FixedCompPlan_id | mshr_FK_PayrollFixedCompensationPlanEntity_Job |
| _mshr_fk_jobdetail_id_value | mshr_hcmjobdetailentity | mshr_FK_JobDetail_id | Not applicable |
| _mshr_fk_payroll_id_value | mshr_payrollpositionentity | mshr_FK_Payroll_id | mshr_FK_PayrollPositionEntity_Job |

## Example query

**Request**

```http
GET [Organizaton URI]/api/data/v9.1/mshr_payrollpositionjobentities?$filter=mshr_positionid eq '000276'
```

**Response**

```json
{
    "mshr_positionid": "000276",
    "mshr_validfrom": "2016-07-06T18:11:33Z",
    "mshr_validto": "2154-12-31T23:59:59Z",
    "mshr_jobid": "Accountant",
    "mshr_primaryfield": "000276 | Accountant | 7/6/2016 06:11:33 pm",
    "_mshr_fk_jobdetail_id_value": "00000b8d-0000-0000-b0ff-004105000000",
    "_mshr_fk_fixedcompplan_id_value": "0000058a-0000-0000-d5ff-004105000000",
    "_mshr_fk_payroll_id_value": "00000427-0000-0000-df00-014105000000",
    "mshr_payrollpositionjobentityid": "00000906-0000-0000-df00-014105000000"
}
```

## See also

[Payroll integration API introduction](hr-admin-integration-payroll-api-introduction.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
