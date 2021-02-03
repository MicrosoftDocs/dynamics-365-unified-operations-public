---
# required metadata

title: Candidate to hire and related entities
description: This topic describes Candidate to hire and related entities for the Dynamics 365 Human Resources Applicant Tracking System (ATS) integration API.
author: andreabichsel
manager: tfehr
ms.date: 01/25/2021
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
ms.search.validFrom: 2021-01-25
ms.dyn365.ops.version: Platform update 36
---

# Candidate to hire and related entities

This topic describes Candidate to hire and related entities for the Dynamics 365 Human Resources Applicant Tracking System (ATS) integration API.

## Entity: Candidate to Hire

Physical name: mshr_hcmcandidatetohireentity

### Description

This entity provides candidate details used to create a worker in Dynamics 365 Human Resources. It's used to read all candidate records and create internal and external candidate records, allowing you to create personal details for the new candidate.

When creating an external candidate record who will be a new person record in the system, you must not define a party (person) number when posting a new candidate record. The new person entity record is created with the new candidate record.

When creating an internal candidate record (a candidate for the position who already has an employee record with the company), define the party (person) number of the record that already exists for person for the mshr_partynumber property on the candidate record rather than defining personal information (name, gender, birthdate, etc.) that would be used to create a new person record.

### JSON representation

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

### Properties

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
| **Comments**<br>mshr_comments<br>String | Read/write<br>Optional | Comments to be used by the recruiter and/or hiring manager. |
| **Application Integration Result**<br>mshr_applcantintegrationresult<br>mshr_applicantintegrationresult option set | Read/write<br>Required | The status of the candidate in the hiring process related to the integration. |
| **Do Not Hire Reason Code ID**<br>mshr_donothirereasoncodeid<br>String | Read/write<br>Optional | A reason code optionally provided when the status (application integration result) is set to “Not hired”. |
| **Reason Code ID Value**<br>_mshr_fk_reasoncode_id_value<br>GUID | Read-only<br>Optional<br>Foreign key: mshr_hcmreasoncodeentityid of mshr_hcmreasoncodeentity entity | System-generated unique identifier for the Do Not Hire Reason Code. |
| **Data Area ID**<br>mshr_dataareaid<br>String | Read/write<br>Optional | 	Specifies the legal entity (company). |
| **Data Area ID Value**<br>_mshr_dataareaid_id_value<br>GUID | Read-only<br>Optional<br>Foreign key: cdm_companyid of cdm_company entity | System-generated GUID value identifying the legal entity (company). |

## Entity: Person

Physical name: mshr_dirpersonentity

### Description

This entity provides the personal information for the individual who is the candidate.

### JSON representation

```json
{
    "mshr_partynumber": "String",
    "mshr_name": "String",
    "mshr_namealias": "String",
    "mshr_knownas": "String",
    "mshr_languageid": "String",
    "mshr_addressbooks": "String",
    "mshr_anniversaryday": Int,
    "mshr_anniversarymonth": Int,
    "mshr_anniversaryyear": Int,
    "mshr_birthday": Int,
    "mshr_birthmonth": Int,
    "mshr_birthyear": Int,
    "mshr_childrennames": "String",
    "mshr_gender": Int,
    "mshr_hobbies": "String",
    "mshr_initials": "String",
    "mshr_maritalstatus": Int,
    "mshr_phoneticfirstname": "String",
    "mshr_phoneticlastname": "String",
    "mshr_phoneticmiddlename": "String",
    "mshr_personalsuffix": "String",
    "mshr_personaltitle": "String",
    "mshr_professionalsuffix": "String",
    "mshr_professionaltitle": "String",
    "mshr_fullprimaryaddress": "String",
    "mshr_addresscity": "String",
    "mshr_addresscountryregionid": "String",
    "mshr_addresscountryregionisocode": "String",
    "mshr_addresscounty": "String",
    "mshr_addressdistrictname": "String",
    "mshr_addresslatitude": Decimal,
    "mshr_addresslocationid": "000003212",
    "mshr_addresslocationroles": "Home",
    "mshr_addresslongitude": Decimal,
    "mshr_addressstate": "String",
    "mshr_addressstreet": "String",
    "mshr_addressvalidfrom": "Date",
    "mshr_addressvalidto": "Date",
    "mshr_addresszipcode": "String",
    "mshr_addressisprivate": Int,
    "mshr_addressdescription": "String",
    "mshr_primarycontactemail": "String",
    "mshr_primarycontactemaildescription": "String",
    "mshr_primarycontactemailisim": Int,
    "mshr_primarycontactemailpurpose": "String",
    "mshr_primarycontactfax": "String",
    "mshr_primarycontactfaxdescription": "String",
    "mshr_primarycontactfaxextension": "String",
    "mshr_primarycontactfaxpurpose": "String",
    "mshr_primarycontactphone": "String",
    "mshr_primarycontactphonedescription": "String",
    "mshr_primarycontactphoneextension": "String",
    "mshr_primarycontactphoneismobile": Int,
    "mshr_primarycontactphonepurpose": "String",
    "mshr_primarycontacttelex": "String",
    "mshr_primarycontacttelexdescription": "String",
    "mshr_primarycontacttelexpurpose": "String",
    "mshr_primarycontacturl": "String",
    "mshr_primarycontacturldescription": "String",
    "mshr_primarycontacturlpurpose": "String",
    "mshr_primarycontactfacebook": "String",
    "mshr_primarycontactfacebookdescription": "String",
    "mshr_primarycontactfacebookisprivate": Int,
    "mshr_primarycontactfacebookpurpose": "String",
    "mshr_primarycontactlinkedin": "String",
    "mshr_primarycontactlinkedindescription": "String",
    "mshr_primarycontactlinkedinisprivate": Int,
    "mshr_primarycontactlinkedinpurpose": "String",
    "mshr_primarycontacttwitter": "String",
    "mshr_primarycontacttwitterdescription": "String",
    "mshr_primarycontacttwitterisprivate": Int,
    "mshr_primarycontacttwitterpurpose": "String",
    "mshr_partytype": "String",
    "mshr_namesequencedisplayas": "String",
    "mshr_firstname": "String",
    "mshr_lastnameprefix": "String",
    "mshr_lastname": "String",
    "mshr_middlename": "String",
    "mshr_electroniclocationid": "String",
    "mshr_dirpersonentityid": "Guid",
    "mshr_addresstimezone": Int
}
```

### Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Person Entity ID**<br>mshr_dirpersonentityid<br>*GUID* | Read-only<br>Required<br>System-generated | A system-generated unique identifier for the entity record. |
| **Party Number**<br>mshr_partynumber<br>*String* | Read-only<br>Required<br>System-generated | A user-readable, system-generated unique identifier for the person.  |
| **Name**<br>mshr_name<br>*String* | Read-only<br>Required | The field value is a concatenation of First Name, Middle Name, Last Name Prefix, and Last Name in the order defined in the Name Sequence Display As field. |
| **Name Alias**<br>mshr_namealias<br>*String* | Read/write<br>Optional | A name alias that may be provided for the person. |
| **Known As**<br>mshr_knownas<br>*String* | Read/write<br>Optional | A name that may be used for the person if typically known as another name. |
| **Language ID**<br>mshr_languageid<br>*String* | Read/write<br>Optional | The language ID of the person’s primary language, as defined in ISO 639-1 format. |
| **Address books**<br>mshr_addressbooks<br>*String* | Read/write<br>Optional | Address book to which the person may be assigned. Address books that have been set up for the organization are listed in the mshr_diraddressbooksentity entity. |
| **Anniversary Day**<br>mshr_anniversaryday<br>*Int* | Read/write<br>Optional | The day of the person’s anniversary date. |
| **Anniversary Month**<br>mshr_anniversarymonth<br>*mshr_monthsofyear option set* | Read/write<br>Optional | The month of the person’s anniversary date. |
| **Anniversary Year**<br>mshr_anniversaryyear<br>*Int* | Read/write<br>Optional | The year of the person’s anniversary date. |
| **Birth Day**<br>mshr_birthday<br>*Int* | Read/write<br>Optional | The day of the person’s birthdate. |
| **Birth Month**<br>mshr_birthmonth<br>*mshr_monthsofyear option set* | Read/write<br>Optional | The month of the person’s birthdate. |
| **Birth Year**<br>mshr_birthyear<br>*Int* | Read/write<br>Optional | The year of the person’s birthdate. |
| **Children Names**<br>mshr_childrennames<br>*String* | Read/write<br>Optional | String for the names of the person’s children. There is no required delimitation. |
| **Gender**<br>mshr_gender<br>*mshr_hcmpersongender option set* | Read/write<br>Optional | The person’s gender. |
| **Hobbies**<br>mshr_hobbies<br>*String* | Read/write<br>Optional | The person’s hobbies. |
| **Initials**<br>mshr_initials<br>*String* | Read/write<br>Optional | The initials of the person’s name. |
| **Marital Status**<br>mshr_maritalstatus<br>*mshr_hcmpersonmaritalstatus option set* | Read/write<br>Optional | The person’s marital status. |
| **Phonetic First Name**<br>mshr_phoneticfirstname<br>*String* | Read/write<br>Optional | The phonetic pronunciation of the person’s first name. |
| **Phonetic Last Name**<br>mshr_phoneticlastname<br>*String* | Read/write<br>Optional | The phonetic pronunciation of the person’s last name. |
| **Phonetic Middle Name**<br>mshr_phoneticmiddlename<br>*String* | Read/write<br>Optional | The phonetic pronunciation of the person’s last name. |
| **Personal Suffix**<br>mshr_personalsuffix<br>*String* | Read/write<br>Optional | The person’s personal suffix. Valid values in the mshr_dirnameaffixentity entity where mshr_type is Suffix (200000001). |
| **Personal Title**<br>mshr_personaltitle<br>*String* | Read/write<br>Optional | A personal title for the person. Valid values in the mshr_dirnameaffixentity entity where mshr_type is Title (200000000).
| **Professional Suffix**<br>mshr_professionalsuffix<br>*String* | Read/write<br>Optional | A professional suffix. |
| **Professional Title**<br>mshr_professionaltitle<br>*String* | Read/write<br>Optional | A professional title. |
| **Full Primary Address**<br>mshr_fullprimaryaddress<br>*String* | Read/write<br>Optional | The person’s full primary address, a concatenation of the primary address fields. |
| **Address City**<br>mshr_addresscity<br>*String* | Read/write<br>Optional | The city of the person’s primary address. Set up in mshr_logisticsaddresscityentity entity. |
| **Address Country Region**<br>mshr_addresscountryregionid<br>*String* | Read/write<br>Optional | The country/region of the person’s primary address. Valid values in the mshr_logisticsaddresscountryregionentity entity. |
| **Address Country Region ISO Code**<br>mshr_addresscountryregionisocode<br>*String* | Read/write<br>Optional | The ISO code of the country of the person’s primary address. |
| **Address County**<br>mshr_addresscounty<br>*String* | Read/write<br>Optional | The county of the person’s primary address. Set up in mshr_logisticsaddresscountyentity entity. |
| **Address District Name**<br>mshr_addressdistrictname<br>*String* | Read/write<br>Optional | The district of the person’s primary address. Set up in mshr_logisticsaddressdistrictentity entity. |
| **Address Latitude**<br>mshr_addresslatitude<br>*String* | Read/write<br>Optional | The latitude of the person’s primary address. |
| **Address Location ID**<br>mshr_addresslocationid<br>*String* | Read/write<br>Optional | The unique identifier for the location of the person’s primary address. Valid values in mshr_logisticspostaladdresslocationcdsentity entity. |
| **Address Location Roles**<br>mshr_addresslocationroles<br>*String* | Read/write<br>Optional | The location role of the person’s primary address. Set up in the mshr_logisticslocationrolecdsentity entity. |
| **Address Longitude**<br>mshr_addresslongitude<br>*String* | 	Read/write<br>Optional | The longitude of the person’s primary address. |
| **Address State**<br>mshr_addressstate<br>*String* | Read/write<br>Optional | The state of the person’s primary address. Set up in mshr_logisticsaddressstateentity entity. |
| **Address Street**<br>mshr_addressstreet<br>*String* | Read/write<br>Optional | The street address of the person’s primary address. |
| **Address Valid From**<br>mshr_addressvalidfrom<br>*Date* | Read/write<br>Optional | The date from which the person’s primary address is valid. |
| **Address Valid To**<br>mshr_addressvalidto<br>*Date* | Read/write<br>Optional | The date to which the person’s primary address is valid. |
| **Address Zip Code**<br>mshr_addresszipcode<br>*String* | Read/write<br>Optional | The postal code of the person’s primary address. Set up in mshr_logisticsaddresspostalcodeentity entity. |
| **Address Is Private**<br>mshr_addressisprivate<br>*mshr_noyes option set* | Read/write<br>Optional | Determines whether the person’s primary address is shared with others in the organization. |
| **Address Description**<br>mshr_addressdescription<br>*String* | Read/write<br>Optional | Description for the person’s primary address. |
| **Primary Contact Email**<br>mshr_primarycontactemail<br>*String* | Read/write<br>Optional | The person’s primary email address. |
| **Primary Contact Email Description**<br>mshr_primarycontactemaildescription<br>*String* | Read/write<br>Optional | A description provided for the primary email address. |
| **Primary Contact Email is IM**<br>mshr_primarycontactemailisim<br>*mshr_noyes option set* | Read/write<br>Optional | Determines whether the primary email address is available for instant messages. |
| **Primary Contact Email Purpose**<br>mshr_primarycontactemailpurpose<br>*String* | Read/write<br>Optional | The purpose for the primary email address. Set up in mshr_logisticslocationroleentity entity. |
| **Primary Contact Fax**<br>mshr_primarycontactfax<br>*String* | Read/write<br>Optional | Primary fax number. |
| **Primary Contact Fax Description**<br>mshr_primarycontactfaxdescription<br>*String* | Read/write<br>Optional | Description provided for the primary fax number. |
| **Primary Contact Fax Extension**<br>mshr_primarycontactfaxextension<br>*String* | Read/write<br>Optional | The extension of the primary fax number. |
| **Primary Contact Fax Purpose**<br>mshr_primarycontactfaxpurpose<br>*String* | Read/write<br>Optional | The purpose for the primary fax number. Set up in mshr_logisticslocationroleentity entity.
| **Primary Contact Phone**<br>mshr_primarycontactphone<br>*String* | Read/write<br>Optional | Primary phone number. |
| **Primary Contact Phone Description**<br>mshr_primarycontactphonedescription<br>*String* | Read/write<br>Optional | Description provided for the primary phone number. |
| **Primary Contact Phone Extension**<br>mshr_primarycontactphoneextension<br>*String* | Read/write<br>Optional | The extension of the primary phone number. |
| **Primary Contact Phone Is Mobile**<br>mshr_primarycontactphoneismobile<br>*mshr_noyes option set* | Read/write<br>Optional | Determines whether the primary phone number is a mobile phone. |
| **Primary Contact Phone Purpose**<br>mshr_primarycontactphonepurpose<br>*String* | Read/write<br>Optional | The purpose for the primary phone number. Set up in mshr_logisticslocationroleentity entity. |
| **Primary Contact Telex**<br>mshr_primarycontacttelex<br>*String* | Read/write<br>Optional | Primary telex number. |
| **Primary Contact Telex Description**<br>mshr_primarycontacttelexdescription<br>*String* | Read/write<br>Optional | Description provided for the person’s primary telex number. |
| **Primary Contact Telex Purpose**<br>mshr_primarycontacttelexpurpose<br>*String* | Read/write<br>Optional | The purpose for the person’s primary telex number. Set up in mshr_logisticslocationroleentity entity. |
| **Primary Contact URL**<br>mshr_primarycontacturl<br>*String* | Read/write<br>Optional | The primary URL. |
| **Primary Contact URL Description**<br>mshr_primarycontacturldescription<br>*String* | Read/write<br>Optional | Description provided for the person’s primary URL. |
| **Primary Contact URL Purpose**<br>mshr_primarycontacturldescription<br>*String* | Read/write<br>Optional | The purpose for the person’s primary URL. Set up in mshr_logisticslocationroleentity entity. |
| **Primary Contact Facebook**<br>mshr_primarycontactfacebook<br>*String* | Read/write<br>Optional | Primary Facebook account. Identified by User ID. |
| **Primary Contact Facebook Description**<br>mshr_primarycontactfacebookdescription<br>*String* | Read/write<br>Optional | Description provided for the person’s primary Facebook account. |
| **Primary Contact Facebook is Private**<br>mshr_primarycontactfacebookisprivate<br>*mshr_noyes option set* | Read/write<br>Optional | Determines whether the primary Facebook account is visible to other users. |
| **Primary Contact Facebook Purpose**<br>mshr_primarycontactfacebookpurpose<br>*String* | Read/write<br>Optional | The purpose for the person’s primary Facebook account. Set up in mshr_logisticslocationroleentity entity. |
| **Primary Contact LinkedIn**<br>mshr_primarycontactlinkedin<br>*String* | Read/write<br>Optional | Primary LinkedIn account. Identified by user name. |
| **Primary Contact LinkedIn Description**<br>mshr_primarycontactlinkedindescription<br>*String* | Read/write<br>Optional | Description provided for the person’s primary LinkedIn account. |
| **Primary Contact LinkedIn Is Private**<br>mshr_primarycontactlinkedinisprivate<br>*mshr_noyes option set* | Read/write<br>Optional | Determines whether the person’s primary LinkedIn account information is shared with other users. |
| **Primary Contact LinkedIn Purpose**<br>mshr_primarycontactlinkedinpurpose<br>*String* | Read/write<br>Optional | The purpose for the person’s primary LinkedIn account. Set up in mshr_logisticslocationroleentity entity. |
| **Primary Contact Twitter**<br>mshr_primarycontacttwitter<br>*String* | Read/write<br>Optional | The person’s primary Twitter account. Identified by @username. |
| **Primary Contact Twitter Description**<br>mshr_primarycontacttwitterdescription<br>*String* | Read/write<br>Optional | Description provided for the person’s primary Twitter account. |
| **Primary Contact Twitter Is Private**<br>mshr_primarycontacttwitterisprivate<br>*mshr_noyes option set* | Read/write<br>Optional | Determines whether the person’s primary Twitter account information is shared with other users. |
| **Primary Contact Twitter Purpose**<br>mshr_primarycontacttwitterpurpose<br>*String* | Read/write<br>Optional | The purpose for the person’s primary Twitter account. Set up in mshr_logisticslocationroleentity entity. |
| **Party Type**<br>mshr_partytype<br>*String* | Read/write<br>Optional | The party type of the person. Will always be **Person** for candidates. |
| **Name Sequence Display As**<br>mshr_namesequencedisplayas<br>*String* | Read/write<br>Optional | The sequence in which the person’s name properties are concatenated to form the Name (mshr_name) property value. |
| **First Name**<br>mshr_firstname<br>*String* | Read/write<br>Required | The person’s first name. |
| **Middle Name**<br>mshr_middlename<br>*String* | Read/write<br>Optional | The person’s middle name. |
| **Last Name Prefix**<br>mshr_lastnameprefix<br>*String* | Read/write<br>Optional | The prefix of the person’s last name. |
| **Last Name**<br>mshr_lastname<br>*String* | Read/write<br>Optional | The person’s last name. |
| **Electronic Location ID**<br>mshr_electroniclocationid<br>*String* | Read/write<br>Optional | The ID of the person’s electronic location. |
| **Address Time Zone**<br>mshr_addresstimezone<br>*Int* | Read/write<br>Optional | The time zone of the person’s primary address. |


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
    "mshr_comments": "Evenly's experience is exactly what we need for this position.",
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
