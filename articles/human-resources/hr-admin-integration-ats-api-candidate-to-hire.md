---
# required metadata

title: Candidate to hire
description: This topic describes the Candidate to hire entity for Dynamics 365 Human Resources.
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

# Candidate to hire


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes the Candidate to hire entity for Dynamics 365 Human Resources.

Physical name: mshr_hcmcandidatetohireentity

## Description

This entity provides candidate details used to create a worker in Dynamics 365 Human Resources. It's used to read all candidate records and create internal and external candidate records, allowing you to create personal details for the new candidate.

When you create an external candidate record who will be a new person record in the system, you must not define a party (person) number you post a new candidate record. The new person entity record is created with the new candidate record.

When you create an internal candidate record (a candidate for the position who already has an employee record with the company), define the party (person) number of the record that already exists for person for the mshr_partynumber property on the candidate record rather than defining personal information (such as name, gender, or birthdate) that would be used to create a new person record.

## JSON representation

```json
        {
            "mshr_candidateid": "String",
            "mshr_partynumber": "String",
            "mshr_partytype": "String",
            "mshr_recruitingrequestid": "String",
            "mshr_positionid": "String",
            "mshr_firstname": "String",
            "mshr_middlename": "String",
            "mshr_lastnameprefix": "String",
            "mshr_lastname": "String",
            "mshr_gender": Int,
            "mshr_birthdate": "Date",
            "mshr_citizenshipcountrycode": "String",
            "mshr_veteranstatusid": "String",
            "mshr_isdisabledveteran": Int,
            "mshr_availabilitydate": "Date",
            "mshr_iswillingtorelocate": Int,
            "mshr_comments": "String",
            "mshr_applicantintegrationresult": Int,
            "mshr_donothirereasoncodeid": "String",
            "mshr_dataareaid": "String",
            "_mshr_dataareaid_id_value": "Guid",
            "_mshr_fk_person_id_value": "Guid",
            "_mshr_fk_recruitingrequest_id_value": "Guid",
            "_mshr_fk_position_id_value": "Guid",
            "mshr_hcmcandidatetohireentityid": "Guid",
            "_mshr_fk_veteranstatus_id_value": "Guid",
            "_mshr_fk_reasoncode_id_value": "Guid",
            "mshr_militaryserviceenddate": "Guid",
            "mshr_militaryservicestartdate": "Guid"
        }
```

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Candidate to Hire Entity ID**<br>mshr_hcmcandidatetohireentityid<br>GUID | Read-only<br>Required<br>System-generated | A system-generated unique identifier for the entity record. |
| **Candidate ID**<br>mshr_candidateid<br>String | Read-only<br>Required<br>System-generated | A unique identifier for the entity. |
| **Party Number**<br>mshr_partynumber<br>String | Read-only<br>Required | The party (person) number of the candidate’s person record. |
| **Person ID Value**<br>_mshr_fk_person_id_value<br>GUID | Read-only<br>Required<br>Foreign key: mshr_dirpersonentityid of mshr_direpersonentity | The system-generated unique identifier for the party (person) record of the candidate. |
| **Party Type**<br>mshr_partytype<br>mshr_dirpartytype option set | Read-only<br>Required | The party type of the record, as defined in the mshr_dirpartytype option set. For this entity, the type will always be “Person”. |
| **Recruiting Request ID**<br>mshr_recruitingrequestid<br>String | Write once<br>Optional | References the Recruiting Request this candidate fulfills. |
| **Recruiting Request ID Value**<br>_mshr_fk_recruitingrequest_id_value<br>GUID | Read/write<br>Optional<br>Foreign key: mshr_hcmrecruitingrequestentityid of mshr_hcmrecruitingrequestentity | The system-generated unique identifier of the recruiting request the candidate fulfills. |
| **Position ID**<br>mshr_positionid<br>String | Read/write<br>Optional | The ID of the position for which the candidate is being considered. |
| **Position ID Value**<br>_mshr_fk_position_if_value<br>GUID | Read-only<br>Optional<br>Foreign key: mshr_hcmpositionv2entityid of mshr_hcmpositionv2entity | System-generated identifier of the position for with the candidate is being considered. |
| **First Name**<br>mshr_firstname<br>String | Read/write<br>Required | Candidate first name. |
| **Middle Name**<br>mshr_middlename<br>String | Read/write<br>Optional | Candidate middle name. |
| **Last Name Prefix**<br>mshr_lastnameprefix<br>String | Read/write<br>Optional | Candidate last name prefix. |
| **Last Name**<br>mshr_lastname<br>String | Read/write<br>Optional | Candidate last name. |
| **Gender**<br>mshr_gender<br>mshr_hcmpersongender option set | Read/write<br>Optional | The candidate’s gender. |
| **Birth Date**<br>mshr_birthdate<br>Datetime | Read/write<br>Optional | The candidate’s birth date. |
| **Citizenship Country Code**<br>mshr_citizenshipcountrycode<br>String | Read/write<br>Optional | Specifies the country where the candidate has citizenship. Valid country codes are in mshr_logisticaddresscountryregionentity. |
| **Veteran Status ID**<br>mshr_veteranstatusid<br>String | Read/write<br>Optional | Indicates the veteran status of the candidate. |
| **Veteran Status ID Value**<br>_mshr_fk_veteranstatus_id_value<br>GUID | Read-only<br>Optional<br>Foreign key: mshr_hcmveteranstatusentityid of mshr_hcmveteranstatusentity | System-generated unique identifier for the veteran status entity record. |
| **Military Service Start Date**<br>mshr_militaryservicestartdate<br>Datetime | Read/write<br>Optional | The start date of the candidate’s military service. |
| **Military Service End Date**<br>mshr_militaryserviceenddate<br>Datetime | Read/write<br>Optional | The end date of the candidate’s military service. |
| **Is Disabled Veteran**<br>mshr_isdisabledveteran<br>mshr_noyes option set | Read/write<br>Optional | Indicates if the candidate has disabled veteran status. |
| **Availability Date**<br>mshr_availabilitydate<br>Datetime | Read/write<br>Optional | The earliest date the candidate would be available to work. |
| **Is Willing To Relocate**<br>mshr_iswillingtorelocate<br>mshr_noyes option set | Read/write<br>Optional | Indicates whether the candidate is willing to relocate for the position. |
| **Comments**<br>mshr_comments<br>String | Read/write<br>Optional | Comments to be used by the recruiter or hiring manager. |
| **Application Integration Result**<br>mshr_applcantintegrationresult<br>mshr_applicantintegrationresult option set | Read/write<br>Required | The status of the candidate in the hiring process related to the integration. |
| **Do Not Hire Reason Code ID**<br>mshr_donothirereasoncodeid<br>String | Read/write<br>Optional | A reason code optionally provided when the status (application integration result) is set to “Not hired”. |
| **Reason Code ID Value**<br>_mshr_fk_reasoncode_id_value<br>GUID | Read-only<br>Optional<br>Foreign key: mshr_hcmreasoncodeentityid of mshr_hcmreasoncodeentity entity | System-generated unique identifier for the **Do Not Hire** reason code. |
| **Data Area ID**<br>mshr_dataareaid<br>String | Read/write<br>Optional | 	Specifies the legal entity (company). |
| **Data Area ID Value**<br>_mshr_dataareaid_id_value<br>GUID | Read-only<br>Optional<br>Foreign key: cdm_companyid of cdm_company entity | System-generated GUID value identifying the legal entity (company). |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Candidate to hire](hr-admin-integration-ats-api-candidate-to-hire-example-query.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
