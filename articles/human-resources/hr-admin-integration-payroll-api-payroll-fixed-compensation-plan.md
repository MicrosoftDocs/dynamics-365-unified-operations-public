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
| **Employee ID**<br>mshr_fk_employee_id_value<br>*GUID* | EDM<br>Required |  |
| **Pay rate**<br>mshr_payrate<br>*GUID* | Decimal<br>Required |  |
| **Plan ID**<br>mshr_planid<br>*GUID* | String<br>Required |  |
| **Valid from**<br>mshr_validfrom<br>*GUID* | Date Time Offset <br>Required |  |
| **Payroll Fixed Compensation Plan ID**<br>mshr_payrollfixedcompensationplanentityid<br>*GUID* | Int32<br>Required |  |
| **Pay frequency**<br>mshr_payfrequency<br>*GUID* | String<br>Required |  |
| **Valid to**<br>mshr_validto<br>*GUID* | Date Time Offset <br>Required |  |
| **Position ID**<br>mshr_positionid<br>*GUID* | Date Time Offset <br>Required |  |
| **Currency**<br>mshr_currency<br>*GUID* | String <br>Required |The identifcation number defined for the employee.  |
| **Personnel number**<br>mshr_personnelnumber<br>*GUID* | String<br>Required |  |

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