---
# required metadata

title: Recruiting request education
description: This topic describes the Recruiting request education entity for Dynamics 365 Human Resources.
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

# Recruiting request education


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes the Recruiting request education entity for Dynamics 365 Human Resources.

Physical name: mshr_hcmrecruitingrequesteducationentity

### Description

Describes educational requirements for a RecruitingRequest.

### JSON representation

```json
{
    "mshr_recruitingrequestid": "String",
    "mshr_educationdisciplineid": "String",
    "mshr_educationdisciplinedescription": "String",
    "mshr_educationlevelid": "String",
    "mshr_educationleveldescription": "String",
    "mshr_dataareaid": "String",
    "_mshr_dataareaid_id_value": "Guid",
    "mshr_primaryfield": "String",
    "_mshr_fk_recruitingrequest_id_value": "Guid",
    "_mshr_fk_educationdiscipline_id_value": "Guid",
    "_mshr_fk_educationlevel_id_value": "Guid",
    "mshr_hcmrecruitingrequesteducationentityid": "Guid"
}
```

### Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Recruiting Request Education Entity ID**<br>mshr_hcmrecruitingrequesteducationentityid<br>*GUID* | Read-only<br>Required | System-generated unique identifier for the Recruiting Request Education record. |
| **Recruiting Request ID**<br>mshr_recruitingrequestid<br>*String* | Write-once<br>Required | The user-readable unique identifier of the related recruiting request. |
| **Recruiting Request ID Value**<br>_mshr_fk_recruitingrequest_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmrecruitingrequestentityid of mshr_hcmrecruitingrequestentity | System-generated unique identifier of the related recruiting request. |
| **Education Level ID**<br>mshr_educationlevelid<br>*String* | Write-once<br>Required | The level of education required. |
| **Educational Level ID Value**<br>_mshr_fk_educationlevel_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmeducationlevelentityid of mshr_hcmeducationlevelentity | System-generated unique identifier of the level of education required. |
| **Education Level Description**<br>mshr_educationleveldescription<br>*String* | Read-only<br>Required | The description of the level required for the skill. |
| **Education Discipline ID**<br>mshr_educationdisciplinedescription<br>*String* | Write-once<br>Required | The area of educational discipline. |
| **Education Discipline ID Value**<br>_mshr_fk_educationdiscipline_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmeducationdisciplineentityid of mshr_hcmeducationdisciplineentity | System-generated unique identifier of the area of educational discipline. |
| **Education Discipline Description**<br>mshr_educationdisciplinedescription<br>String	| Read-only<br>Required	| The description of the area of educational discipline. |
| **Data Area ID**<br>mshr_dataareaid<br>*String* | Read/write<br>Optional | Specifies the legal entity (company).|
| **Data Area ID Value**<br>_mshr_dataareaid_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: cdm_companyid of cdm_company entity | System-generated GUID value identifying the legal entity (company). |
| **Primary Field**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | Concatenation of Recruiting Request value, Education Level ID, and Education Discipline ID as another method to uniquely identify the record. |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Recruiting request](hr-admin-integration-ats-api-recruiting-request-example-query.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
