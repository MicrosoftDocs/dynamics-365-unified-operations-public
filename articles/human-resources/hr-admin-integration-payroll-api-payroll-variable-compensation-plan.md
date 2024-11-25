---
# required metadata

title: Payroll variable compensation plan
description: This article provides details and an example query for the Payroll variable compensation plan entity in Dynamics 365 Human Resources.
author: twheeloc
ms.date: 06/15/2021
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
ms.search.validFrom: 2021-06-15
ms.dyn365.ops.version: Human Resources
---

# Payroll variable compensation plan



[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Payroll variable compensation plan entity for Dynamics 365 Human Resources.

### Description

This entity provides the variable compensation plan assigned for a given position of an employee.

Physical name: mshr_payrollvariablecompensationawardentity.

## Properties

| Property</br>**Physical name**</br>***Type*** | Use | Description |
| --- | --- | --- |
| **Personnel number**</br>mshr_personnelnumber</br>*String* | Read-only | The employee's unique personnel number.  |
| **Award date**</br>mshr_awarddate</br>*Date Time Offset* | Read-only | Date of the award. |
| **Award type**</br>mshr_awardtype</br>*[mshr_HrmCompVarAwardEmplType option set](hr-admin-integration-payroll-api-award-type.md)* | Read-only | The type of the award defined for the variable compensation plan. |
| **Currency**</br>mshr_unitcurrencycode</br>*String* | Read-only |The currency defined for the variable compensation plan.   |
| **Fixed compensation plan ID**</br>mshr_fixedplanid</br>*String* | Read-only | The fixed compensation plan that is used as a basis for the calculation of the award. |
| **Unit value**</br>mshr_awardamount</br>*Decimal* | Read-only | The value of the unit |
| **Process type**</br>mshr_processtype</br>*[mshr_hrmCompProcessType option set](hr-admin-integration-payroll-api-process-type.md)* | Read-only | The process type. |
| **Variable compensation plan type**</br>String</br>*mshr_typeid* | Read-only | The type of the variable compensation plan. |
| **Variable compensation plan ID**</br>String</br>*mshr_planid* | Read-only | The id of the variable compensation plan. |
| **Number of units**</br>Decimal</br>*mshr_numberofunits* | Read-only | The number of units of the award. |
| **Primary field**</br>mshr_primaryfield</br>*GUID* | Read-only</br>System generated. | |
| **Payroll Variable Compensation Plan entity**</br>mshr_payrollvariablecompensationawardentityid</br>*GUID* | System generated | A system-generated GUID value to uniquely identify the compensation plan. |

## Relations 

|Property value | Related entity | Navigation property | Collection type |
| --- | --- | --- | --- |
| _mshr_fk_employee_id_value | [mshr_payrollemployeeentity](hr-admin-integration-payroll-api-payroll-employee.md) | mshr_FK_Employee_id | mshr_FK_PayrollEmployeeEntity_VariableCompAward |
| _mshr_fk_fixedcomp_id_value | [mshr_payrollfixedcompensationplanentity](hr-admin-integration-payroll-api-payroll-fixed-compensation-plan.md) | mshr_FK_FixedComp_id | mshr_FK_PayrollFixedCompensationPlanEntity_VariableCompAward |

## Example query

**Request**

```http
GET [Organizaton URI]/api/data/v9.1/mshr_payrollvariablecompensationawardentities?$filter=mshr_personnelnumber eq '000046'
```

**Response**

```json
{
    "mshr_personnelnumber": "000046",
    "mshr_awarddate": "2015-01-15T00:00:00Z",
    "mshr_awardtype": 200000000,
    "mshr_unitcurrencycode": "USD",
    "mshr_fixedplanid": "",
    "mshr_unitvalue": 1,
    "mshr_processtype": 200000003,
    "mshr_typeid": "Bonus",
    "mshr_planid": "MgBonus",
    "mshr_numberofunits": 1500,
    "mshr_primaryfield": "000046 | MgBonus | Bonus | 1/15/2015",
    "_mshr_fk_employee_id_value": "00000666-0000-0000-daff-004105000000",
    "mshr_payrollvariablecompensationawardentityid": "000001a4-0000-0000-0d00-005001000000",
    "_mshr_fk_fixedcomp_id_value": null
}
```

## See also

[Payroll integration API introduction](hr-admin-integration-payroll-api-introduction.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
