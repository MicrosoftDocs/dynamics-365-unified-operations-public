---
# required metadata

title: Person professional experience
description: This topic describes the Person professional experience entity for Dynamics 365 Human Resources.
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

# Person professional experience


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes the Person professional experience entity for Dynamics 365 Human Resources.

Physical name: mshr_hcmpersonprofessionalexperienceentity

## Description

This entity describes professional experience or work history of a candidate.

## JSON representation

```json
{
    "mshr_partynumber": "String",
    "mshr_employerposition": "String",
    "mshr_startdate": "Date",
    "mshr_allowcontactemployer": Int,
    "mshr_employerlocation": "String",
    "mshr_employername": "String",
    "mshr_enddate": "Date",
    "mshr_note": "String",
    "mshr_phone": "String",
    "mshr_url": "String",
    "mshr_primaryfield": "String",
    "_mshr_fk_person_id_value": "Guid",
    "mshr_hcmpersonprofessionalexperienceentityid": "Guid"
}
```

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Person Professional Experience Entity ID**<br>mshr_hcmpersonprofessionalexperienceentityid<br>*GUID* | Read-only<br>Required | System-generated unique identifier for the entity record. |
| **Party Number**<br>mshr_partynumber<br>*String* | Read/write<br>Required | Unique identifier of the person record for the candidate. |
| **Person ID Value**<br>_mshr_fk_person_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_dirpersonentityid of mshr_dirpersonentity | System-generated unique identifier of the person entity record. |
| **Employer Position**<br>mshr_employerposition<br>*String* | Read/write<br>Required | The position title held by the candidate while under employment. |
| **Employer Name**<br>mshr_employername<br>*String* | Read/write<br>Required | The name of the employer. |
| **Employer Location**<br>mshr_employerlocation<br>*String* | Read/write<br>Optional | The employer’s location. Max length: 60. No specific format defined or required. |
| **Phone**<br>mshr_phone<br>*String* | Read/write<br>Optional | The employer’s phone number. |
| **URL**<br>mshr_url<br>*String* | Read/write<br>Optional | The URL of the employer’s website. |
| **Start Date**<br>mshr_startdate<br>*Datetime* | Read/write<br>Required | The start date of the candidate’s employment. |
| **End Date**<br>mshr_enddate<br>*Datetime* | Read/write<br>Optional | The end date of the candidate’s employment, or null if the candidate is still employed here. |
| **Allow Contact Employer**<br>mshr_allowcontactemployer<br>*mshr_hrmblankyesno option set* | Read/write<br>Optional | Signifies whether the candidate allows contacting the previous employer. |
| **Notes**<br>mshr_note<br>*String* | Read/write<br>Optional | Notes for use by the recruiter or hiring manager. |
| **Primary Field**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | Field used as a primary identifier of the entity record. Combination of party number, start date, employer position, and employer name. |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Candidate to hire](hr-admin-integration-ats-api-candidate-to-hire-example-query.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
