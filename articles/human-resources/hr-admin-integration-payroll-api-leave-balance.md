---
# required metadata

title: Leave balance
description: This article provides details and an example query for the leave balance entity in Dynamics 365 Human Resources.
author: avanish2821
ms.date: 03/25/2026
ms.topic: how-to
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



[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the leave balance entity for Dynamics 365 Human Resources.

### Description

This entity provides the leave balance per leave type for a given employee.

Physical name: mserp_essleavebalanceentity.

## Properties

| Property</br>**Physical name**</br>***Type*** | Use | Description |
| --- | --- | --- |
| **Personnel number**</br>mserp_personnelnumber</br>*String* | Read-only | The employee's unique personnel number. |
| **Current balance**</br>mserp_balanceavailable</br>*Decimal* | Read-only | The employee's current balance. |
| **Type**</br>mserp_balanceavailable</br>*String* | Read-only | The leave type ID. |
| **Accrual rate**</br>mserp_accrualratedescription</br> | Read-only | The accrual rate. |
| **Last carry-forward amount**</br>mserp_lastcarryforwardamount</br>*Decimal* | Read-only | The last carry-forward amount. |
| **Taken this year**</br>mserp_takenthisyear</br>*Decimal* | Read-only | The amount of leave taken this year. |
| **Total this year**</br>mserp_totalthisyear</br>*Decimal* | Read-only | The total amount for this year. |
| **Data area ID**</br>mserp_dataareaid_id</br>*String* | Read-only | Specifies the legal entity (company). |
| **Primary field**</br>mserp_primaryfield</br>*GUID* | Read-only</br>System generated | |
| **Leave type Id**</br>_mserp_fk_leavetype_id_value</br>*GUID* | Read-only</br>Foreign key:mserp_essleavetypeentityid of mserp_essleavetypeentity entity  | Leave type ID |
| **Leave balance entity**</br>mserp_essleavebalanceentityid</br>*GUID* | System generated | A system-generated GUID value to uniquely identify the balance. |

## Example query

**Request**

```http
GET [Organizaton URI]/api/data/v9.1/mserp_essleavebalanceentities?$filter=mserp_personnelnumber eq '000013'
```

**Response**

```json
{
    "mserp_personnelnumber": "000013",
    "mserp_balanceavailable": 67.76,
    "mserp_leavetypeid": "PTO",
    "mserp_accrualratedescription": "6.16 hrs / Semimonthly",
    "mserp_lastcarryforwardamount": 0,
    "mserp_takenthisyear": 0,
    "mserp_totalthisyear": 67.76,
    "mserp_dataareaid": "usmf",
    "mserp_primaryfield": "000013 | PTO",
    "_mserp_fk_leavetype_id_value": "00000a6c-0000-0000-0000-005001000000",
    "mserp_essleavebalanceentityid": "0000091f-0000-0000-2703-005001000000",
    "_mserp_dataareaid_id_value": null
},
{
    "mserp_personnelnumber": "000013",
    "mserp_balanceavailable": 80,
    "mserp_leavetypeid": "Sick",
    "mserp_accrualratedescription": "80.00 hrs / Annually",
    "mserp_lastcarryforwardamount": 0,
    "mserp_takenthisyear": 0,
    "mserp_totalthisyear": 80,
    "mserp_dataareaid": "usmf",
    "mserp_primaryfield": "000013 | Sick",
    "_mserp_fk_leavetype_id_value": "00000a6c-0000-0000-ee02-005001000000",
    "mserp_essleavebalanceentityid": "0000091f-0000-0000-3003-005001000000",
    "_mserp_dataareaid_id_value": null
},
{
    "mserp_personnelnumber": "000013",
    "mserp_balanceavailable": 0,
    "mserp_leavetypeid": "Bereavement",
    "mserp_accrualratedescription": "0.00 hrs / Annually",
    "mserp_lastcarryforwardamount": 0,
    "mserp_takenthisyear": 0,
    "mserp_totalthisyear": 0,
    "mserp_dataareaid": "usmf",
    "mserp_primaryfield": "000013 | Bereavement",
    "_mserp_fk_leavetype_id_value": "00000a6c-0000-0000-f402-005001000000",
    "mserp_essleavebalanceentityid": "0000091f-0000-0000-4403-005001000000",
    "_mserp_dataareaid_id_value": null
},
{
    "mserp_personnelnumber": "000013",
    "mserp_balanceavailable": 66.65,
    "mserp_leavetypeid": "Vacation",
    "mserp_accrualratedescription": "13.33 hrs / Monthly",
    "mserp_lastcarryforwardamount": 0,
    "mserp_takenthisyear": 0,
    "mserp_totalthisyear": 66.65,
    "mserp_dataareaid": "usmf",
    "mserp_primaryfield": "000013 | Vacation",
    "_mserp_fk_leavetype_id_value": "00000a6c-0000-0000-f502-005001000000",
    "mserp_essleavebalanceentityid": "0000091f-0000-0000-1009-005001000000",
    "_mserp_dataareaid_id_value": null
}
```

## See also

[Payroll integration API introduction](hr-admin-integration-payroll-api-introduction.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
