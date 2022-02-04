---
# required metadata

title: Recruiting request
description: This topic describes the Recruiting request entity for Dynamics 365 Human Resources.
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

# Recruiting request


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes the Recruiting request entity for Dynamics 365 Human Resources.

Physical name: mshr_hcmrecruitingrequestentity

### Description

Describes a request to recruit for a job.

### JSON representation

```json
{
    "mshr_recruitingrequestid": "String",
    "mshr_hiringmanagerpersonnelnumber": "String",
    "mshr_recruiterpartynumber": "String",
    "mshr_status": Int,
    "mshr_description": "String",
    "mshr_recruitingrequestlocationid": "String",
    "mshr_comments": "String",
    "mshr_jobid": "String",
    "mshr_titleid": "String",
    "mshr_jobfunctionid": "String",
    "mshr_defaultfulltimeequivalency": Decimal,
    "mshr_regulatoryjobcategory": Int,
    "mshr_jobtypeid": "String",
    "mshr_exemptstatus": Int,
    "mshr_estimatedstartdate": "Date",
    "mshr_externaldescription": "String",
    "mshr_compensationlevelid": "String",
    "mshr_compensationlowthreshold": Decimal,
    "mshr_compensationcontrolpoint": Decimal,
    "mshr_compensationhighthreshold": Decimal,
    "mshr_dataareaid": "String",
    "_mshr_dataareaid_id_value": "Guid",
    "_mshr_fk_hiringmanager_id_value": "Guid",
    "_mshr_fk_recruiter_id_value": "Guid",
    "_mshr_fk_job_id_value": "Guid",
    "_mshr_fk_title_id_value": "Guid",
    "_mshr_fk_jobtype_id_value": "Guid",
    "_mshr_fk_compensationlevel_id_value": "Guid",
    "mshr_hcmrecruitingrequestentityid": "Guid",
    "_mshr_fk_recruitingrequestlocation_id_value": “Guid”
}
```

### Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Recruiting Request ID**<br>mshr_recruitingrequestid<br>*String* | Read-only<br>Required<br>System-generated | A user-readable unique identifier for the request displayed in the HR application. Number sequence. |
| **Recruiting Request Entity ID**<br>mshr_hcmrecruitingrequestentityid<br>*GUID* | Read-only<br>Required<br>System-generated | A system-generated GUID value to uniquely identify the recruiting request. |
| **Data Area ID**<br>mshr_dataareaid<br>*String* | Read/write<br>Optional<br> | Specifies the legal entity (company) for the recruiting request. |
| **Data Area ID Value**<br>_mshr_dataareaid_id_value<br>*GUID*<br> | Read-only<br>Optional<br>Foreign key: cdm_companyid of cdm_company entity | System-generated GUID value identifying the legal entity (company) for the recruiting request. |
| **Hiring Manager Personnel Number**<br>mshr_hiringmanagerpersonnelnumber<br>*String* | Read/write<br>Optional | The personnel number of the hiring manager associated with this recruiting request. |
| **Hiring Manager ID Value**<br>_mshr_fk_hiringmanager_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_hcmworkerbaseentityid of mshr_hcmworkerbaseentity entity | System-generated GUID value to identify the manager associated with the recruiting request. |
| **Recruiter Party Number**<br>mshr_recruiterpartynumber<br>*String* | Read/write<br>Optional | The person (party) number of the recruiter selected for the request. |
| **Recruiter ID Value**<br>_mshr_fk_recruiter_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_dirpersonentityid of mshr_dirpersonentity entity | System-generated GUID value to identify the recruiter associated with the recruiting request. |
| **Status**<br>mshr_status<br>*RecruitingRequestStatus* option set | Read/write<br>Required<br> | Indicates the status of the recruiting request. |
| **Description**<br>mshr_description<br>*String* | Read/write<br>Required | Describes the request. |
| **Recruiting Request Location ID**<br>mshr_recruitingrequestlocationid<br>*String* | Read/write<br>Optional | The user-readable unique identifier of the job location associated with this request. |
| **Recruiting Location ID Value**<br>_mshr_fk_recruitinglocation_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_hcmrecruitingrequestlocationentityid of mshr_hcmrecruitingrequestlocationentity entity | System-generated GUID value to identify the recruiting request location selected for the request. |
| **Comments**<br>mshr_comments<br>*String* | Read/write<br>Optional | Comments about the request for use by hiring managers and recruiters. |
| **Job ID**<br>mshr_jobid<br>*String* | Write-once<br>Required |	The user-readable unique identifier of the job shared by all Positions associated with this request. |
| **Job ID Value**<br>_mshr_fk_job_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmjobentityid of mshr_hcmjobentity entity | The system-generated unique identifier of the job shared by all Positions associated with the recruiting request. |
| **Title ID**<br>mshr_titleid<br>*String* | Read-only<br>Required | The user-readable unique identifier of the job title associated with this request. |
| **Title ID Value**<br>_mshr_fk_title_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmtitleid of mshr_hcmtitleentity entity | The system-generated unique identifier of the title of the job selected for the recruiting request. |
| **Job Function ID**<br>mshr_jobfunctionid<br>*String* | Read-only<br>Required<br>Foreign key: mshr_jobfunctionid of mshr_hcmjobfunctionentity entity | The user-readable unique identifier of the job function associated with this request. |
| **Default Full-Time Equivalency**<br>mshr_defaultfulltimeequivalency<br>*Double* | Read-only<br>Required | The full-time equivalent value for the job, where 1.0 represents a full-time worker. |
| **Regulatory Job Category**<br>mshr_regulatoryjobcategory<br>*RegulatoryJobCategory* option set | Read-only<br>Optional | The EEO job category of the job function selected for the job. Valid values included in the HcmRegulatoryJobCatetory (mshr_hcmregulatoryjobcategory) option set. |
| **Job Type ID**<br>mshr_jobtypeid<br>*String* | Read-only<br>Optional | The type of the job associated with the position. The job types are user-defined values, available in the mshr_hcmjobtypeentity entity. |
| **Job Type ID Value**<br>_mshr_fk_jobtype_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_hcmjobtypeentityid of mshr_hcmjobtypenentity entity | The system-generated unique identifier of the job type associated with the job for the recruiting request. |
| **Exempt Status**<br>mshr_exemptstatus<br>*JobExemptStatus* option set | Read-only<br>Optional | The FLSA exempt status based on the job type. |
| **Estimated Start Date**<br>mshr_estimatedstartdate<br>*Date* | Read/write<br>Required | The estimated date a candidate would start work. |
| **External Description**<br>mshr_externaldescription<br>*String* | Read/write<br>Optional | A candidate-facing description of the job/position. | 
| **Compensation Low Threshold**<br>mshr_compensationlowthreshold<br>*Double* | Read/write<br>Optional | Lower bound for the compensation level. |
| **Compensation Control Point**<br>mshr_compensationcontrolpoint<br>*Double* | Read/write<br>Optional | Control point for the compensation level. |
| **Compensation High Threshold**<br>mshr_compensationhighthreshold<br>*Double* | Read/write<br>Optional | Upper bound for the compensation level. |
| **Compensation Level**<br>mshr_compensationlevelid<br>*String* | Read/write<br>Optional | The compensation level of the job. A job can be set up with multiple compensation levels. This attribute indicates the selected job compensation level for this request. |
| **Job Compensation ID**<br>_mshr_fk_jobcompensation_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_hcmjobcompensationentityid of mshr_hcmjobcompensationentity entity | System-generated unique identifier for the compensation level associated with the Job of the recruiting request. |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Recruiting request](hr-admin-integration-ats-api-recruiting-request-example-query.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
