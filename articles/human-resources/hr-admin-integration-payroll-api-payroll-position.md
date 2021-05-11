---
# required metadata

title: Payroll details for Positions
description: This topic provides details and an example query for the Payroll details for the Positions entity in Dynamics 365 Human Resources.
author: jcart
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

# Payroll position

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic provides details and an example query for the Payroll details for the Positions entity in Dynamics 365 Human Resources.

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Annual regular hours**<br>annualregularhours<br>*Decimal* | Read-only<br>Required | Annual regular hours defined on the position.  |
| **Payroll position details entity ID**<br>payrollpositiondetailsentityid<br>*Guid* | Required<br>System generated. | A system-generated GUID value to uniquely identify the position.  |
| **Primary field**<br>mshr_primaryfield<br>*String* | Required<br>System generated |  |
| **Position job ID value**<br>_mshr_fk_positionjob_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key:mshr_PayrollPositionJobEntity of the mshr_payrollpositionjobentity |The ID of the job associated with the position.|
| **Fixed compensation plan ID value**<br>_mshr_fk_fixedcompplan_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_FixedCompPlan_id of mshr_payrollfixedcompensationplanentity  | The ID of the fixed compensation plan associated with the position. |
| **Pay cycle ID**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | The pay cycle defined on the position. |
| **Paid by legal entity**<br>paidbylegalentity<br>*String* | Read-only<br>Required | The legal entity defined on the positoin responsible for issuing payment. |
| **Position ID**<br>mshr_positionid<br>*String* | Read-only<br>Required | The ID of the position. |
| **Valid to**<br>validto<br>*Date Time Offset* | Read-only<br>Required |The date the position details are valid from.  |
| **Valid from**<br>validfrom<br>*Date Time Offset* | Read-only<br>Required |The date the position details are valid to.  |

**Query**

**Request**

```http
GET [Organizaton URI]/api/data/v9.1/mshr_payrollpositionentities?$filter=mshr_positionid eq @positionid and mshr_validfrom le @asofdate and mshr_validto ge @asofdate&@positionid='000276'&@asofdate=2021-04-01
```

**Response**

```json
{
            "mshr_positionid": "000276",
            "mshr_paycycleid": "w",
            "mshr_annualregularhours": 3000,
            "mshr_paidbylegalentity": "USMF",
            "mshr_validfrom": "2021-03-14T00:00:00Z",
            "mshr_validto": "2154-12-31T00:00:00Z",
            "mshr_primaryfield": "000276 | 3/14/2021",
            "_mshr_fk_job_id_value": "00010094-0000-0000-df00-014105000000",
            "_mshr_fk_fixedcompplan_id_value": "0000029f-0000-0000-d5ff-004105000000",
            "mshr_payrollpositionentityid": "00010097-0000-0000-df00-014105000000"
}
```
