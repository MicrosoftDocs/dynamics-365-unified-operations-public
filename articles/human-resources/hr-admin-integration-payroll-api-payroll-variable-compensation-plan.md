---
# required metadata

title: Payroll variable compensation plan
description: This topic provides details and an example query for the Payroll variable compensation plan entity in Dynamics 365 Human Resources.
author: marcelbf
ms.date: 06/15/2021
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
ms.author: marcelbf
ms.search.validFrom: 2021-06-15
ms.dyn365.ops.version: Human Resources
---

# Payroll variable compensation plan

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic provides details and an example query for the Payroll variable compensation plan entity in Dynamics 365 Human Resources.

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Personnel number**<br>mshr_personnelnumber<br>*String* | Read-only<br>Required |The employee's unique personnel number.  |
| **Award date**<br>mshr_awarddate<br>*Date Time Offset* | Read-only<br>Required | Date of the award |
| **Award type**<br>mshr_awardtype<br>*mshr_awardtype option set* | Read-only<br>Required | The type of the award defined for the variable compensation plan |
| **Currency**<br>mshr_unitcurrencycode<br>*String* | Read-only <br>Required |The currency defined for the variable compensation plan   |
| **Fixed compensation plan ID**<br>mshr_fixedplanid<br>*String* | Read-only | The fixed compensation plan that is used as a basis for the calculation of the award |
| **Unit value**<br>mshr_awardamount<br>*Decimal* | Read-only | The value of the unit |
| **Process type**<br>mshr_processtype<br>*mshr_processtype option set* | Read-only | The process type |
| **Variable compensation plan type**<br>String<br>*mshr_typeid* | Read-only | The type of the variable compensation plan |
| **Variable compensation plan ID**<br>String<br>*mshr_planid* | Read-only | The id of the variable compensation plan |
| **Primary field**<br>mshr_primaryfield<br>*GUID* | Read-only<br>System generated | |
| **Employee ID**<br>mshr_fk_employee_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key:mshr_Employee_id of mshr_payrollemployeeentity entity  | Employee ID |
| **Payroll Variable Compensation Plan entity**<br>mshr_payrollvariablecompensationawardentityid<br>*GUID* | Required<br>Sytem generated | A system-generated GUID value to uniquely identify the compensation plan. |


**Query**

**Request**

```http
GET [Organizaton URI]/api/data/v9.1/mshr_payrollvariablecompensationawardentities?$filter=mshr_personnelnumber eq '000001'
```

**Response**

```json
{
            "mshr_personnelnumber": "000001",
            "mshr_awarddate": "2015-01-15T00:00:00Z",
            "mshr_awardtype": 200000000,
            "mshr_unitcurrencycode": "USD",
            "mshr_fixedplanid": "",
            "mshr_awardamount": 1,
            "mshr_processtype": 200000003,
            "mshr_typeid": "Bonus",
            "mshr_planid": "MgBonus",
            "mshr_primaryfield": "000001 | MgBonus | Bonus | 1/15/2015",
            "_mshr_fk_employee_id_value": "00000655-0000-0000-adff-004105000000",
            "mshr_payrollvariablecompensationawardentityid": "000001a1-0000-0000-adff-004105000000",
            "_mshr_fk_fixedcomp_id_value": null
}
```
