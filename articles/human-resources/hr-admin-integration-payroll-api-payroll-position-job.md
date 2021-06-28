---
# required metadata

title: Payroll position job
description: This topic provides details and an example query for the Payroll position job entity in Dynamics 365 Human Resources.
author: jcart
ms.date: 04/07/2021
ms.topic: article
ms.prod: 
ms.technology: 

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

This topic describes the Payroll position job entity for Dynamics 365 Human Resources.

### Description

This entity provides the relationship between position and a job for a given fixed compensation plan.

Physical name: mshr_payrollpositionjobentity.

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Job ID**<br>mshr_jobid<br>*String* | Readp-only<br>Required |The ID of the job. |
| **Valid from**<br>mshr_validto<br>*Date Time Offset* | Read-only <br>Required | Date the postion and job relationship is valid from. |
| **Valid to**<br>mshr_validto<br>*Date Time Offset* | Read-only <br>Required | Date the position and job relationship is valid to.  |
| **Position ID**<br>mshr_positionid<br>*String* | Read-only<br>Required | The ID of the position. |
| **Primary field**<br>mshr_primaryfield<br>*String* | Required<br>System generated |  |
| **Position job ID value**<br>_mshr_fk_positionjob_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key:mshr_PayrollPositionJobEntity of the mshr_payrollpositionjobentity |The ID of the job associated with the position.|
| **Fixed compensation plan ID value**<br>_mshr_fk_fixedcompplan_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_FixedCompPlan_id of mshr_payrollfixedcompensationplanentity  | The ID of the fixed compensation plan associated with the position. |
| **Payroll position job entity ID**<br>mshr_payrollpositionjobentityid<br>*Guid* | Required<br>System generated. | A system-generated GUID value to uniquely identify the job.  |

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
