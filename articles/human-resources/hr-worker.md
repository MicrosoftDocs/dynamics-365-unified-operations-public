---
# required metadata

title: Worker entity
description: This article provides details and an example query for the Worker entity in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 04/24/2024
ms.topic: article

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# Worker entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Worker entity for Dynamics 365 Human Resources.

## Description

This entity provides information about the employee. Before you use this entity, you must set the payroll integration parameters.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| PersonnelNumber | mshr\_PersonnelNumber | String | Read-only |
| PartyNumber | mshr\_PartyNumber | String | Read-only |
| KnownAs | mshr\_KnownAs | String | Read-only |
| LanguageId | mshr\_LanguageId | String | Read-only |
| Name | mshr\_Name | String | Read-only |
| NameAlias | mshr\_NameAlias | String | Read-only |
| PhoneticFirstName | mshr\_PhoneticFirstName | String | Read-only |
| PhoneticLastName | mshr\_PhoneticLastName | String | Read-only |
| PhoneticMiddleName | mshr\_PhoneticMiddleName | String | Read-only |
| PrimaryAddressLocation | mshr\_PrimaryAddressLocation | Int64 | Read-only |
| PrimaryContactEmail | mshr\_PrimaryContactEmail | String | Read-only |
| PrimaryContactEmailDescription | mshr\_PrimaryContactEmailDescription | String | Read-only |
| PrimaryContactEmailIsIM | mshr\_PrimaryContactEmailIsIM | Enum | Read-only |
| PrimaryContactEmailIsPrivate | mshr\_PrimaryContactEmailIsPrivate | Enum | Read-only |
| PrimaryContactEmailPurpose | mshr\_PrimaryContactEmailPurpose | String | Read-only |
| PrimaryContactFax | mshr\_PrimaryContactFax | String | Read-only |
| PrimaryContactFaxDescription | mshr\_PrimaryContactFaxDescription | String | Read-only |
| PrimaryContactFaxExtension | mshr\_PrimaryContactFaxExtension | String | Read-only |
| PrimaryContactFaxIsPrivate | mshr\_PrimaryContactFaxIsPrivate| Enum | Read-only |
| PrimaryContactFaxPurpose | mshr\_PrimaryContactFaxPurpose | String | Read-only |
| PrimaryContactPhone | mshr\_PrimaryContactPhone | String | Read-only |
| PrimaryContactPhoneDescription | mshr\_PrimaryContactPhoneDescription | String | Read-only |
| PrimaryContactPhoneExtension | mshr\_PrimaryContactPhoneExtension | String | Read-only |
| PrimaryContactPhoneIsMobile | mshr\_PrimaryContactPhoneIsMobile | Enum | Read-only |
| PrimaryContactURLPurpose | mshr\_PrimaryContactURLPurpose | String | Read-only |
| PrimaryContactURLIsPrivate | mshr\_PrimaryContactURLIsPrivate | Enum | Read-only |
| PrimaryContactURLDescription | mshr\_PrimaryContactURLDescription | String | Read-only |
| PrimaryContactPhonePurpose | mshr\_PrimaryContactPhonePurpose | String | Read-only |
| PrimaryContactPhoneIsPrivate | mshr\_PrimaryContactPhoneIsPrivate | Enum | Read-only |
| PrimaryContactURL | mshr\_PrimaryContactURL | String | Read-only |
| PrimaryContactFacebook | mshr\_PrimaryContactFacebook | String | Read-only |
| PrimaryContactFacebookDescription | mshr\_PrimaryContactFacebookDescription | String | Read-only |
| PrimaryContactFacebookIsPrivate | mshr\_PrimaryContactFacebookIsPrivate | Enum | Read-only |
| PrimaryContactFacebookPurpose | mshr\_PrimaryContactFacebookPurpose | String | Read-only |
| PrimaryContactLinkedIn | mshr\_PrimaryContactLinkedIn | String | Read-only |
| PrimaryContactLinkedInDescription | mshr\_PrimaryContactLinkedInDescription | String | Read-only |
| PrimaryContactLinkedInIsPrivate | mshr\_PrimaryContactLinkedInIsPrivate | Enum | Read-only |
| PrimaryContactLinkedInPurpose | mshr\_PrimaryContactLinkedInPurpose | String | Read-only |
| PrimaryContactTwitter | mshr\_PrimaryContactTwitter | String | Read-only |
| PrimaryContactTwitterPurpose | mshr\_PrimaryContactTwitterPurpose | String | Read-only |
| PrimaryContactTwitterIsPrivate | mshr\_PrimaryContactTwitterIsPrivate | Enum | Read-only |
| PrimaryContactTwitterDescription | mshr\_PrimaryContactTwitterDescription | String | Read-only |
| ProfessionalSuffix | mshr\_ProfessionalSuffix | String | Read-only |
| ProfessionalTitle | mshr\_ProfessionalTitle | String | Read-only |
| PersonalTitle | mshr\_PersonalTitle | String | Read-only |
| PersonalSuffix | mshr\_PersonalSuffix | String | Read-only |
| TitleId | mshr\_TitleId | String | Read-only |
| OriginalHireDateTime | mshr\_OriginalHireDateTime | Date time offset | Read-only |
| SeniorityDate | mshr\_SeniorityDate | Date time offset | Read-only |
| AnniversaryDateTime | mshr\_AnniversaryDateTime | Date time offset | Read-only |
| OfficeLocation | mshr\_OfficeLocation | String | Read-only |
| OfficeLocationId | mshr\_OfficeLocationId | String | Read-only |
| SummaryValidFrom | mshr\_SummaryValidFrom | Date time offset | Read-only |
| SummaryValidTo | mshr\_SummaryValidTo | Date time offset | Read-only |
| BirthDate | mshr\_BirthDate | Date time offset | Read-only |
| CitizenshipCountryRegion | mshr\_CitizenshipCountryRegion | String | Read-only |
| NationalityCountryRegion | mshr\_NationalityCountryRegion | String | Read-only |
| DeceasedDate | mshr\_DeceasedDate | Date time offset | Read-only |
| DisabledVerificationDate | mshr\_DisabledVerificationDate | Date time offset | Read-only |
| Education | mshr\_Education | String | Read-only |
| EthnicOriginId | mshr\_EthnicOriginId | String | Read-only |
| FatherBirthCountryRegion | mshr\_FatherBirthCountryRegion | String | Read-only |
| Gender | mshr\_Gender | Enum | Read-only |
| IsDisabled | mshr\_IsDisabled | Enum | Read-only |
| IsFulltimeStudent | mshr\_IsFulltimeStudent | Enum | Read-only |
| MotherBirthCountryRegion | mshr\_MotherBirthCountryRegion | String | Read-only |
| NativeLanguageId | mshr\_NativeLanguageId | String | Read-only |
| PersonBirthCountryRegion | mshr\_PersonBirthCountryRegion | String | Read-only |
| PersonBirthCity | mshr\_PersonBirthCity | String | Read-only |
| IsDisabledVeteran | mshr\_IsDisabledVeteran | Enum | Read-only |
| IsExpatriateRulingApplicable | mshr\_IsExpatriateRulingApplicable | Enum | Read-only |
| ExpatriateRulingValidFrom | mshr\_ExpatriateRulingValidFrom | Date time offset | Read-only |
| ExpatriateRulingValidTo | mshr\_ExpatriateRulingValidTo | Date time offset | Read-only |
| MaritalStatus | mshr\_MaritalStatus | Enum | Read-only |
| NumberOfDependents | mshr\_NumberOfDependents | Int | Read-only |
| MilitaryServiceStartDate | mshr\_MilitaryServiceStartDate | Date time offset | Read-only |
| MilitaryServiceEndDate | mshr\_MilitaryServiceEndDate | Date time offset | Read-only |
| VeteranStatusId | mshr\_VeteranStatusId | String | Read-only |
| PersonDetailsValidFrom | mshr\_PersonDetailsValidFrom | Date time offset | Read-only |
| PersonDetailsValidTo | mshr\_PersonDetailsValidTo | Date time offset | Read-only |
| AddressBooks | mshr\_AddressBooks | String | Read-only |
| AddressCity | mshr\_AddressCity | String | Read-only |
| AddressCountryRegionId | mshr\_AddressCountryRegionId | String | Read-only |
| AddressCountryRegionISOCode | mshr\_AddressCountryRegionISOCode | String | Read-only |
| AddressCounty | mshr\_AddressCounty | String | Read-only |
| AddressDistrictName | mshr\_AddressDistrictName | String | Read-only |
| AddressLocationId | mshr\_AddressLocationId | String | Read-only |
| AddressNameDescription | mshr\_AddressNameDescription | String | Read-only |
| AddressPurpose | mshr\_AddressPurpose | String | Read-only |
| AddressState | mshr\_AddressState | String | Read-only |
| AddressStreet | mshr\_AddressStreet | String | Read-only |
| AddressZipCode | mshr\_AddressZipCode | String | Read-only |
| AddressValidFrom | mshr\_AddressValidFrom | Date time offset | Read-only |
| AddressValidTo | mshr\_AddressValidTo | Date time offset | Read-only |
| FirstName | mshr\_FirstName | String | Read-only |
| MiddleName | mshr\_MiddleName | String | Read-only |
| LastNamePrefix | mshr\_LastNamePrefix | String | Read-only |
| LastName | mshr\_LastName | String | Read-only |
| PartyType | mshr\_PartyType | String | Read-only |
| NameSequenceDisplayAs | mshr\_NameSequenceDisplayAs | String | Read-only |
| ElectronicLocationId | mshr\_ElectronicLocationId | String | Read-only |
| WorkerType | mshr\_WorkerType | Enum | Read-only |
| WorkerStatus | mshr\_WorkerStatus | Enum | Read-only |
| AllowRehire | mshr\_AllowRehire | Enum | Read-only |
| WorksFromHome | mshr\_WorksFromHome | Enum | Read-only |
| User | mshr\_User | String | Read-only |
| PersonUserValidFrom | mshr\_PersonUserValidFrom | Date time offset | Read-only |
| PersonUserValidTo | mshr\_PersonUserValidTo | Date time offset | Read-only |
| IdentityEmail | mshr\_IdentityEmail | String | Read-only |
| ObjectId | mshr\_ObjectId | GUID | Read-only |
| IdentityProvider | mshr\_IdentityProvider | String | Read-only |
| EthnicOrigin | mshr\_EthnicOrigin | Int64 | Read-only |
| Location | mshr\_Location | Int64 | Read-only |
| NameValidFrom | mshr\_NameValidFrom | Date time offset | Read-only |
| NameValidTo | mshr\_NameValidTo | Date time offset | Read-only |
| NativeLanguage | mshr\_NativeLanguage | String | Read-only |
| Person | mshr\_Person | Int64 | Read-only |
| PrimaryContactEmailRecordId | mshr\_PrimaryContactEmailRecordId | Int64 | Read-only |
| PrimaryContactFacebookRecordId | mshr\_PrimaryContactFacebookRecordId | Int64 | Read-only |
| PrimaryContactFaxRecordId | mshr\_PrimaryContactFaxRecordId | Int64 | Read-only |
| PrimaryContactLinkedInRecordId | mshr\_PrimaryContactLinkedInRecordId | Int64 | Read-only |
| PrimaryContactPhoneRecordId | mshr\_PrimaryContactPhoneRecordId | Int64 | Read-only |
| PrimaryContactTwitterRecordId | mshr\_PrimaryContactTwitterRecordId | Int64 | Read-only |
| PrimaryContactURLRecordId | mshr\_PrimaryContactURLRecordId | Int64 | Read-only |
| Title | mshr\_Title | Int64 | Read-only |
| VeteranStatus | mshr\_VeteranStatus | Int64 | Read-only |

## Example query for PayIntV1WorkerEntity

Physical name: mshr\_workerentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mshr_workerentities_
```

**Response**

```JSON
{  
    "mshr_personnelnumber": "000001",  
    "mshr_partynumber": "000000032",  
    "mshr_knownas": "",  
    "mshr_languageid": "en-us",  
    "mshr_name": "Jodi Christiansen",  
    "mshr_namealias": "Jodi Christiansen",  
    "mshr_phoneticfirstname": "",  
    "mshr_phoneticlastname": "",  
    "mshr_phoneticmiddlename": "",  
    "mshr_primarycontactemail": "<jodi@contoso.com>",  
    "mshr_primarycontactemaildescription": "Work",  
    "mshr_primarycontactemailisim": 200000001,  
    "mshr_primarycontactemailisprivate": 200000000,  
    "mshr_primarycontactemailpurpose": "Home",  
    "mshr_primarycontactfax": "",  
    "mshr_primarycontactfaxdescription": "",  
    "mshr_primarycontactfaxextension": "",  
    "mshr_primarycontactfaxisprivate": 200000000,  
    "mshr_primarycontactfaxpurpose": "",  
    "mshr_primarycontactphone": "425-555-5049",  
    "mshr_primarycontactphonedescription": "Work",  
    "mshr_primarycontactphoneextension": "5049",  
    "mshr_primarycontactphoneismobile": 200000000,  
    "mshr_primarycontactphoneisprivate": 200000000,  
    "mshr_primarycontactphonepurpose": "Home",  
    "mshr_primarycontacturl": "",  
    "mshr_primarycontacturldescription": "",  
    "mshr_primarycontacturlisprivate": 200000000,  
    "mshr_primarycontacturlpurpose": "",  
    "mshr_primarycontactfacebook": "",  
    "mshr_primarycontactfacebookdescription": "",  
    "mshr_primarycontactfacebookisprivate": 200000000,  
    "mshr_primarycontactfacebookpurpose": "",  
    "mshr_primarycontactlinkedin": "",  
    "mshr_primarycontactlinkedindescription": "",  
    "mshr_primarycontactlinkedinisprivate": 200000000,  
    "mshr_primarycontactlinkedinpurpose": "",  
    "mshr_primarycontacttwitter": "",  
    "mshr_primarycontacttwitterpurpose": "",  
    "mshr_primarycontacttwitterisprivate": 200000000,  
    "mshr_primarycontacttwitterdescription": "",  
    "mshr_professionalsuffix": "",  
    "mshr_professionaltitle": "",  
    "mshr_personaltitle": "",  
    "mshr_personalsuffix": "",  
    "mshr_titleid": "Compensation & Benefits Cons.",  
    "mshr_senioritydate": "2006-02-01T08:00:00Z",  
    "mshr_officelocation": "Building B - 5049",  
    "mshr_officelocationid": "000000034",  
    "mshr_summaryvalidfrom": "2012-09-20T21:23:17Z",  
    "mshr_summaryvalidto": "2154-12-31T23:59:59Z",  
    "mshr_birthdate": "1972-03-06T00:00:00Z",  
    "mshr_citizenshipcountryregion": "",  
    "mshr_nationalitycountryregion": "",  
    "mshr_education": "",  
    "mshr_ethnicoriginid": "White",  
    "mshr_fatherbirthcountryregion": "",  
    "mshr_gender": 200000002,  
    "mshr_isdisabled": 200000000,  
    "mshr_isfulltimestudent": 200000000,  
    "mshr_motherbirthcountryregion": "",  
    "mshr_nativelanguageid": "English",  
    "mshr_personbirthcountryregion": "",  
    "mshr_personbirthcity": "",  
    "mshr_isdisabledveteran": 200000000,  
    "mshr_isexpatriaterulingapplicable": 200000000,  
    "mshr_maritalstatus": 200000001,  
    "mshr_numberofdependents": 2,  
    "mshr_veteranstatusid": "",  
    "mshr_persondetailsvalidfrom": "2012-09-11T20:09:56Z",  
    "mshr_persondetailsvalidto": "2154-12-31T23:59:59Z",  
    "mshr_addressbooks": "",  
    "mshr_addresscity": "Bellevue",  
    "mshr_addresscountryregionid": "USA",  
    "mshr_addresscountryregionisocode": "US",  
    "mshr_addresscounty": "KING",  
    "mshr_addressdistrictname": "",  
    "mshr_addresslocationid": "000000594",  
    "mshr_addressnamedescription": "Home address",  
    "mshr_addresspurpose": "Home",  
    "mshr_addressstate": "WA",  
    "mshr_addressstreet": "3219 Oak St",  
    "mshr_addresszipcode": "98107",  
    "mshr_addressvalidfrom": "2012-09-20T21:23:11Z",  
    "mshr_addressvalidto": "2154-12-31T23:59:59Z",  
    "mshr_firstname": "Jodi",  
    "mshr_middlename": "",  
    "mshr_lastnameprefix": "",  
    "mshr_lastname": "Christiansen",  
    "mshr_partytype": "Person",  
    "mshr_namesequencedisplayas": "FirstMiddleLast",  
    "mshr_electroniclocationid": "000000042",  
    "mshr_workertype": 200000001,  
    "mshr_workerstatus": 200000001,  
    "mshr_allowrehire": 200000000,  
    "mshr_worksfromhome": 200000000,  
    "mshr_user": "JODI",  
    "mshr_personuservalidfrom": "2013-03-10T18:17:42Z",  
    "mshr_personuservalidto": "2154-12-31T23:59:59Z",  
    "mshr_identityemail": "<JODI@contosoax7.onmicrosoft.com>",  
    "mshr_identityprovider": "<https://sts.windows.net/>",  
    "mshr_objectid": "4545ac9b-a78d-4721-b626-f0f700517eab",  
    "mshr_namevalidto": "2154-12-31T23:59:59Z",  
    "mshr_militaryserviceenddate": null,  
    "mshr_anniversarydatetime": null,  
    "mshr_expatriaterulingvalidto": null,  
    "mshr_militaryservicestartdate": null,  
    "mshr_deceaseddate": null,  
    "mshr_disabledverificationdate": null,  
    "mshr_expatriaterulingvalidfrom": null,  
    "versionnumber": null,  
    "mshr_namevalidfrom": null,  
    "mshr_originalhiredatetime": null  
}
```
