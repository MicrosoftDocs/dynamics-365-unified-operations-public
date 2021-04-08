---
# required metadata

title: Payroll fixed compensation plan API
description: This topic provides details and an example query for the Payroll fixed compensation plan entity in Dynamics 365 Human Resources.
author: jcart
manager: tfehr
ms.date: 04/07/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jcart
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# Payroll fixed compensation plan API

This topic provides details and an example query for the Payroll fixed compensation plan entity in Dynamics 365 Human Resources.

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Employee ID**<br>mshr_fk_employee_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key:mshr_Employee_id of mshr_payrollemployeeentity entity  | Employee ID |
| **Pay rate**<br>mshr_payrate<br>*Decimal* | Read-only<br>Required | Pay rate defined in fixed compensation plan. |
| **Plan ID**<br>mshr_planid<br>*String* | Read-only<br>Required |Specifies the compensation plan.  |
| **Valid from**<br>mshr_validfrom<br>*Date Time Offset* |  Read-only<br>Required |Date the employee fixed compensation is valid from.  |
| **Payroll Fixed Compensation Plan entity**<br>mshr_payrollfixedcompensationplanentityid<br>*GUID* | Required<br>Sytem generated | A system-generated GUID value to uniquely identify the compensation plan. |
| **Pay frequency**<br>mshr_payfrequency<br>*String* | Read-only<br>Required |The frequency the employee will be paid.  |
| **Valid to**<br>mshr_validto<br>*Date Time Offset* | Read-only <br>Required | Date the employee fixed compensation is valid to. |
| **Position ID**<br>mshr_positionid<br>*String* | Read-only <br>Required | Postion ID associated with the employee and fixed compensation plan enrollment. |
| **Currency**<br>mshr_currency<br>*String* | Read-only <br>Required |The currency defined for the fixed compensation plan   |
| **Personnel number**<br>mshr_personnelnumber<br>*String* | Read-only<br>Required |The employee's unique personnel number.  |

**Query**

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
