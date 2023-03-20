---
# required metadata

title: Leave balance
description: This article provides details and an example query for the leave balance entity in Dynamics 365 Human Resources.
author: marcelbf
ms.date: 03/20/2023
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
ms.search.validFrom: 2021-06-25
ms.dyn365.ops.version: Human Resources
---

# Leave balance


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the leave balance entity for Dynamics 365 Human Resources.

### Description

This entity provides the leave balance per leave type for a given employee.

Physical name: mshr_essleavebalanceentity.

## Properties

| Property</br>**Physical name**</br>***Type*** | Use | Description |
| --- | --- | --- |
| **Personnel number**</br>mshr_personnelnumber</br>*String* | Read-only | The employee's unique personnel number. |
| **Current balance**</br>mshr_balanceavailable</br>*Decimal* | Read-only | The employee's current balance. |
| **Type**</br>mshr_balanceavailable</br>*String* | Read-only | The leave type ID. |
| **Accrual rate**</br>mshr_accrualratedescription</br> | Read-only | The accrual rate. |
| **Last carry-forward amount**</br>mshr_lastcarryforwardamount</br>*Decimal* | Read-only | The last carry-forward amount. |
| **Taken this year**</br>mshr_takenthisyear</br>*Decimal* | Read-only | The amount of leave taken this year. |
| **Total this year**</br>mshr_totalthisyear</br>*Decimal* | Read-only | The total amount for this year. |
| **Data area ID**</br>mshr_dataareaid_id</br>*String* | Read-only | Specifies the legal entity (company). |
| **Primary field**</br>mshr_primaryfield</br>*GUID* | Read-only</br>System generated | |
| **Leave type Id**</br>_mshr_fk_leavetype_id_value</br>*GUID* | Read-only</br>Foreign key:mshr_essleavetypeentityid of mshr_essleavetypeentity entity  | Leave type ID |
| **Leave balance entity**</br>mshr_essleavebalanceentityid</br>*GUID* | System generated | A system-generated GUID value to uniquely identify the balance. |

## Example query

**Request**

```http
GET [Organizaton URI]/api/data/v9.1/mshr_essleavebalanceentities?$filter=mshr_personnelnumber eq '000013'
```

**Response**

```json
{
    "mshr_personnelnumber": "000013",
    "mshr_balanceavailable": 67.76,
    "mshr_leavetypeid": "PTO",
    "mshr_accrualratedescription": "6.16 hrs / Semimonthly",
    "mshr_lastcarryforwardamount": 0,
    "mshr_takenthisyear": 0,
    "mshr_totalthisyear": 67.76,
    "mshr_dataareaid": "usmf",
    "mshr_primaryfield": "000013 | PTO",
    "_mshr_fk_leavetype_id_value": "00000a6c-0000-0000-0000-005001000000",
    "mshr_essleavebalanceentityid": "0000091f-0000-0000-2703-005001000000",
    "_mshr_dataareaid_id_value": null
},
{
    "mshr_personnelnumber": "000013",
    "mshr_balanceavailable": 80,
    "mshr_leavetypeid": "Sick",
    "mshr_accrualratedescription": "80.00 hrs / Annually",
    "mshr_lastcarryforwardamount": 0,
    "mshr_takenthisyear": 0,
    "mshr_totalthisyear": 80,
    "mshr_dataareaid": "usmf",
    "mshr_primaryfield": "000013 | Sick",
    "_mshr_fk_leavetype_id_value": "00000a6c-0000-0000-ee02-005001000000",
    "mshr_essleavebalanceentityid": "0000091f-0000-0000-3003-005001000000",
    "_mshr_dataareaid_id_value": null
},
{
    "mshr_personnelnumber": "000013",
    "mshr_balanceavailable": 0,
    "mshr_leavetypeid": "Bereavement",
    "mshr_accrualratedescription": "0.00 hrs / Annually",
    "mshr_lastcarryforwardamount": 0,
    "mshr_takenthisyear": 0,
    "mshr_totalthisyear": 0,
    "mshr_dataareaid": "usmf",
    "mshr_primaryfield": "000013 | Bereavement",
    "_mshr_fk_leavetype_id_value": "00000a6c-0000-0000-f402-005001000000",
    "mshr_essleavebalanceentityid": "0000091f-0000-0000-4403-005001000000",
    "_mshr_dataareaid_id_value": null
},
{
    "mshr_personnelnumber": "000013",
    "mshr_balanceavailable": 66.65,
    "mshr_leavetypeid": "Vacation",
    "mshr_accrualratedescription": "13.33 hrs / Monthly",
    "mshr_lastcarryforwardamount": 0,
    "mshr_takenthisyear": 0,
    "mshr_totalthisyear": 66.65,
    "mshr_dataareaid": "usmf",
    "mshr_primaryfield": "000013 | Vacation",
    "_mshr_fk_leavetype_id_value": "00000a6c-0000-0000-f502-005001000000",
    "mshr_essleavebalanceentityid": "0000091f-0000-0000-1009-005001000000",
    "_mshr_dataareaid_id_value": null
}
```

## See also

[Payroll integration API introduction](hr-admin-integration-payroll-api-introduction.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
