---
# required metadata

title: Payroll fixed compensation plan
description: This topic provides details and an example query for the Payroll fixed compensation plan entity in Dynamics 365 Human Resources.
author: jcart
ms.date: 08/25/2021
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

# Payroll fixed compensation plan


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes the Payroll fixed compensation plan entity for Dynamics 365 Human Resources.

### Description

This entity provides the fixed compensation plan assigned for a given position of an employee.

Physical name: mshr_payrollfixedcompensationplanentity.

## Properties

| Property</br>**Physical name**</br>***Type*** | Use | Description |
| --- | --- | --- |
| **Plan ID**</br>mshr_planid</br>*String* | Read-only | Specifies the compensation plan.  |
| **Personnel number**</br>mshr_personnelnumber</br>*String* | Read-only | The employee's unique personnel number. |
| **Pay rate**</br>mshr_payrate</br>*Decimal* | Read-only | Pay rate defined in fixed compensation plan. |
| **Position ID**</br>mshr_positionid</br>*String* | Read-only | Position ID associated with the employee and fixed compensation plan enrollment. |
| **Valid from**</br>mshr_validfrom</br>*Date Time Offset* |  Read-only | Date the employee fixed compensation is valid from.  |
| **Valid to**</br>mshr_validto</br>*Date Time Offset* | Read-only | Date the employee fixed compensation is valid to. |
| **Pay frequency**</br>mshr_payfrequency</br>*String* | Read-only | The ID of the [compensation pay frequency](hr-admin-integration-payroll-api-compensation-pay-frequency.md) for the given pay rate. |
| **Currency**</br>mshr_currency</br>*String* | Read-only | The currency defined for the fixed compensation plan. |
| **Payroll Fixed Compensation Plan entity**</br>mshr_payrollfixedcompensationplanentityid</br>*GUID* | System generated | A system-generated GUID value to uniquely identify the compensation plan. |

## Relations

|Property value | Related entity | Navigation property | Collection type |
| --- | --- | --- | --- |
| _mshr_fk_employee_id_value | [mshr_payrollemployeeentity](hr-admin-integration-payroll-api-payroll-employee.md) | mshr_FK_Employee_id | mshr_FK_PayrollEmployeeEntity_FixedCompPlan |
| _mshr_fk_job_id_value | [mshr_payrollpositionjobentity](hr-admin-integration-payroll-api-payroll-position-job.md) | mshr_FK_Job_id | mshr_FK_PayrollPositionJobEntity_FixedCompPlan |
| _mshr_fk_payrollposition_id_value | [mshr_payrollpositionentity](hr-admin-integration-payroll-api-payroll-position.md) | mshr_FK_PayrollPosition_id | mshr_FK_PayrollPositionEntity_FixedCompPlan |
| _mshr_fk_plan_id_value | mshr_hcmcompfixedplantableentity | mshr_FK_Plan_id | - |
| _mshr_fk_variablecompaward_id_value | [mshr_payrollvariablecompensationawardentity](hr-admin-integration-payroll-api-payroll-variable-compensation-plan.md) | mshr_FK_VariableCompAward_id | mshr_FK_PayrollVariableCompensationAwardEntity_FixedComp |

## Example query

**Request**

```http
GET [Organizaton URI]/api/data/v9.1/mshr_payrollfixedcompensationplanentities?$filter=mshr_personnelnumber eq @personnelnumber and mshr_validfrom le @asofdate and mshr_validto ge @asofdate&@personnelnumber='000041'&@asofdate=2021-04-01
```

**Response**

```json
{
    "mshr_planid": "GradeC",
    "mshr_personnelnumber": "000041",
    "mshr_payrate": 75200,
    "mshr_positionid": "000276",
    "mshr_validfrom": "2011-04-05T00:00:00Z",
    "mshr_validto": "2154-12-31T00:00:00Z",
    "mshr_payfrequency": "Annual",
    "mshr_currency": "USD",
    "_mshr_fk_employee_id_value": "00000d3c-0000-0000-d5ff-004105000000",
    "_mshr_fk_plan_id_value": "0000070c-0000-0000-b328-fef003000000",
    "_mshr_fk_job_id_value": "00010094-0000-0000-df00-014105000000",
    "mshr_payrollfixedcompensationplanentityid": "0000029f-0000-0000-d5ff-004105000000",
    "_mshr_fk_payroll_id_value": null
}
```

## See also

[Payroll integration API introduction](hr-admin-integration-payroll-api-introduction.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
