---
# required metadata

title: Leave request
description: This article provides details and an example query for the leave request entity in Dynamics 365 Human Resources.
author: marcelbf
ms.date: 07/09/2024
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
ms.author: ajitchandran
ms.search.validFrom: 2021-06-25
ms.dyn365.ops.version: Human Resources
---

# Leave request



[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the leave request entity for Dynamics 365 Human Resources.

### Description

This entity provides information for a leave request.

Physical name: mserp_essleaverequestentity.

## Properties

| Property</br>**Physical name**</br>***Type*** | Use | Description |
| --- | --- | --- |
| **Request id**</br>mserp_requestid</br>*String* | Read-only | The request ID. |
| **Leave type id**</br>mserp_leavetypeid</br>*String* | Read-only | The leave type ID. |
| **Date**</br>mserp_leavedate</br>*Date Time Offset* | Read-only | The date of the leave request. |
| **Amount**</br>mserp_amount</br>*Decimal* | Read-only | The leave request amount. |
| **Half day type**</br>mserp_halfdaydefinition</br>*mserp_LeaveHalfDayDefinition option set* | Read-only | The type of half day leave. |
| **Comment**</br>mserp_comment</br>*String* | Read-only | Comment for the request. |
| **Status**</br>mserp_status</br>*mserp_status option set* | Read-only | The status of the request. |
| **Date**</br>mserp_requestdate</br>*Date Time Offset* | Read-only | The date of the request. |
| **Personnel number**</br>mserp_personnelnumber</br>*String* | Read-only | The employee's unique personnel number. |
| **Reason code id**</br>mserp_reasoncodeid</br>*String* | Read-only | The reason code ID. |
| **Data area ID**</br>mserp_dataareaid</br>*String* | Read-only | Specifies the legal entity (company). |
| **Primary field**</br>mserp_primaryfield</br>*GUID* | Read-only</br>System generated | |
| **Leave type entity**</br>mserp_essleaverequestentityid</br>*GUID* | System generated | A system-generated GUID value to uniquely identify the leave request. |

## Example query

**Request**

```http
GET [Organizaton URI]/api/data/v9.1/mserp_essleaverequestentities?$filter=mserp_personnelnumber eq '000020'
```

**Response**

```json
{
    "mserp_requestid": "USMF-000001",
    "mserp_leavetype": "PTO",
    "mserp_leavedate": "2017-01-02T00:00:00Z",
    "mserp_amount": 8,
    "mserp_halfdaydefinition": 200000000,
    "mserp_comment": "Taking a week off to relax",
    "mserp_status": 200000009,
    "mserp_requestdate": "2017-07-31T00:00:00Z",
    "mserp_personnelnumber": "000020",
    "mserp_reasoncodeid": "",
    "mserp_dataareaid": "usmf",
    "mserp_primaryfield": "USMF-000001 | PTO | 1/2/2017",
    "mserp_essleaverequestentityid": "000004dd-0000-0000-0f00-005001000000",
    "_mserp_dataareaid_id_value": null
}
```

## See also

[Payroll integration API introduction](hr-admin-integration-payroll-api-introduction.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
