---
# required metadata

title: Person skill
description: This topic describes the Person skill entity for Dynamics 365 Human Resources.
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

# Person skill


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes the Person skill entity for Dynamics 365 Human Resources.

Physical name: mshr_hcmpersonskillentity

## Description

This entity describes the skills of a candidate.

## JSON representation

```json
{
    "mshr_certifier": "String",
    "mshr_partynumber": "String",
    "mshr_levelid": "String",
    "mshr_ratinglevelexaminer": "String",
    "mshr_skillid": "String",
    "mshr_ratingid": "String",
    "mshr_leveltype": Int,
    "mshr_yearsofexperience": Decimal,
    "mshr_verified": Int,
    "mshr_leveldate": "Date",
    "mshr_primaryfield": "String",
    "_mshr_fk_certifier_id_value": "Guid",
    "_mshr_fk_person_id_value": "Guid",
    "_mshr_fk_ratinglevel_id_value": "Guid",
    "_mshr_fk_ratinglevelexaminer_id_value": "Guid",
    "_mshr_fk_skill_id_value": "Guid",
    "mshr_hcmpersonskillentityid": "Guid"
}
```

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Person Skill Entity ID**<br>mshr_hcmpersonskillentityid<br>*GUID* | Read-only<br>Required | System-generated unique identifier for the entity record. |
| **Party Number**<br>mshr_partynumber<br>*String* | Read/write<br>Required | 	The ID of the associated party (person) record. |
| **Person ID Value**<br>_mshr_fk_person_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_dirpersonentityid of mshr_dirpersonentity | The system-generated identifier of the party (person) entity record. |
| **Certifier**<br>mshr_certifier<br>*String* | Read/write<br>Optional | The personnel number of the worker who certified this skill. |
| **Certifier ID Value**<br>_mshr_fk_certifier_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_hcmworkerentityid of mshr_hcmworkerentity | System-generated unique identifier of the worker record for the worker who certified the skill. |
| **Skill ID**<br>mshr_skillid<br>*String* | Read/write<br>Required | The identifier of the skill defined in Human Resources. |
| **Skill ID Value**<br>_mshr_fk_skill_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmskillentityid of mshr_hcmskillentity | The system-generated identifier of the selected skill. |
| **Years of Experience**<br>mshr_yearsofexperience<br>*Decimal* | Read/write<br>Optional | The years of experience the candidate has in this skill. |
| **Rating ID**<br>mshr_ratingid<br>*String* | Read/write<br>Required | The rating scale type. For this entity, the value is **Skills**. |
| **Level Type**<br>mshr_leveltype<br>*mshr_hrmskillleveltype option set* | Read/write<br>Required | A type categorization for the level assigned to the skill. |
| **Level ID**<br>mshr_levelid<br>*String* | Read/write<br>Required | The ID of the Rating Level the candidate has for this skill. |
| **Rating Level ID Value**<br>_mshr_fk_ratinglevel_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmratinglevelentityid of mshr_hcmratinglevelentity | The system-generated identifier of the rating level. |
| **Level Date**<br>mshr_leveldate<br>*Datetime* | Read/write<br>Required | The date at which the candidate was rated in the skill. |
| **Rating Level Examiner**<br>mshr_ratinglevelexaminer<br>*String* | Read/write<br>Optional | The personnel number of the worker who rated the candidate. |
| **Rating Level Examiner ID Value**<br>_mshr_fk_ratinglevelexaminer_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_hcmworkerentityid of mshr_hcmworkerentity | The system-generated identifier of the worker who examined the candidate’s skill level. |
| **Verified**<br>mshr_verified<br>*mshr_noyes option set* | Read/write<br>Required | Indicates whether the assessed skill level has been verified. |
| **Primary Field**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | Field to be used as an identifier of the entity record. Combination of party number, level type, skill ID, and level date. |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Candidate to hire](hr-admin-integration-ats-api-candidate-to-hire-example-query.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
