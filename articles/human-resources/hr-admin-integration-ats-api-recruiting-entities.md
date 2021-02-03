---
# required metadata

title: Recruiting request and related entities
description: This topic describes Recruiting request and related entities for the Dynamics 365 Human Resources Applicant Tracking System (ATS) integration API.
author: andreabichsel
manager: tfehr
ms.date: 02/03/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-human-resources
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jaredha
ms.search.validFrom: 2021-02-03
ms.dyn365.ops.version: Platform update 36
---

# Recruiting request and related entities

This topic describes Recruiting request and related entities for the Dynamics 365 Human Resources Applicant Tracking System (ATS) integration API.

## Entity: Recruiting Request

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
| **Tempt Status**<br>mshr_exemptstatus<br>*JobExemptStatus* option set | Read-only<br>Optional | The FLSA exempt status based on the job type. |
| **Estimated Start Date**<br>mshr_estimatedstartdate<br>*Date* | Read/write<br>Required | The estimated date a candidate would start work. |
| **External Description**<br>mshr_externaldescription<br>*String* | Read/write<br>Optional | A candidate-facing description of the job/position. | Compensation Low Threshold<br>mshr_compensationlowthreshold<br>*Double* | Read/write<br>Optional | Lower bound for the compensation level. |
| **Compensation Control Point**<br>mshr_compensationcontrolpoint<br>*Double* | Read/write<br>Optional | Control point for the compensation level. |
| **Compensation High Threshold**<br>mshr_compensationhighthreshold<br>*Double* | Read/write<br>Optional | Upper bound for the compensation level. |
| **Compensation Level**<br>mshr_compensationlevelid<br>*String* | Read/write<br>Optional | The compensation level of the job. A job can be set up with multiple compensation levels. This attribute indicates the selected job compensation level for this request. |
| **Job Compensation ID**<br>_mshr_fk_jobcompensation_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_hcmjobcompensationentityid of mshr_hcmjobcompensationentity entity | System-generated unique identifier for the compensation level associated with the Job of the recruiting request. |

## Entity: Recruiting Request Position

Physical name: mshr_hcmrecruitingrequestpositionentity

### Description

Describes the position or positions to fill for a Recruiting Request. Adding a position to the recruiting request is optional. The properties of the position are read-only as the position properties shouldn't be different on the recruiting request than they are on the position master record. If the properties need to change, it should be done on the position master record before adding the position to the recruiting request.

### JSON representation
```json
{
    "mshr_recruitingrequestid": "String",
    "mshr_positionid": "String",
    "mshr_description": "String",
    "mshr_positiontypeid": "String",
    "mshr_status": Int,
    "mshr_departmentnumber": "String",
    "mshr_reportstopositionid": "String",
    "mshr_reportstopersonnelnumber": "String",
    "mshr_financialdimension": "String",
    "mshr_dataareaid": "String",
    "_mshr_dataareaid_id_value": "Guid",
    "mshr_primaryfield": "String",
    "_mshr_fk_recruitingrequest_id_value": "Guid",
    "_mshr_fk_position_id_value": "Guid",
    "_mshr_fk_positiontype_id_value": "Guid",
    "_mshr_fk_department_id_value": "Guid",
    "_mshr_fk_reportstoposition_id_value": "Guid",
    "_mshr_fk_reportstoworker_id_value": "Guid",
    "mshr_hcmrecruitingrequestpositionentityid": "Guid"
}
```

### Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Recruiting Request Position Entity ID**<br>mshr_hcmrecruitingrequestpositionentityid<br>*GUID* | Read-only<br>Required |	System-generated identifier of the recruiting request position record. |
| **Recruiting Request ID**<br>mshr_recruitingrequestid<br>*String* | Write-once<br>Required | The user-readable unique identifier of the recruiting request. |
| **Recruiting Request ID Value**<br>_mshr_fk_recruitingrequest_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmrecruitingrequestentityid of mshr_hcmrecruitingrequestentity entity | System-generated identifier of the recruiting request to which the position is assigned. |
| **Position ID**<br>mshr_positionid<br>*String* | Write-once<br>Required | The user-readable unique identifier of the position. |
| **Position ID Value**<br>_mshr_fk_position_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmpositionv2entityid of mshr_hcmpositionv2entity entity | System-generated identifier of the position. |
| **Description**<br>mshr_description<br>*String* | Read-only<br>Required | The position description. |
| **Position Type ID**<br>mshr_positiontypeid<br>*String* | Read-only<br>Optional | The user-readable unique identifier of the position type for this position. |
| **Position Type ID Value**<br>_mshr_fk_positiontype_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_hcmpositiontypeentityid of mshr_hcmpositiontypeentity entity | A system-generated unique identifier of the position type for this position. |
| **Status**<br>mshr_status<br>*RecruitingRequestPositionStatus* option set | Read/write<br>Required | Status of the position for the recruiting request. |
| **Department Number**<br>mshr_departmentnumber<br>*String* | Read-only<br>Optional<br> | The department number of the position. |
| **Department ID Value**<br>_mshr_fk_department_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_omdepartmententityid of mshr_omdepartmententity entity | System-generated unique identifier of the department of the position. |
| **Reports To Position ID**<br>mshr_reportstopositionid<br>*String* | Read-only<br>Required | The user-readable ID of the position to which the recruited position reports in the organizational hierarchy. |
| **Reports To Position ID Value**<br>_mshr_fk_reportstoposition_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmpositionv2entityid of mshr_hcmpositionv2entity entity | The system-generated ID of the position to which the recruited position reports. |
| **Reports To Personnel Number**<br>mshr_reportstopersonnelnumber<br>*String* | Read-only<br>Required | The worker ID of the worker to which the hired candidate will report. |
| **Reports To Worker ID Value**<br>_mshr_fk_reportstoworker_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmworkerbaseentityid of mshr_hcmworkerbaseentity entity | System-generated ID of the worker to which the hired candidate will report. |
| **Financial Dimension**<br>mshr_financialdimension<br>*String* | Read-only<br>Optional | The financial dimension (for example, cost center) assigned to the position. The financial dimension is assigned for each position per legal entity. Cost centers that are defined in dimensions are accessible through the mshr_dimattributeomcostcenterentity entity. |
| **Data Area ID**<br>mshr_dataareaid<br>*String* | Read/write<br>Optional | Specifies the legal entity (company) for the recruiting request position. |
| **Data Area ID Value**<br>_mshr_dataareaid_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: cdm_companyid of cdm_company entity | System-generated GUID value identifying the legal entity (company) for the recruiting request position. |
| **Primary Field**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | Concatenation of Recruiting Request value and Position ID as another method to uniquely identify the record. |

## Entity: Recruiting Request Skill

Physical name: mshr_hcmrecruitingrequestskillentity

### Description

Describes skill requirements for a RecruitingRequest.

### JSON representation

```json
{
    "mshr_recruitingrequestid": "String",
    "mshr_skillid": "String",
    "mshr_skilldescription": "String",
    "mshr_ratinglevelid": "String",
    "mshr_ratingmodelid": "String",
    "mshr_ratingleveldescription": "String",
    "mshr_dataareaid": "String",
    "_mshr_dataareaid_id_value": "Guid",
    "mshr_primaryfield": "String",
    "_mshr_fk_recruitingrequest_id_value": "Guid",
    "_mshr_fk_skill_id_value": "Guid",
    "_mshr_fk_ratinglevel_id_value": "Guid",
    "_mshr_fk_ratingmodel_id_value": "Guid",
    "mshr_hcmrecruitingrequestskillentityid": "Guid"
}
```

### Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Recruiting Request Skill Entity ID**<br>mshr_hcmrecruitingrequestskillentityid<br>*GUID* | Read-only<br>Required | System-generated unique identifier for the **Recruiting Request Skill** record. |
| **Recruiting Request ID**<br>mshr_recruitingrequestid<br>*String* | Write-once<br>Required | The user-readable unique identifier of the associated recruiting request. |
| **Recruiting Request ID Value**<br>_mshr_fk_recruitingrequest_id_value<br>*GUID* | Read-only<br>Required<br> Foreign key: mshr_hcmrecruitingrequestentityid of mshr_hcmrecruitingrequestentity entity | System-generated unique identifier of the associated recruiting request. |
| **Skill ID**<br>mshr_skillid<br>*String*<br> | Write-once<br>Required | The user-readable unique identifier of the required skill. |
| **Skill ID Value**<br>_mshr_fk_skill_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmskillentityid of mshr_hcmskillentity entity | System-generated unique identifier of the required skill. |
| **Rating Level ID**<br>mshr_ratinglevelid<br>*String* | Write-once<br>Optional | The required skill level value selected for the job, based on the rating model assigned to the skill. |
| **Rating Level ID Value**<br>_mshr_fk_ratinglevel_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_hcmratinglevelentityid of mshr_hcmratinglevelentity entity | System-generated unique identifier for the level. |
| **Skill Description**<br>mshr_skilldescription<br>*String* | Read-only<br>Required | The skill description. |
| **Rating Level Description**<br>mshr_ratingleveldescription<br>*String* | Read-only<br>Optional | The description of the selected skill level. |
| **Data Area ID**<br>mshr_dataareaid<br>*String* | Read/write<br>Optional | Specifies the legal entity (company). |
| **Data Area ID Value**<br>_mshr_dataareaid_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: cdm_companyid of cdm_company entity | System-generated GUID value identifying the legal entity (company). |
| **Primary Field**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | Concatenation of Recruiting Request value and Skill ID as another method to uniquely identify the record. |
| **Rating Model ID**<br>mshr_ratingmodelid<br>*String* | Read-write<br>Required | The rating model used to rate the skill. |
| **Rating Model ID Value**<br>_mshr_fk_hcmratingmodel_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmratingmodelentityid of mshr_hcmratingmodelentity entity | System-generated unique identifier of the rating model used to rate the skill. |

## Entity: Recruiting Request Education

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

## Entity: Recruiting Request Location

Physical name: mshr_hcmrecruitingrequestlocationentity

### Description

The list of locations defined as locations where recruited employees will work upon hiring. These are locations created across legal entities.

### JSON representation

```
{
    "mshr_recruitingrequestlocationid": "String",
    "mshr_locationid": "String",
    "mshr_description": "String",
    "mshr_countryregionid": "String",
    "mshr_zipcode": "String",
    "mshr_street": "String",
    "mshr_city": "String",
    "mshr_state": "String",
    "mshr_county": "String",
    "mshr_telephone": "String",
    "mshr_email": "String",
    "mshr_internetaddress": "String",
    "_mshr_dataareaid_id_value": "Guid",
    "mshr_dataareaid": "String",
    "_mshr_fk_countryregion_id_value": "Guid",
    "mshr_hcmrecruitingrequestlocationentityid": "Guid"
}
```

### Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Location ID**<br>mshr_locationid<br>*String* | Write-once<br>Required | The system-generated, user-readable identifier for the recruiting location. |
| **Recruiting Request Location**<br>mshr_recruitingrequestlocationid<br>*String* | Write-once<br>Required | User-defined unique identifier for the recruiting location. |
| **Recruiting Request Location Entity ID**<br>mshr_hcmrecruitingrequestlocationentityid<br>*GUID* | Read-only<br>Required | System-generated unique identifier for the recruiting request location record. |
| **Description**<br>mshr_description<br>*String* | Read/write<br>Required | Description of the location. |
| **Country/Region ID**<br>mshr_countryregionid<br>*String* | Read-only<br>Optional | Specifies the country or region where the candidate has citizenship. |
| **Country/Region ID Value**<br>_mshr_fk_countriregion_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_logisticaddresscountryregionentityid of mshr_logisticsaddresscountryregionentity | System-generated unique identifier of the country/region of the address. |
| **ZipCode**<br>mshr_zipcode<br>*String* | Read-only<br>Optional | Zip/postal code. |
| **Street**<br>mshr_street<br>*String* | Read-only<br>Optional | Street address. |
| **City**<br>mshr_city<br>*String* | Read-only<br>Optional | City. |
| **State**<br>mshr_state<br>*String* | Read-only<br>Optional | State or province. |
| **County**<br>mshr_county<br>*String* | Read-only<br>Optional | County. |
| **Telephone**<br>mshr_telephone<br>*String* | Read/write<br>Optional | Telephone number for the location. |
| **Email**<br>mshr_email<br>*String* | Read/write<br>Optional | Email address. |
| **InternetAddress**<br>mshr_internetaddress<br>*String* | Read/write<br>Optional | URL for the location website. |
| **Data Area ID**<br>mshr_dataareaid<br>*String* | Read/write<br>Optional | Specifies the legal entity (company). |
| **Data Area ID Value**<br>_mshr_dataareaid_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: cdm_companyid of cdm_company entity | System-generated GUID value identifying the legal entity (company). |

## Option set: Recruiting Request Status

Physical name: mshr_hcmrecruitingrequeststatus

This enumeration provides the option set for the status values of a RecruitingRequest.

| Value | Label | Description |
| --- | --- | --- |
| 200000000 | Draft | The request is in draft and isn't ready for active recruiting. |
| 200000001 | In Review | The request has been submitted and is being routed for approval by workflow. Only available when workflow is enabled. |
| 200000002 | Pending | The request is pending workflow action. Only available when workflow is enabled. |
| 200000003 | Canceled | The request has been canceled. Only available when workflow is enabled. |
| 200000004 | Denied | The request has been denied. Only available when workflow is enabled. |
| 200000005 | Active | Any workflow is completed and approved, and the request is ready for active recruiting. |
| 200000006 | Closed | The recruiting request is closed. |


## Option set: Recruiting Request Position Status

Physical name: mshr_hcmrecruitingrequestpositionstatus

This enumeration provides the option set for the status values of each position a recruiting request in the RecruitingRequestPosition entity.

| Value | Label | Description |
| --- | --- | --- |
| 200000000 | Open | The position in the recruiting request is open for recruiting. This does not indicate that there is no currently active position assignment for the position. There may be an employee in the position at the time of recruiting. It indicates only that the position is available for recruiting in the context of the recruiting request. |
| 200000001 | Filled | A worker has been selected for assignment to the position. |
| 200000002 | Canceled | The request to recruit for this position has been canceled. |


## Option set: Job Exempt Status

Physical name: cdm_jobexemptstatus

This enumeration specifies the option set for FLSA job exempt status values. This is provided in the existing cdm_jobexemptstatus option set.

| Value | Label | Description |
| --- | --- | --- |
| 200000000 | Exempt | The job has an exempt status based on FLSA guidelines. |
| 200000001 | NonExempt | The job has a non-exempt status based on FLSA guidelines. |
| 200000002 | Does Not Apply | FLSA status guidelines do not apply to the job. |

 
## Option set: Regulatory Job Category

Physical name: mshr_hcmregulatoryjobcategory

This enumeration specifies the option set for regulatory job category option set values. This is provided in the existing mshr_hcmregulatoryjobcategory option set.

| Value | Label | Description |
| --- | --- | --- |
| 200000000 | None | None. |
| 200000001 | Executive | Executive/Senior level officials and managers. |
| 200000002 | Manager | First/Mid level officials and managers. |
| 200000003 | Professional | Professionals. |
| 200000004 | Technician | Technicians. |
| 200000005 | SalesWorker | Sales workers. |
| 200000006 | Administrative | Administrative support workers. |
| 200000007 | CraftWorker | Craft workers. |
| 200000008 | Operative | Operatives. |
| 200000009 | Laborer | Laborers/Helpers. |
| 200000010 | ServiceWorker | Service workers. |

## Example query

The following query shows how you can use the $expand query option in a GET operation to retrieve a specified recruiting request record and all associated positions, required skills, and educational requirements for the specified request. The example response shows a recruiting request for two positions, and the required skills and education for the requested positions.

**Request**

```http
GET [Organizaton URI]/api/data/v9.1/mshr_hcmrecruitingrequestentities(<recruiting request entity ID>)?$expand=mshr_FK_HcmRecruitingRequestPositionEntity_RecruitingRequest,mshr_FK_HcmRecruitingRequestSkillEntity_RecruitingRequest,mshr_FK_HcmRecruitingRequestEducationEntity_RecruitingRequest
```

**Response**

```json
{
    "mshr_recruitingrequestid": "USMF-000001",
    "mshr_exemptstatus": 200000001,
    "mshr_regulatoryjobcategory": 200000000,
    "_mshr_fk_compensationlevel_id_value": "0000041c-0000-0000-ce27-fef003000000",
    "mshr_recruitingrequestlocationid": "",
    "mshr_hiringmanagerpersonnelnumber": "000662",
    "mshr_titleid": "Project Manager",
    "_mshr_fk_title_id_value": "000003a6-0000-0000-a4ff-004105000000",
    "_mshr_fk_jobtype_id_value": "000004ff-0000-0000-b127-fef003000000",
    "mshr_compensationhighthreshold": 92500,
    "mshr_comments": "",
    "mshr_description": "Project Manager",
    "mshr_estimatedstartdate": "2021-01-04T00:00:00Z",
    "_mshr_dataareaid_id_value": "e13a8e22-f278-ea11-a811-000d3a17b4eb",
    "_mshr_fk_recruiter_id_value": "00000007-0000-0000-5509-014105000000",
    "_mshr_fk_hiringmanager_id_value": "0000009e-0000-0000-2a0d-000010000000",
    "mshr_externaldescription": "A Program Manager plans and manages a program’s strategy and main objectives and assesses its impact in our organization.",
    "mshr_compensationlowthreshold": 70000,
    "mshr_hcmrecruitingrequestentityid": "00000d6b-0000-0000-0000-005001000000",
    "mshr_recruiterpartynumber": "HR000000518",
    "_mshr_fk_job_id_value": "00000ab2-0000-0000-baff-004105000000",
    "mshr_status": 200000005,
    "_mshr_fk_recruitingrequestlocation_id_value": null,
    "mshr_jobtypeid": "Managers",
    "mshr_defaultfulltimeequivalency": 1,
    "mshr_dataareaid": "usmf",
    "mshr_jobid": "Project Manager",
    "mshr_jobfunctionid": "0100",
    "mshr_compensationcontrolpoint": 80000,
    "mshr_compensationlevelid": "G05",
    "mshr_FK_HcmRecruitingRequestPositionEntity_RecruitingRequest": [
        {
            "mshr_description": "Project Manager",
            "mshr_positiontypeid": "Full-time",
            "mshr_hcmrecruitingrequestpositionentityid": "00000d6b-0000-0000-ee02-005001000000",
            "mshr_primaryfield": "USMF-000001 | 000426",
            "_mshr_fk_position_id_value": "000006b9-0000-0000-0e03-014105000000",
            "_mshr_fk_reportstoworker_id_value": "0000009e-0000-0000-ea01-014105000000",
            "_mshr_dataareaid_id_value": "e13a8e22-f278-ea11-a811-000d3a17b4eb",
            "_mshr_fk_positiontype_id_value": "000008e5-0000-0000-ab27-fef003000000",
            "_mshr_fk_recruitingrequest_id_value": "00000d78-0000-0000-0000-005001000000",
            "_mshr_fk_department_id_value": "00000b01-0000-0000-0108-014105000000",
            "mshr_reportstopositionid": "000434",
            "mshr_reportstopersonnelnumber": "000364",
            "mshr_financialdimension": "007",
            "mshr_dataareaid": "usmf",
            "_mshr_fk_reportstoposition_id_value": "000006b9-0000-0000-1603-014105000000",
            "mshr_status": 200000001,
            "mshr_departmentnumber": "028",
            "mshr_recruitingrequestid": "USMF-000001",
            "mshr_positionid": "000426"
        },
        {
            "mshr_description": "Project Manager",
            "mshr_positiontypeid": "Full-time",
            "mshr_hcmrecruitingrequestpositionentityid": "00000d6b-0000-0000-0000-005001000000",
            "mshr_primaryfield": "USMF-000001 | 000461",
            "_mshr_fk_position_id_value": "000006b9-0000-0000-3103-014105000000",
            "_mshr_fk_reportstoworker_id_value": "0000009e-0000-0000-8601-014105000000",
            "_mshr_dataareaid_id_value": "e13a8e22-f278-ea11-a811-000d3a17b4eb",
            "_mshr_fk_positiontype_id_value": "000008e5-0000-0000-ab27-fef003000000",
            "_mshr_fk_recruitingrequest_id_value": "00000d78-0000-0000-0000-005001000000",
            "_mshr_fk_department_id_value": "00000b01-0000-0000-0108-014105000000",
            "mshr_reportstopositionid": "000329",
            "mshr_reportstopersonnelnumber": "000277",
            "mshr_financialdimension": "019",
            "mshr_dataareaid": "usmf",
            "_mshr_fk_reportstoposition_id_value": "000006b9-0000-0000-1401-014105000000",
            "mshr_status": 200000000,
            "mshr_departmentnumber": "028",
            "mshr_recruitingrequestid": "USMF-000001",
            "mshr_positionid": "000461"
        }
    ],
    "mshr_FK_HcmRecruitingRequestSkillEntity_RecruitingRequest": [
        {
            "_mshr_fk_skill_id_value": "00000228-0000-0000-c3ff-004105000000",
            "mshr_skillid": "Present",
            "mshr_dataareaid": "usmf",
            "_mshr_dataareaid_id_value": "e13a8e22-f278-ea11-a811-000d3a17b4eb",
            "mshr_ratinglevelid": "4",
            "_mshr_fk_recruitingrequest_id_value": "00000d78-0000-0000-0000-005001000000",
            "mshr_skilldescription": "Organize and present ideas",
            "mshr_recruitingrequestid": "USMF-000001",
            "mshr_ratingmodelid": "Skills",
            "mshr_primaryfield": "USMF-000001 | Present",
            "_mshr_fk_ratingmodel_id_value": "0000066e-0000-0000-79ff-004105000000",
            "_mshr_fk_ratinglevel_id_value": "000000c3-0000-0000-87ff-004105000000",
            "mshr_hcmrecruitingrequestskillentityid": "00000d69-0000-0000-0000-005001000000",
            "mshr_ratingleveldescription": "Advanced"
        },
        {
            "_mshr_fk_skill_id_value": "00000228-0000-0000-d3ff-004105000000",
            "mshr_skillid": "ProjectMgmt",
            "mshr_dataareaid": "usmf",
            "_mshr_dataareaid_id_value": "e13a8e22-f278-ea11-a811-000d3a17b4eb",
            "mshr_ratinglevelid": "5",
            "_mshr_fk_recruitingrequest_id_value": "00000d78-0000-0000-0000-005001000000",
            "mshr_skilldescription": "Project management",
            "mshr_recruitingrequestid": "USMF-000001",
            "mshr_ratingmodelid": "Skills",
            "mshr_primaryfield": "USMF-000001 | ProjectMgmt",
            "_mshr_fk_ratingmodel_id_value": "0000066e-0000-0000-79ff-004105000000",
            "_mshr_fk_ratinglevel_id_value": "000000c3-0000-0000-88ff-004105000000",
            "mshr_hcmrecruitingrequestskillentityid": "00000d69-0000-0000-0300-005001000000",
            "mshr_ratingleveldescription": "Expert"
        }
    ],
    "mshr_FK_HcmRecruitingRequestEducationEntity_RecruitingRequest": [
        {
            "mshr_educationdisciplineid": "Business Admin",
            "_mshr_fk_educationdiscipline_id_value": "000009e6-0000-0000-9eff-004105000000",
            "mshr_primaryfield": "USMF-000001 | Bachelor | Business Admin",
            "_mshr_fk_educationlevel_id_value": "00000d6d-0000-0000-82ff-004105000000",
            "mshr_educationdisciplinedescription": "Business Administration",
            "_mshr_fk_recruitingrequest_id_value": "00000d78-0000-0000-0000-005001000000",
            "mshr_dataareaid": "usmf",
            "mshr_recruitingrequestid": "USMF-000001",
            "mshr_hcmrecruitingrequesteducationentityid": "00000d75-0000-0000-ef02-005001000000",
            "mshr_educationlevelid": "Bachelor",
            "mshr_educationleveldescription": "Bachelor",
            "_mshr_dataareaid_id_value": "e13a8e22-f278-ea11-a811-000d3a17b4eb"
        },
        {
            "mshr_educationdisciplineid": "Business Mgmt",
            "_mshr_fk_educationdiscipline_id_value": "000009e6-0000-0000-9dff-004105000000",
            "mshr_primaryfield": "USMF-000001 | Bachelor | Business Mgmt",
            "_mshr_fk_educationlevel_id_value": "00000d6d-0000-0000-82ff-004105000000",
            "mshr_educationdisciplinedescription": "Business Management",
            "_mshr_fk_recruitingrequest_id_value": "00000d78-0000-0000-0000-005001000000",
            "mshr_dataareaid": "usmf",
            "mshr_recruitingrequestid": "USMF-000001",
            "mshr_hcmrecruitingrequesteducationentityid": "00000d75-0000-0000-0000-005001000000",
            "mshr_educationlevelid": "Bachelor",
            "mshr_educationleveldescription": "Bachelor",
            "_mshr_dataareaid_id_value": "e13a8e22-f278-ea11-a811-000d3a17b4eb"
        }
    ]
}
```

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Candidate to hire and related entities](hr-admin-integration-ats-api-candidate-entities.md)
