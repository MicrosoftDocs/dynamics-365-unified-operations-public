---
# required metadata

title: Person education
description: This topic describes the Person education entity for Dynamics 365 Human Resources.
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

# Person education


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes the Person education entity for Dynamics 365 Human Resources.

Physical name: mshr_hcmpersoneducationentity

## Description

This entity contains the educational history of the person who is the candidate. The education is linked to the person record enabling the education to be associated with any other roles created for the person in addition to the candidate record (worker, contractor, and so on).

## JSON representation

```json
{
    "mshr_creditbasis": Int,
    "mshr_creditscompleted": Decimal,
    "mshr_creditsearned": Decimal,
    "mshr_creditsneeded": Decimal,
    "mshr_description": "String",
    "mshr_duration": Decimal,
    "mshr_durationunit": Int,
    "mshr_educationdisciplineid": "String",
    "mshr_educationinstitutionid": "String",
    "mshr_educationlevelid": "String",
    "mshr_enddate": "Date",
    "mshr_gradepointaverage": Decimal,
    "mshr_gradescale": "String",
    "mshr_notes": "String",
    "mshr_secondaryemphasis": "String",
    "mshr_startdate": "Date",
    "mshr_partynumber": "String",
    "mshr_primaryfield": "String",
    "_mshr_fk_educationdiscipline_id_value": "Guid",
    "_mshr_fk_person_id_value": "Guid",
    "_mshr_fk_educationinstitution_id_value": "Guid",
    "_mshr_fk_educationlevel_id_value": "Guid",
    "mshr_hcmpersoneducationentityid": "Guid"
}
```

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Person Education Entity ID**<br>mshr_hcmpersoneducationentityid<br>*GUID* | Read-only<br>Required | System-generated unique identifier of the person education entity record. |
| **Party Number**<br>mshr_partynumber<br>*String* | Read/write<br>Required | The unique identifier of the party (person) record for the candidate. |
| **Person ID Value**<br>_mshr_fk_person_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_dirpersonentityid of mshr_dirpersonentity | The system-generated unique identifier of the candidate’s person record. |
| **Credit Basis**<br>mshr_creditbasis<br>*mshr_hcmeducationcreditbasis option set* | Read/write<br>Optional | The credit basis of the educational degree. |
| **Credits Completed**<br>mshr_creditscompleted<br>*Decimal* | Read/write<br>Optional | The number of credits completed for the education. |
| **Credits Earned**<br>mshr_creditsearned<br>*Decimal* | Read/write<br>Optional | The number of credits earned for the education record for a degree in progress. |
| **Credits Needed**<br>mshr_creditsneeded<br>*Decimal* | Read/write<br>Optional | The number of credits required for a degree in progress. |
| **Description**<br>mshr_description<br>*String* | Read/write<br>Optional | A description of the candidate’s degree. |
| **Education Level ID**<br>mshr_educationlevelid<br>*String* | Read/write<br>Optional | The ID of the education level. | 
| **Education Level ID Value**<br>_mshr_fk_educationlevel_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_hcmeducationdegreeentityid of mshr_hcmeducationdegreeentity entity | System-generated identifier for the education degree record. This identifier provides the degrees and education levels defined for the organization. |
| **Education Discipline ID**<br>mshr_educationdisciplineid<br>*String* | Read/write<br>Required<br>Foreign key: EducationDiscipline | The ID of the education discipline. |
| **Education Discipline ID Value**<br>_mshr_fk_educationdiscipline_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmeducationdisciplineentityid of mshr_hcmeducationdisciplineentity | The system-generated unique identifier of the education discipline of the education record. |
| **Secondary Emphasis**<br>mshr_secondaryemphasis<br>*String* | Read/write<br>Optional | The secondary emphasis of the earned degree. |
| **Education Institution ID**<br>mshr_educationinstitutionid<br>*String* | Read/write<br>Optional | The ID of the attended educational institution. |
| **Education Institution ID Value**<br>_mshr_fk_educationinstitution_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_hcmeducationinstitutionentityid of mshr_hcmeducationinstitutionentity | System-generated identifier of the educational institution. |
| **Start Date**<br>mshr_startdate<br>*Datetime* | Read/write<br>Optional | The start date of the education for the earned degree. |
| **End Date**<br>mshr_enddate<br>*Datetime* | Read/write<br>Required | The date the credential was issued. |
| **Duration**<br>mshr_duration<br>*Decimal* | Read/write<br>Optional | The duration of time of the education record. |
| **Duration Unit**<br>mshr_durationunit<br>*mshr_periodunit option set* | Read/write<br>Optional | The unit of time associated with the duration of the education record. |
| **Grade Point Average**<br>mshr_gradepointaverage<br>*Decimal* | Read/write<br>Optional | The earned grade point average for the degree. |
| **Grade Scale**<br>mshr_gradescale<br>*String* | Read/write<br>Optional | The scale used for the grade point average. |
| **Notes**<br>mshr_notes<br>*String* | Read/write<br>Optional | Notes for use by the recruiter or hiring manager. |
| **Primary Field**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | Field used as another primary identifier of the entity record. Combination of party number, education discipline ID, education institution ID, and education level ID. |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Candidate to hire](hr-admin-integration-ats-api-candidate-to-hire-example-query.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
