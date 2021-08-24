---
# required metadata

title: Payroll fixed compensation plan
description: This topic provides details and an example query for the Payroll fixed compensation plan entity in Dynamics 365 Human Resources.
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

# Payroll fixed compensation plan

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes the Payroll fixed compensation plan entity for Dynamics 365 Human Resources.

### Description

This entity provides the fixed compensation plan assigned for a given position of an employee.

Physical name: mshr_payrollfixedcompensationplanentity.

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Employee ID**<br>mshr_fk_employee_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key:mshr_Employee_id of mshr_payrollemployeeentity entity  | Employee ID |
| **Pay rate**<br>mshr_payrate<br>*Decimal* | Read-only<br>Required | Pay rate defined in fixed compensation plan. |
| **Plan ID**<br>mshr_planid<br>*String* | Read-only<br>Required |Specifies the compensation plan.  |
| **Valid from**<br>mshr_validfrom<br>*Date Time Offset* |  Read-only<br>Required |Date the employee fixed compensation is valid from.  |
| **Payroll Fixed Compensation Plan entity**<br>mshr_payrollfixedcompensationplanentityid<br>*GUID* | Required<br>System generated | A system-generated GUID value to uniquely identify the compensation plan. |
| **Pay frequency**<br>mshr_payfrequency<br>*String* | Read-only<br>Required |The frequency the employee will be paid.  |
| **Valid to**<br>mshr_validto<br>*Date Time Offset* | Read-only <br>Required | Date the employee fixed compensation is valid to. |
| **Position ID**<br>mshr_positionid<br>*String* | Read-only <br>Required | Position ID associated with the employee and fixed compensation plan enrollment. |
| **Currency**<br>mshr_currency<br>*String* | Read-only <br>Required |The currency defined for the fixed compensation plan   |
| **Personnel number**<br>mshr_personnelnumber<br>*String* | Read-only<br>Required |The employee's unique personnel number.  |

## Relations

|Property value | Related entity | Navigation Property | Collection type |
| --- | --- | --- | --- |
| _mshr_fk_employment_id_value | mshr_hcmemploymentdetailentity | mshr_FK_Employment_id | - |
| _mshr_fk_fixedcompplan_id_value | mshr_payrollfixedcompensationplanentity | mshr_FK_FixedCompPlan_id | mshr_FK_PayrollFixedCompensationPlanEntity_Employee |
| _mshr_fk_name_id_value | mshr_dirpersonnamehistoricalentity | mshr_FK_Name_id | - |
| _mshr_fk_worker_id_value | mshr_hcmworkerbaseentity | mshr_FK_Worker_id | - |
| _mshr_fk_workerbankaccount_id_value | mshr_hcmworkerbankaccountentity | mshr_FK_WorkerBankAccount_id |
| _mshr_fk_variablecompaward_id_value | mshr_payrollvariablecompensationawardentity | mshr_FK_VariableCompAward_id | mshr_FK_PayrollVariableCompensationAwardEntity_Employee |
| _mshr_fk_address_id_value | mshr_payrollworkeraddressentity | mshr_FK_Address_id | mshr_FK_PayrollWorkerAddressEntity_Worker |

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
