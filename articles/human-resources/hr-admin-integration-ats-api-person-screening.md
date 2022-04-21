---
# required metadata

title: Person screening
description: This topic describes the Person screening entity for Dynamics 365 Human Resources.
author: jaredha
ms.date: 02/05/2021
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
ms.author: jaredha
ms.search.validFrom: 2021-02-05
ms.dyn365.ops.version: Human Resources
---

# Person screening


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes the Person screening entity for Dynamics 365 Human Resources.

Physical name: mshr_hcmpersonscreeningentity

## Description

This entity describes screenings a candidate has passed or must pass for employment.

## JSON representation

```json
{
    "mshr_note": "String",
    "mshr_requiredby": "Date",
    "mshr_status": Int,
    "mshr_partynumber": "String",
    "mshr_screeningtypeid": "String",
    "mshr_primaryfield": "String",
    "_mshr_fk_person_id_value": "Guid",
    "mshr_hcmpersonscreeningentityid": "Guid",
    "mshr_completeddate": "Date"
}
```

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Person Screening Entity ID**<br>mshr_hcmpersonscreeningentityid<br>*GUID* | Read-only<br>Required<br>System-generated | Unique primary identifier for the person screening record. |
| **Party Number**<br>mshr_partynumber<br>*String* | Read/write<br>Required | The party (person) number associated with the candidate. |
| **Person ID Value**<br>_mshr_fk_person_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_dirpersonentityid of mshr_dirpersonentity | The system-generated identifier of the party (person) entity record. |
| **Screening Type ID**<br>mshr_screeningtypeid<br>*String* | Read/write<br>Required<br>Foreign key: ScreeningType | The identifier of the screening type defined in Human Resources. |
| **Screening Type ID Value**<br>_mshr_fk_screeningtype_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmscreeningtypeentityid of mshr_hcmscreeningtypeentity | System-generated identifier for the screening type record in the associated entity. |
| **Required By**<br>mshr_requiredby<br>*Datetime* | Read/write<br>Optional | The date by which the screening is required to be completed. |
| **Status**<br>mshr_status<br>*mshr_hcmcompletionstatus option set*<br>Read/write<br>Required | Provides the candidate’s status for the screening. |
| **Completed Date**<br>mshr_completeddate<br>*Datetime* | Read/write<br>Optional | The date the screening was completed. |
| **Notes**<br>mshr_note<br>*String* | Read/write<br>Optional | Notes for use by hiring managers and recruiters. |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Candidate to hire](hr-admin-integration-ats-api-candidate-to-hire-example-query.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
