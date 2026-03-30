---
# required metadata

title: Leave type
description: This article provides details and an example query for the leave type entity in Dynamics 365 Human Resources.
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
ms.author: ajitchandran
ms.search.validFrom: 2021-06-25
ms.dyn365.ops.version: Human Resources
---

# Leave type

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the leave type entity for Dynamics 365 Human Resources.

### Description

This entity provides information for a given leave type.

Physical name: mserp_essleavetypeentity.

## Properties

| Property</br>**Physical name**</br>***Type*** | Use | Description |
| --- | --- | --- |
| **Leave type id**</br>mserp_leavetypeid</br>*String* | Read-only | The leave type ID. |
| **Description**</br>mserp_description</br>*String* | Read-only | A description of the leave type. |
| **Category**</br>mserp_category</br>*mserp_LeaveTypeCategory option set* | Read-only | The leave type category. |
| **Reason code required**</br>mserp_isreasoncoderequired</br>*mserp_NoYes option set* | Read-only | Defines if a reason code is required for the leave type. |
| **Leave unity**</br>mserp_leaveamountunit</br>*mserp_LeaveAmountUnit option set* | Read-only | The unity of this leave type. |
| **Enable half day**</br>mserp_enablehalfdaydefinition</br>*mserp_NoYes option set* | Defines if half day is enabled for the leave type. |
| **Data area ID**</br>mserp_dataareaid_id</br>*String* | Read-only | Specifies the legal entity (company). |
| **Leave type entity**</br>mserp_essleavetypeentityid</br>*GUID* | System generated | A system-generated GUID value to uniquely identify the leave type. |

## Example query

**Request**

```http
GET [Organizaton URI]/api/data/v9.1/mserp_essleavetypeentities?$filter=mserp_leavetypeid eq 'PTO'
```

**Response**

```json
{
    "mserp_leavetypeid": "PTO",
    "mserp_description": "Paid time off",
    "mserp_category": 200000000,
    "mserp_isreasoncoderequired": 200000000,
    "mserp_leaveamountunit": 200000000,
    "mserp_enablehalfdaydefinition": 200000000,
    "mserp_dataareaid": "usmf",
    "mserp_essleavetypeentityid": "00000a6c-0000-0000-0000-005001000000",
    "_mserp_dataareaid_id_value": null
}
```

## See also

[Payroll integration API introduction](hr-admin-integration-payroll-api-introduction.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
