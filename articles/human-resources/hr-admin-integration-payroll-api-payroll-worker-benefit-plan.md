---
# required metadata

title: Payroll worker benefit plan
description: This topic provides details and an example query for the Payroll worker benefit plan entity in Dynamics 365 Human Resources.
author: twheeloc
ms.date: 07/28/2021
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
ms.author: twheeloc
ms.search.validFrom: 2021-07-28
ms.dyn365.ops.version: Human Resources
---

# Payroll worker benefit plan


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes the Payroll worker benefit plan entity for Dynamics 365 Human Resources.

Physical name: mshr_payrollworkerbenefitplanentities.

### Description

This entity provides information about the benefits plan for a given worker.

## Properties

| Property</br>**Physical name**</br>***Type*** | Use | Description |
| --- | --- | --- |
| **Personnel number**</br>mshr_personnelnumber</br>*String* | Read-only</br>Required | The employee's unique personnel number. |
| **Legal entity ID**</br>mshr_legalentityID</br>*String* | Read-only | Specifies the legal entity (company). |
| **Period ID**</br>mshr_periodid</br>*String* | Read-only | The identifier of the period. |
| **Plan ID**</br>mshr_planid</br>*String* | Read-only | The identifier of the plan. |
| **Coverage option**</br>mshr_coverageoptionid</br>*String* | Read-only | Identification of the coverage option. |
| **Deduction start date**</br>mshr_deductionstartdatetime</br>*Date time offset* | Read-only | Deduction start date. |
| **Deduction end date**</br>mshr_deductionenddatetime</br>*Date time offset* | Read-only | Deduction end date. |
| **Status**</br>mshr_status</br>*[Benefit employee plan status option set](hr-admin-integration-payroll-api-benefit-employee-plan-status.md)* | Read-only | Status for the benefit plan. |
| **Valid from**</br>mshr_validfrom</br>*Date Time Offset* | Read-only | The time from which this record is valid. |
| **Valid to**</br>mshr_validto</br>*Date Time Offset* |  Read-only | The time up to which this record is valid. |
| **Plan type ID**</br>mshr_plantypeid</br>*String* | Read-only | The identifier of the plan type. |
| **Plan type code**</br>mshr_plantypecode</br>*[benefit plan type cover option set](hr-admin-integration-payroll-api-benefit-plan-type-cover.md)* | Read-only | The specification of the plan type. |
| **Number of pay periods**</br>mshr_payperiod</br>*Integer* | Read-only | The number of pay periods that represents how often the benefit provider or employees are paid. This amount will be used to calculate the employee's annual benefit salary amount. |
| **Employee amount**</br>mshr_amountemployee</br>*Decimal* | Read-only | The employee amount or percentage. |
| **Employer amount**</br>mshr_amountemployer</br>*Decimal* | Read-only | The employer amount or percentage. |
| **Primary field**</br>mshr_primaryfield</br>*String* | System generated | Primary field. |
| **Worker ID value** </br>_mshr_fk_worker_id_value</br>*GUID* | Foreign key: mshr_hcmworkerbaseentityid of mshr_hcmworkerbaseentity entity. | System-generated unique identifier for the worker. |
| **Period ID value**</br> _mshr_fk_period_id_value</br>*GUID* | Foreign key: mshr_benefitperiodentityid of mshr_benefitperiodentity entity. | System-generated unique identifier for the period. |
| **Plan ID value**</br> _mshr_fk_plan_id_value</br>*GUID* | Foreign key: mshr_benefitplanentityid of mshr_benefitplanentity entity. | System-generated unique identifier for the plan. |
| **Plan Type ID value**</br> _mshr_fk_plantype_id_value</br>*GUID* | Foreign key: mshr_benefitplantypeentityid of mshr_benefitplantypeentity entity. | System-generated unique identifier for the plan. |
| **Coverage option ID value**</br> _mshr_fk_coverageoption_id_value</br>*GUID* | Foreign key: mshr_benefitcoverageoptionentityid of mshr_benefitcoverageoptionentity entity. | System-generated unique identifier for the plan. |
| **Payroll worker benefit plan entity ID value**</br> mshr_payrollworkerbenefitplanentityid</br>*GUID* | Read-only </br> System generated | System-generated unique identifier for the record. |

## Example query for Payroll worker benefit plan

**Request**

```http
GET [Organization URI]/api/data/v9.1/mshr_payrollworkerbenefitplanentities?$filter=mshr_personnelnumber eq '000020'
```

**Response**

```json
{
    "mshr_personnelnumber": "000020",
    "mshr_legalentityid": "USMF",
    "mshr_periodid": "2021",
    "mshr_planid": "Dental plan",
    "mshr_coverageoptionid": "Emp Only",
    "mshr_deductionstartdatetime": "2021-01-01T06:00:00Z",
    "mshr_deductionenddatetime": "2021-12-31T06:00:00Z",
    "mshr_status": 200000001,
    "mshr_validfrom": "2021-01-01T06:00:00Z",
    "mshr_validto": "2021-12-31T06:00:00Z",
    "mshr_plantypeid": "Dental",
    "mshr_plantypecode": 200000001,
    "mshr_payperiod": 12,
    "mshr_amountemployee": 47,
    "mshr_amountemployer": 57,
    "mshr_primaryfield": "000020 | USMF | 2021 | Dental plan",
    "_mshr_fk_worker_id_value": "000000ae-0000-0000-bfff-004105000000",
    "_mshr_fk_period_id_value": "00000807-0000-0000-ee02-005001000000",
    "_mshr_fk_plan_id_value": "00000c61-0000-0000-0200-005001000000",
    "_mshr_fk_plantype_id_value": "0000057c-0000-0000-0200-005001000000",
    "_mshr_fk_coverageoption_id_value": "00000391-0000-0000-0b00-005001000000",
    "mshr_payrollworkerbenefitplanentityid": "000006c4-0000-0000-bfff-004105000000"
}
```
## See also

[Payroll integration API introduction](hr-admin-integration-payroll-api-introduction.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
