---
# required metadata

title: Leave request
description: This article provides details and an example query for the leave request entity in Dynamics 365 Human Resources.
author: marcelbf
ms.date: 07/09/2024
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
ms.author: ajitchandran
ms.search.validFrom: 2021-06-25
ms.dyn365.ops.version: Human Resources
---

# Leave request



[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the leave request entity for Dynamics 365 Human Resources.

### Description

This entity provides information for a leave request.

Physical name: mshr_essleaverequestentity.

## Properties

| Property</br>**Physical name**</br>***Type*** | Use | Description |
| --- | --- | --- |
| **Request id**</br>mshr_requestid</br>*String* | Read-only | The request ID. |
| **Leave type id**</br>mshr_leavetypeid</br>*String* | Read-only | The leave type ID. |
| **Date**</br>mshr_leavedate</br>*Date Time Offset* | Read-only | The date of the leave request. |
| **Amount**</br>mshr_amount</br>*Decimal* | Read-only | The leave request amount. |
| **Half day type**</br>mshr_halfdaydefinition</br>*mshr_LeaveHalfDayDefinition option set* | Read-only | The type of half day leave. |
| **Comment**</br>mshr_comment</br>*String* | Read-only | Comment for the request. |
| **Status**</br>mshr_status</br>*mshr_status option set* | Read-only | The status of the request. |
| **Date**</br>mshr_requestdate</br>*Date Time Offset* | Read-only | The date of the request. |
| **Personnel number**</br>mshr_personnelnumber</br>*String* | Read-only | The employee's unique personnel number. |
| **Reason code id**</br>mshr_reasoncodeid</br>*String* | Read-only | The reason code ID. |
| **Data area ID**</br>mshr_dataareaid</br>*String* | Read-only | Specifies the legal entity (company). |
| **Primary field**</br>mshr_primaryfield</br>*GUID* | Read-only</br>System generated | |
| **Leave type entity**</br>mshr_essleaverequestentityid</br>*GUID* | System generated | A system-generated GUID value to uniquely identify the leave request. |

## Example query

**Request**

```http
GET [Organizaton URI]/api/data/v9.1/mshr_essleaverequestentities?$filter=mshr_personnelnumber eq '000020'
```

**Response**

```json
{
    "mshr_requestid": "USMF-000001",
    "mshr_leavetype": "PTO",
    "mshr_leavedate": "2017-01-02T00:00:00Z",
    "mshr_amount": 8,
    "mshr_halfdaydefinition": 200000000,
    "mshr_comment": "Taking a week off to relax",
    "mshr_status": 200000009,
    "mshr_requestdate": "2017-07-31T00:00:00Z",
    "mshr_personnelnumber": "000020",
    "mshr_reasoncodeid": "",
    "mshr_dataareaid": "usmf",
    "mshr_primaryfield": "USMF-000001 | PTO | 1/2/2017",
    "mshr_essleaverequestentityid": "000004dd-0000-0000-0f00-005001000000",
    "_mshr_dataareaid_id_value": null
}
```

## See also

[Payroll integration API introduction](hr-admin-integration-payroll-api-introduction.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
