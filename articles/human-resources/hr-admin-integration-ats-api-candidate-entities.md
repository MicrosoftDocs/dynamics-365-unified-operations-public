---
# required metadata

title: Candidate to hire and related entities
description: This topic describes Candidate to hire and related entities for the Dynamics 365 Human Resources Applicant Tracking System (ATS) integration API.
author: andreabichsel
manager: tfehr
ms.date: 02/05/2021
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
ms.search.validFrom: 2021-02-05
ms.dyn365.ops.version: Platform update 36
---

# Candidate to hire and related entities

This topic describes Candidate to hire and related entities for the Dynamics 365 Human Resources Applicant Tracking System (ATS) integration API.


## Entity: Person Education

Physical name: mshr_hcmpersoneducationentity

### Description

This entity contains the educational history of the person who is the candidate. The education is linked to the person record enabling the education to be associated with any other roles created for the person in addition to the candidate record (worker, contractor, etc.).

### JSON representation

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

### Properties

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
| **Education Level ID Value**<br>_mshr_fk_educationlevel_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_hcmeducationdegreeentityid of mshr_hcmeducationdegreeentity entity | System-generated identifier for the education degree record. This provides the degrees and education levels defined for the organization. |
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
| **Notes**<br>mshr_notes<br>*String* | Read/write<br>Optional | Notes for use by the recruiter and/or hiring manager. |
| **Primary Field**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | Field used as another primary identifier of the entity record. Combination of party number, education discipline ID, education institution ID, and education level ID. |

## Entity: Person Professional Experience

Physical name: mshr_hcmpersonprofessionalexperienceentity

### Description

This entity describes professional experience or work history of a candidate.

### JSON representation

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

### Properties

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
| **Notes**<br>mshr_note<br>*String* | Read/write<br>Optional | Notes for use by the recruiter and/or hiring manager. |
| **Primary Field**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | Field used as a primary identifier of the entity record. Combination of party number, start date, employer position, and employer name. |


## Entity: Person Address

Physical name: mshr_hcmpersonaddressentities

### Description

This entity contains the list of postal addresses for candidate records.

### JSON representation

```json
{
    "mshr_partynumber": "String",
    "mshr_locationid": "String",
    "mshr_description": "String",
    "mshr_roles": "String",
    "mshr_countryregionid": "String",
    "mshr_zipcode": "String",
    "mshr_street": "String",
    "mshr_city": "String",
    "mshr_state": "String",
    "mshr_county": "String",
    "mshr_isprimary": Int,
    "mshr_isprivate": Int,
    "mshr_primaryfield": "String",
    "_mshr_fk_person_id_value": "Guid",
    "_mshr_fk_countryregion_id_value": "Guid",
    "mshr_hcmpersonaddressentityid": "Guid"
}
```

### Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Person Address Entity ID**<br>mshr_hcmpersonaddressentityid<br>*String* | Read-only<br>Required | System-generated unique identifier for the entity record. |
| **Party Number**<br>mshr_partynumber<br>*String* | Read/write<br>Required | The ID of the associated party (person) record. |
| **Person ID Value**<br>_mshr_fk_person_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_dirpersonentityid of mshr_dirpersonentity | The system-generated identifier of the party (person) entity record. |
| **Location ID**<br>mshr_locationid<br>*String* | Read/write<br>Required | The location ID of the address record. Set up in mshr_logisticspostaladdresslocationcdsentity entity. |
| **Description**<br>mshr_description<br>*String* | Read/write<br>Required | A description of the candidate’s address. |
| **Roles**<br>mshr_roles<br>*String* | Read/write<br>Required | The roles assigned for the purpose of this address. More than one role can be assigned. Each role should be separated by a semicolon. Valid values contained in the mshr_logisticslocationroleentity entity. |
| **Street**<br>mshr_street<br>*String* | Read/write<br>Optional | The street number. |
| **City**<br>mshr_city<br>*String* | Read/write<br>Optional | The city of the address. Set up in mshr_logisticsaddresscityentity entity. |
| **State**<br>mshr_state<br>*String* | Read/write<br>Optional | The state of the address. Set up in mshr_logisticsaddressstateentity entity. |
| **County**<br>mshr_county<br>*String* | Read/write<br>Optional | The county of the address. Set up in mshr_logisticsaddresscountyentity entity. |
| **Zip Code**<br>mshr_zipcode<br>*String* | Read/write<br>Optional | The zip/postal code of the address. Set up in mshr_logisticsaddresspostalcodeentity entity. |
| **Country Region ID**<br>mshr_countryregionid<br>*String* | Read/write<br>Optional | The country or region of the address. |
| **Country/Region ID Value**<br>_mshr_fk_countriregion_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_logisticaddresscountryregionentityid of mshr_logisticsaddresscountryregionentity | System-generated unique identifier of the country/region of the address. |
| **Is Primary**<br>mshr_isprimary<br>*mshr_noyes option set* | Read/write<br>Required | Identifies whether this is the primary address for the person of the defined role. |
| **Is Private**<br>mshr_isprivate<br>*mshr_noyes option set* | Read/write<br>Required | Identifies whether this is a private address for the person. |
| **Primary Field**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | Field used as a primary identifier of the entity record. Combination of party number and location ID. |

## Entity: Party Contact 

Physical name: mshr_dirpartycontactentities

### Description

This entity describes the candidate’s contact information, including phone, email, and social media accounts.

### JSON representation

```json
{
    "mshr_partynumber": "String",
    "mshr_locationid": "String",
    "mshr_description": "String",
    "mshr_type": Int,
    "mshr_countryregioncode": "String",
    "mshr_locator": "String",
    "mshr_locatorextension": "String",
    "mshr_purpose": "String",
    "mshr_ismobilephone": Int,
    "mshr_isinstantmessage": Int,
    "mshr_isprimary": Int,
    "mshr_isprivate": Int,
    "mshr_primaryfield": "String",
    "_mshr_fk_person_id_value": "String",
    "mshr_dirpartycontactentityid": "String"
}
```

### Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Party Contact Entity ID**<br>mshr_dirpartycontactentityid<br>*String* | Read-only<br>Required | System-generated unique identifier for the entity record. |
| **Party Number**<br>mshr_partynumber<br>*String* | Read/write<br>Required | The ID of the associated party (person) record. |
| **Person ID Value**<br>_mshr_fk_person_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_dirpersonentityid of mshr_dirpersonentity | The system-generated identifier of the party (person) entity record. |
| **Location ID**<br>mshr_locationid<br>*String* | Read/write<br>Required | The location ID of the address record. Set up in mshr_logisticspostaladdresslocationcdsentity entity. |
| **Description**<br>mshr_description<br>*String* | Read/write<br>Required | The description of the contact details. |
| **Type**<br>mshr_type<br>*mshr_logisticselectronicaddressmethodtype option set* | Read/write<br>Required | The contact detail type. |
| **Country Region Code**<br>mshr_countryregioncode<br>*String* | Read/write<br>Optional | The country or region of the address. |
| **Locator**<br>mshr_locator<br>*String* | Read/write<br>Optional | The contact details. For example, if the type is **Email address**, then this field contains the candidate’s email address. |
| **Locator Extension**<br>mshr_locatorextension<br>*String* | Read/write<br>Optional | The locator extension. For example, if the type is **Phone**, then this would contain the phone number extension. |
| **Is Mobile**<br>mshr_ismobile<br>*mshr_noyes option set* | Read/write<br>Required | Specifies whether the phone is a mobile number. |
| **Is Instant Message**<br>mshr_isinstantmessage<br>*mshr_noyes option set* | Read/write<br>Required | Specifies whether the phone is enabled for instant messaging. |
| **Is Primary**<br>mshr_isprimary<br>*mshr_noyes option set* | Read/write<br>Required | Determines the primary contact of the contact type. There must be only one primary record per contact type. |
| **Is Private**<br>mshr_isprivate<br>*mshr_noyes option set* | Read/write<br>Required | Identifies whether this is a private address for the person. |
| **Purpose**<br>mshr_purpose<br>*String* | Read/write<br>Optional | The purpose/role of the contact details. |
| **Primary Field**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | Field used as a primary identifier of the entity record. Combination of party number, type, description, and locator. |

## Entity: Person Skill

Physical name: mshr_hcmpersonskillentity

### Description

This entity describes skills possessed by a candidate.

### JSON representation

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

### Properties

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
| **Level ID**<br>mshr_levelid<br>*String* | Read/write<br>Required | The ID of the Rating Level the candidate possesses for this skill. |
| **Rating Level ID Value**<br>_mshr_fk_ratinglevel_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmratinglevelentityid of mshr_hcmratinglevelentity | The system-generated identifier of the rating level. |
| **Level Date**<br>mshr_leveldate<br>*Datetime* | Read/write<br>Required | The date at which the candidate was rated in the skill. |
| **Rating Level Examiner**<br>mshr_ratinglevelexaminer<br>*String* | Read/write<br>Optional | The personnel number of the worker who rated the candidate. |
| **Rating Level Examiner ID Value**<br>_mshr_fk_ratinglevelexaminer_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_hcmworkerentityid of mshr_hcmworkerentity | The system-generated identifier of the worker who examined the candidate’s skill level. |
| **Verified**<br>mshr_verified<br>*mshr_noyes option set* | Read/write<br>Required | Indicates whether the assessed skill level has been verified. |
| **Primary Field**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | Field to be used as an identifier of the entity record. Combination of party number, level type, skill ID, and level date. |

## Entity: Rating Level

Physical name: mshr_hcmratinglevelentity

### Description

This entity provides the available rating levels for skills. Rating levels apply across all legal entities.

### JSON representation

```json
{
    "mshr_description": "String",
    "mshr_factor": Int,
    "mshr_note": "String",
    "mshr_ratinglevelid": "String",
    "mshr_ratingmodelid": "String",
    "mshr_primaryfield": "String",
    "_mshr_fk_ratingmodelentity_id_value": "Guid",
    "mshr_hcmratinglevelentityid": "Guid"
}
```

### Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Rating Level Entity ID**<br>mshr_hcmratinglevelentityid<br>*GUID* | Read-only<br>Required<br>System-generated | The system-generated unique identifier for the level. |
| **Rating Level ID**<br>mshr_ratinglevelid<br>*String* | Read/write<br>Required | User-readable unique identifier for the level. |
| **Rating Model ID**<br>mshr_ratingmodelid<br>*String* | Read/write<br>Required | The rating model to which the rating level belongs. |
| **Rating Model Entity ID**<br>_mshr_fk_ratingmodelentity_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmratingmodelentityid of mshr_hcmratingmodelentity | The system-generated identifier for the rating model to which the rating level belongs. |
| **Description**<br>mshr_description<br>*String* | Read/write<br>Required | The description of the rating level. |
| **Factor**<br>mshr_factor<br>*Integer* | Read/write<br>Required | The factor for the rating level. When you compare items with a different number of rating levels, the factor is used to normalize the scores. The value must be an integer between 0 and 9. |
| **Note**<br>mshr_note<br>*String* | Read/write<br>Optional | Any notes associated with the rating level. |
| **Primary Field**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | Field to be used as an identifier of the entity record. Combination of rating level ID and rating model ID. |

## Entity: Person Certificate

Physical name: mshr_hcmpersoncertificateentity

### Description

This entity describes professional certificates possessed by a candidate. 

### JSON representation

```json
{
    "mshr_certificatetypeid": "String",
    "mshr_startdate": "Date",
    "mshr_enddate": "Date",
    "mshr_notes": "String",
    "mshr_partynumber": "String",
    "mshr_primaryfield": "String",
    "_mshr_fk_certificatetype_id_value": "Guid",
    "_mshr_fk_person_id_value": "Guid",
    "mshr_hcmpersoncertificateentityid": "Guid"
}
```

### Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Person Certificate Entity ID**<br>mshr_hcmpersoncertificateentityid<br>*GUID* | Read-only<br>Required | System-generated unique identifier for the person certificate entity record. |
| **Party Number**<br>mshr_partynumber<br>*String* | Read/write<br>Required | The party (person) ID of the candidate. |
| **Person ID Value**<br>_mshr_fk_person_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_dirpersonentityid of mshr_dirpersonentity | The system-generated identifier of the party (person) entity record. |
| **Certificate Type ID**<br>mshr_certificatetypeid<br>*String* | Read/write<br>Required | 	The identifier of the certificate type defined in Human Resources. |
| **Certificate Type ID Value**<br>_mshr_fk_certificatetype_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmcertificatetypeentityid of mshr_hcmcertificatetypeentity | System-generated unique identifier of the certificate type in the associated entity. |
| **Start Date**<br>mshr_startdate<br>*Datetime* | Read/write<br>Required | The date at which the certificate was issued. |
| **End Date**<br>mshr_enddate<br>*Datetime* | Read/write<br>Optional | The date at which the certificate will expire. |
| **Notes**<br>mshr_notes<br>*String* | Read/write<br>Optional | Notes for use by hiring managers and recruiters. |
| **Primary Field**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | 	Field to be used as an identifier of the entity record. Combination of party number, certificate type ID, and start date. |

## Entity: Certificate Type

Physical name: mshr_hcmcertificatetypeentity

### Description

This entity defines the list of professional certificate types set up in Human Resources. The entity is not specific to a legal entity (company).

### JSON representation

```json
{
    "mshr_certificatetype": "String",
    "mshr_description": "String",
    "mshr_requirerenewal": Int,
    "mshr_hcmcertificatetypeentityid": "Guid"
}
```

### Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Certificate Type Entity ID**<br>mshr_hcmcertificatetypeentityid<br>*GUID* | Read-only<br>Required 
System-generated | Unique primary identifier for the certificate type. |
| **Certificate Type**<br>mshr_certificatetype<br>*String* | Read/write<br>Required | Unique user-readable identifier for the certificate type. |
| **Description**<br>mshr_description<br>*String* | Read/write<br>Required | Description of the certificate type. |
| **Require Renewal**<br>mshr_requirerenewal<br>*mshr_noyes option set* | Read/write<br>Optional | Indicates whether renewal is required for the certificate. |

## Entity: Person Screening

Physical name: mshr_hcmpersonscreeningentity

### Description

This entity describes screenings a candidate has passed or must pass for employment.

### JSON representation

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

### Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Person Screening Entity ID**<br>mshr_hcmpersonscreeningentityid<br>*GUID* | Read-only<br>Required<br>System-generated | Unique primary identifier for the person screening record. |
| **Party Number**<br>mshr_partynumber<br>*String* | Read/write<br>Required | The party (person) number associated with the candidate. |
| **Person ID Value**<br>_mshr_fk_person_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_dirpersonentityid of mshr_dirpersonentity | The system-generated identifier of the party (person) entity record. |
| **Screening Type ID**<br>mshr_screeningtypeid<br>*String* | Read/write<br>Required<br>Foreign key: ScreeningType | The identifier of the screening type defined in Human Resources. |
| **Screening Type ID Value**<br>_mshr_fk_screeningtype_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmscreeningtypeentityid of mshr_hcmscreeningtypeentity | System-generated identifier for the screening type record in the associated entity. |
| **Required By**<br>mshr_requiredby<br>*Datetime* | Read/write<br>Optional | The date by which the screening is required to be completed. |
| **Status**<br>mshr_status<br>*mshr_hcmcompletionstatus option set*<br>Read/write<br>Required | Provides the candidate’s status regarding the screening. |
| **Completed Date**<br>mshr_completeddate<br>*Datetime* | Read/write<br>Optional | The date the screening was completed. |
| **Notes**<br>mshr_note<br>*String* | Read/write<br>Optional | Notes for use by hiring managers and recruiters. |

## Entity: Screening Types

Physical name: mshr_hcmscreeningtypeentity

### Description

This entity describes the screening types set up by the company for pre-employment and ongoing employee screening processes.

### JSON representation

```json
{
    "mshr_description": "String",
    "mshr_frequencyunit": Int,
    "mshr_generatefrom": Int,
    "mshr_frequencyinterval": Int,
    "mshr_screeningtypeid": "String",
    "mshr_hcmscreeningtypeentityid": "Guid"
}
```

### Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Screening Type Entity ID**<br>mshr_hcmscreeningtypeentityid<br>*GUID* | Read-only<br>Required<br>System-generated | Unique primary identifier for the screening type record. |
| **Screening Type ID**<br>mshr_screeningtypeid<br>*String* | Read/write<br>Required | User-defined unique identifier for the screening type. |
| **Description**<br>mshr_description<br>*String* | Read/write<br>Required | The description of the screening type. |
| **Frequency Unit**<br>mshr_frequencyunit<br>*mshr_hcmfrequencyunit option set* | Read/write<br>Required | Describes the frequency with which the screening must be completed for the assigned person. |
| **Generate From**<br>mshr_generatefrom<br>*mshr_hcmfrequencygeneratefrom option set* | Read-write<br>Required | If the Frequency value is any value other than “One-time only”, the GenerateFrom value determines the date from which to calculate the next screening event. |
| **Frequency Interval**<br>mshr_frequencyinterval<br>*Integer* | Read-write<br>Required | If the Frequency value is any value other than “One-time only”, an interval must be defined to define the number of units of time between each screening event. |

## Entity: Person Identification Number

Physical name: mshr_hcmpersonidentificationnumberentity

### Description

This entity describes the identification numbers for the person who is the candidate. It enables the API consumer to write identification numbers, like Social Security numbers or passport numbers, to the candidate record. Note that identification numbers are surfaced on the worker record, but not on the candidate record. So an integrating application can write the values to the Human Resources database, but the numbers won’t be visible to the user in Human Resources until the worker record is created for the candidate.

### JSON representation

```json
{
    "mshr_entrytype": "String",
    "mshr_description": "String",
    "mshr_expirationdate": "Datetime",
    "mshr_isprimary": Int,
    "mshr_identificationnumber": "String",
    "mshr_partynumber": "String",
    "mshr_identificationtypeid": "String",
    "mshr_issuingagencyid": "String",
    "mshr_primaryfield": "String",
    "_mshr_fk_person_id_value": "Guid",
    "_mshr_fk_issuingagency_id_value": "Guid",
    "_mshr_fk_identificationtype_id_value": "Guid",
    "mshr_hcmpersonidentificationnumberentityid": "Guid",
    "mshr_issueddate": "Datetime"
}
```

### Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Person Identification Number Entity ID**<br>mshr_hcmpersonidentificationnumberentityid<br>*GUID* | Read-only<br>Required<br>System-generated | Unique primary identifier for the person identification number record. |
| **Entry Type**<br>mshr_entrytype<br>*String* | Read-write<br>Optional | Free value to reference the type of entry for the identification number. |
| **Description**<br>mshr_description<br>*String* | Read-write<br>Optional | The description of the identification number. |
| **Expiration Date**<br>mshr_expirationdate<br>*Datetime* | Read-write<br>Optional | The date on which the identification number or associated document expires. |
| **Is Primary**<br>mshr_isprimary<br>*mshr_noyes option set* | Read-write<br>Optional | Defines whether the identification number is the primary record for the person for this identification type. |
| **Identification Number**<br>mshr_identificationnumber<br>*String* | Read-write<br>Required | The identification number. |
| **Party Number**<br>mshr_partynumber<br>*String* | Read-write<br>Required | The identifier of the party (person) owning the identification number. |
| **Person ID Value**<br>_mshr_fk_person_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_dirpersonentityid of mshr_dirpersonentity entity | The unique identifier of the party (person). |
| **Identification Type ID**<br>mshr_identificationtypeid<br>*String* | Read-write<br>Required | The type of identification number. |
| **Identification Type ID Value**<br>_mshr_fk_identificationtype_id_value<br>*GUID* | Read-only<br>Required<br>Foreign key: mshr_hcmidentificationtypeentityid of mshr_hcmidentificationtypeentity entity | System-generated unique identifier of the identification type. |
| **Issuing Agency ID**<br>mshr_issuingagencyid<br>*String* | Read-write<br>Optional | The agency or organization issuing the identification number. |
| **Issuing Agency ID Value**<br>_mshr_fk_issuingagency_id_value<br>*GUID* | Read-only<br>Optional<br>Foreign key: mshr_hcmissuingagencyentityid of mshr_hcmissuingagencyentity entity | System-generated unique identifier of the agency issuing the identification number. |
| **Primary Field**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | Field to be used as an identifier of the entity record. Combination of party number, identification type ID, and identification number. |
| **Issue Date**<br>mshr_issuedate<br>*Date* | Read-write<br>Optional | The date the identification number was issued. |

## Option set: No Yes

Physical name: mshr_noyes

This enumeration provides option set for typical Boolean properties in HR virtual entities.

| Value | Label | Description |
| --- | --- | --- |
| 200000000 | No | No. |
| 200000001 | Yes | Yes. |

## Option set: Blank Yes No

Physical name: mshr_hrmblankyesno

This enumeration provides option set for yes/no properties that also allow blanks.

| Value | Label | Description |
| --- | --- | --- |
| 200000000 | Blank | No value has been selected. |
| 200000001 | Yes | Yes. |
| 200000002 | No | No. |

## Option set: Skill Level Type

Physical name: mshr_hrmskillleveltype

This enumeration provides the option set of values that categorize the level assigned to a candidate’s skill.

| Value | Label | Description |
| --- | --- | --- |
| 200000000 | Actual | Actual skill level. |
| 200000001 | Target | Targeted value for the skill level. |

## Option set: Gender

Physical name: mshr_hcmpersongender

This enumeration provides the option set of genders for the candidate. This is available in the mshr_hcmpersongender option set.

| Value | Label | Description |
| --- | --- | --- |
| 200000000 | None | No gender has been specified. |
| 200000001 | Male | Male. |
| 200000002 | Female | Female. |
| 200000003 | NonSpecific | Selection for a non-specific gender. |

 
## Option set: Applicant Integration Result

Physical name: mshr_hcmapplicantintegrationresult

This enumeration provides status for a candidate record.

| Value | Label | Description |
| --- | --- | --- |
| 200000000 | Not processed | Candidate is still under consideration. |
| 200000001 | Hired | The candidate has been hired. |
| 200000002 | Not hired | Decision was made to not hire the candidate. |
| 200000003 | Dismissed | The candidate was dismissed from consideration. |

## Option set: Completion Status

Physical name: mshr_hcmcompletionstatus

This enumeration provides the option set of status values for candidate screenings. 

| Value | Label | Description |
| --- | --- | --- |
| 200000000 | Not Complete | The candidate has not yet completed the screening. |
| 200000001 | Pass | The candidate has passed the screening. |
| 200000002 | Fail | The candidate has failed the screening. |

## Option set: Contact Type

Physical name: mshr_logisticselectronicaddressmethodtype

This enumeration provides the option set of values for candidate contact types. 

| Value | Label | Description |
| --- | --- | --- |
| 200000000 | None | No type is selected. |
| 200000001 | Phone | Telephone number. |
| 200000002 | Email address | Email address. |
| 200000003 | URL | Website URL. |
| 200000004 | Telex | Telex number. |
| 200000005 | Fax | Fax number. |
| 200000006 | Facebook | Facebook account. Identified by User ID. |
| 200000007 | Twitter | Twitter account. Identified by @username. |
| 200000008 | LinkedIn | LinkedIn account. Identified by user name. |

## Option set: Screening Frequency

Physical name: mshr_hcmfrequencyunit

This enumeration provides the option set of values for the screening frequency. 

| Value | Label | Description |
| --- | --- | --- |
| 200000000	One-time only | The screening is required only once. |
| 200000001	Daily | The screening frequency is calculated in days. |
| 200000002	Weekly | The screening frequency is calculated in weeks. |
| 200000003	Monthly | The screening frequency is calculated in months. |
| 200000004	Yearly | The screening frequency is calculated in years. |

## Option set: Screening Frequency Generate From

Physical name: mshr_hcmfrequencygeneratefrom

This enumeration provides the option set of values for determining the start date of the calculation for the next required screening.

| Value | Label | Description |
| --- | --- | --- |
| 200000000	Not selected | No value has been selected. |
| 200000001	Date completed | Calculation is done from the last screening date completed. |
| 200000002	Date required | Calculation is done from the last screening date required. |

## Option set: Education Credit Basis
Physical name: mshr_hcmeducationcreditbasis

This enumeration provides the option set of values for education credit basis of the candidate’s education record.

| Value | Label | Description |
| --- | --- | --- |
| 200000000 | Blank | No value has been selected. |
| 200000001 | Semester | Semester. |
| 200000002 | Quarter | Quarter. |
| 200000003 | Trimester | Trimester. |
| 200000004 | Term | Term. |
| 200000005 | Other | Other. |

## Option set: Period Unit

Physical name: mshr_periodunit

This enumeration provides the option set of values for units of measurement for periods of time.

| Value | Label | Description |
| --- | --- | --- |
| 200000000 | Days | Day. |
| 200000001 | Months | Month. |
| 200000002 | Years | Year. |

## Option set: Months of Year

Physical name: mshr_monthsofyear

This enumeration provides the option set for the months of the year.

| Value | Label | Description |
| --- | --- | --- |
| 200000000 | None | No value has been selected. |
| 200000001 | January | January. |
| 200000002 | February | February. |
| 200000003 | March | March. |
| 200000004 | April | April. |
| 200000005 | May | May. |
| 200000006 | June | June. |
| 200000007 | July | July. |
| 200000008 | August | August. |
| 200000009 | September | September. |
| 200000010 | October | October. |
| 200000011 | November | November. |
| 200000012 | December | December. |

## Option set: Marital Status

Physical name: mshr_dirpersonmaritalstatus

This enumeration provides the option set for marital status of person records.

| Value | Label | Description |
| --- | --- | --- |
| 200000000 | None | No value has been selected.
| 200000001 | Single | Single. |
| 200000002 | Married | Married. |
| 200000003 | Divorced | Divorced. |
| 200000004 | Widowed | Widowhood. |

## Example query

The following is an example demonstrating how it is possible to use *deep inserts* to create all the detail of a new candidate record in a single API operation. For more information on deep inserts, see [Create related entity records in one operation](https://docs.microsoft.com/powerapps/developer/data-platform/webapi/create-entity-web-api#create-related-entity-records-in-one-operation).

The ```mshr_hcmcandidatetohireentity``` entity is unique because of its relationship to the ```mshr_dirpersonentity``` entity. Many of the properties on the ```mshr_hcmcandidatetohireentity``` (for example, ```mshr_firstname```, ```mshr_lastname```, and ```mshr_birthdate```) are derived from the ```mshr_dirpersonentity``` record. If you post a new candidate record to ```mshr_hcmcandidatetohireentity``` without using deep inserts, you are able to define values for these properties directly on the ```mshr_hcmcandidatetohireentity``` record, and the associated ```mshr_dirpersonentity``` record is created implicitly with the defined values for the properties. You can then create any other related entity records (skills, education, etc.) as separate API calls.

If, however, you want to use deep inserts to create all related entities in one operation, the properties specific to the ```mshr_dirpersonentity``` entity must be defined on that nested level of the operation.

This example shows how you can create a candidate record, the associated person record, and the person's skills and education in three nested levels using deep inserts in a single API operation.

    > [!NOTE]
    > The example does not include all properties of each of the API entities. It is simplified for demonstration purposes.

**Request**

```http
POST [Organization URI]/api/data/v9.1/mshr_hcmcandidatetohireentities
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

{
    "mshr_dataareaid": "usmf",
    "mshr_recruitingrequestid": "USMF-000141",
    "mshr_positionid": "000601",
    "mshr_iswillingtorelocate": 200000000,
    "mshr_availabilitydate": "2021-03-18",
    "mshr_comments": "Evelyn's experience is exactly what we need for this position.",
    "mshr_FK_Person_id":
            {
                "mshr_firstname": "Evelyn",
                "mshr_lastname": "Chambers",
                "mshr_namesequencedisplayas": "FirstMiddleLast",
                "mshr_FK_HcmPersonSkillEntity_Person":
                [
                    {
                        "mshr_skillid": "CustFocus",
                        "mshr_ratingid": "Skills",
                        "mshr_levelid": "4",
                        "mshr_ratinglevelexaminer": "",
                        "mshr_leveltype": 200000000,
                        "mshr_yearsofexperience": 0,
                        "mshr_verified": 200000000,
                        "mshr_leveldate": "2013-01-01T00:00:00Z"
                    },
                    {
                        "mshr_skillid": "CashFlow",
                        "mshr_ratingid": "Skills",
                        "mshr_levelid": "4",
                        "mshr_ratinglevelexaminer": "",
                        "mshr_leveltype": 200000000,
                        "mshr_yearsofexperience": 0,
                        "mshr_verified": 200000000,
                        "mshr_leveldate": "2013-01-01T00:00:00Z"
                    }
                ],
                "mshr_FK_HcmPersonEducationEntity_Person": [
                    {
                        "mshr_creditbasis": 200000000,
                        "mshr_enddate": "2021-02-22T00:00:00Z",
                        "mshr_educationlevelid": "Bachelor",
                        "mshr_creditsearned": 0,
                        "mshr_startdate": "2017-02-21T00:00:00Z",
                        "mshr_creditscompleted": 0,
                        "mshr_educationinstitutionid": "Cottonwood Univ",
                        "mshr_educationdisciplineid": "Business Mgmt",
                        "mshr_durationunit": 200000000
                    }              
                ]
            }
}
```

**Response**

```http
HTTP/1/1 204 No Content
OData-Version: 4.0
OData-EntityId: [Organization URI]/api/data/v9.1/mshr_hcmcandidatetohireentities(00000d2d-0000-0000-7317-005001000000)

```

## See also
[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Recruiting request and related entities](hr-admin-integration-ats-api-recruiting-entities.md)
