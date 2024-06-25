---
# required metadata

title: Leave type
description: This article provides details and an example query for the leave type entity in Dynamics 365 Human Resources.
author: ajitchandran
ms.date: 06/25/2024
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

# Leave type



[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the leave type entity for Dynamics 365 Human Resources.

### Description

This entity provides information for a given leave type.

Physical name: mshr_essleavetypeentity.

## Properties

| Property</br>**Physical name**</br>***Type*** | Use | Description |
| --- | --- | --- |
| **Leave type id**</br>mshr_leavetypeid</br>*String* | Read-only | The leave type ID. |
| **Description**</br>mshr_description</br>*String* | Read-only | A description of the leave type. |
| **Category**</br>mshr_category</br>*mshr_LeaveTypeCategory option set* | Read-only | The leave type category. |
| **Reason code required**</br>mshr_isreasoncoderequired</br>*mshr_NoYes option set* | Read-only | Defines if a reason code is required for the leave type. |
| **Leave unity**</br>mshr_leaveamountunit</br>*mshr_LeaveAmountUnit option set* | Read-only | The unity of this leave type. |
| **Enable half day**</br>mshr_enablehalfdaydefinition</br>*mshr_NoYes option set* | Defines if half day is enabled for the leave type. |
| **Data area ID**</br>mshr_dataareaid_id</br>*String* | Read-only | Specifies the legal entity (company). |
| **Leave type entity**</br>mshr_essleavetypeentityid</br>*GUID* | System generated | A system-generated GUID value to uniquely identify the leave type. |

## Example query

**Request**

```http
GET [Organizaton URI]/api/data/v9.1/mshr_essleavetypeentities?$filter=mshr_leavetypeid eq 'PTO'
```

**Response**

```json
{
    "mshr_leavetypeid": "PTO",
    "mshr_description": "Paid time off",
    "mshr_category": 200000000,
    "mshr_isreasoncoderequired": 200000000,
    "mshr_leaveamountunit": 200000000,
    "mshr_enablehalfdaydefinition": 200000000,
    "mshr_dataareaid": "usmf",
    "mshr_essleavetypeentityid": "00000a6c-0000-0000-0000-005001000000",
    "_mshr_dataareaid_id_value": null
}
```

## See also

[Payroll integration API introduction](hr-admin-integration-payroll-api-introduction.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
