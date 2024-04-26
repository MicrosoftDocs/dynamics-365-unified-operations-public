---
# required metadata

title: Worker entity
description: This article provides details and an example query for the Worker entity in Microsoft Dynamics 365 Human Resources.
author: jcart
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
ms.author: jcart
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# Worker entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Worker entity (PayIntV1WorkerEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the employee. Before you use this entity, you must set the payroll integration parameters.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| PersonnelNumber | mserp\_PersonnelNumber | String | Read-only |
| PartyNumber | mserp\_PartyNumber | String | Read-only |
| KnownAs | mserp\_KnownAs | String | Read-only |
| LanguageId | mserp\_LanguageId | String | Read-only |
| Name | mserp\_Name | String | Read-only |
| NameAlias | mserp\_NameAlias | String | Read-only |
| PhoneticFirstName | mserp\_PhoneticFirstName | String | Read-only |
| PhoneticLastName | mserp\_PhoneticLastName | String | Read-only |
| PhoneticMiddleName | mserp\_PhoneticMiddleName | String | Read-only |
| PrimaryAddressLocation | mserp\_PrimaryAddressLocation | Int64 | Read-only |
| PrimaryContactEmail | mserp\_PrimaryContactEmail | String | Read-only |
| PrimaryContactEmailDescription | mserp\_PrimaryContactEmailDescription | String | Read-only |
| PrimaryContactEmailIsIM | mserp\_PrimaryContactEmailIsIM | Enum | Read-only |
| PrimaryContactEmailIsPrivate | mserp\_PrimaryContactEmailIsPrivate | Enum | Read-only |
| PrimaryContactEmailPurpose | mserp\_PrimaryContactEmailPurpose | String | Read-only |
| PrimaryContactFax | mserp\_PrimaryContactFax | String | Read-only |
| PrimaryContactFaxDescription | mserp\_PrimaryContactFaxDescription | String | Read-only |
| PrimaryContactFaxExtension | mserp\_PrimaryContactFaxExtension | String | Read-only |
| PrimaryContactFaxIsPrivate | mserp\_PrimaryContactFaxIsPrivate| Enum | Read-only |
| PrimaryContactFaxPurpose | mserp\_PrimaryContactFaxPurpose | String | Read-only |
| PrimaryContactPhone | mserp\_PrimaryContactPhone | String | Read-only |
| PrimaryContactPhoneDescription | mserp\_PrimaryContactPhoneDescription | String | Read-only |
| PrimaryContactPhoneExtension | mserp\_PrimaryContactPhoneExtension | String | Read-only |
| PrimaryContactPhoneIsMobile | mserp\_PrimaryContactPhoneIsMobile | Enum | Read-only |
| PrimaryContactURLPurpose | mserp\_PrimaryContactURLPurpose | String | Read-only |
| PrimaryContactURLIsPrivate | mserp\_PrimaryContactURLIsPrivate | Enum | Read-only |
| PrimaryContactURLDescription | mserp\_PrimaryContactURLDescription | String | Read-only |
| PrimaryContactPhonePurpose | mserp\_PrimaryContactPhonePurpose | String | Read-only |
| PrimaryContactPhoneIsPrivate | mserp\_PrimaryContactPhoneIsPrivate | Enum | Read-only |
| PrimaryContactURL | mserp\_PrimaryContactURL | String | Read-only |
| PrimaryContactFacebook | mserp\_PrimaryContactFacebook | String | Read-only |
| PrimaryContactFacebookDescription | mserp\_PrimaryContactFacebookDescription | String | Read-only |
| PrimaryContactFacebookIsPrivate | mserp\_PrimaryContactFacebookIsPrivate | Enum | Read-only |
| PrimaryContactFacebookPurpose | mserp\_PrimaryContactFacebookPurpose | String | Read-only |
| PrimaryContactLinkedIn | mserp\_PrimaryContactLinkedIn | String | Read-only |
| PrimaryContactLinkedInDescription | mserp\_PrimaryContactLinkedInDescription | String | Read-only |
| PrimaryContactLinkedInIsPrivate | mserp\_PrimaryContactLinkedInIsPrivate | Enum | Read-only |
| PrimaryContactLinkedInPurpose | mserp\_PrimaryContactLinkedInPurpose | String | Read-only |
| PrimaryContactTwitter | mserp\_PrimaryContactTwitter | String | Read-only |
| PrimaryContactTwitterPurpose | mserp\_PrimaryContactTwitterPurpose | String | Read-only |
| PrimaryContactTwitterIsPrivate | mserp\_PrimaryContactTwitterIsPrivate | Enum | Read-only |
| PrimaryContactTwitterDescription | mserp\_PrimaryContactTwitterDescription | String | Read-only |
| ProfessionalSuffix | mserp\_ProfessionalSuffix | String | Read-only |
| ProfessionalTitle | mserp\_ProfessionalTitle | String | Read-only |
| PersonalTitle | mserp\_PersonalTitle | String | Read-only |
| PersonalSuffix | mserp\_PersonalSuffix | String | Read-only |
| TitleId | mserp\_TitleId | String | Read-only |
| OriginalHireDateTime | mserp\_OriginalHireDateTime | Date time offset | Read-only |
| SeniorityDate | mserp\_SeniorityDate | Date time offset | Read-only |
| AnniversaryDateTime | mserp\_AnniversaryDateTime | Date time offset | Read-only |
| OfficeLocation | mserp\_OfficeLocation | String | Read-only |
| OfficeLocationId | mserp\_OfficeLocationId | String | Read-only |
| SummaryValidFrom | mserp\_SummaryValidFrom | Date time offset | Read-only |
| SummaryValidTo | mserp\_SummaryValidTo | Date time offset | Read-only |
| BirthDate | mserp\_BirthDate | Date time offset | Read-only |
| CitizenshipCountryRegion | mserp\_CitizenshipCountryRegion | String | Read-only |
| NationalityCountryRegion | mserp\_NationalityCountryRegion | String | Read-only |
| DeceasedDate | mserp\_DeceasedDate | Date time offset | Read-only |
| DisabledVerificationDate | mserp\_DisabledVerificationDate | Date time offset | Read-only |
| Education | mserp\_Education | String | Read-only |
| EthnicOriginId | mserp\_EthnicOriginId | String | Read-only |
| FatherBirthCountryRegion | mserp\_FatherBirthCountryRegion | String | Read-only |
| Gender | mserp\_Gender | Enum | Read-only |
| IsDisabled | mserp\_IsDisabled | Enum | Read-only |
| IsFulltimeStudent | mserp\_IsFulltimeStudent | Enum | Read-only |
| MotherBirthCountryRegion | mserp\_MotherBirthCountryRegion | String | Read-only |
| NativeLanguageId | mserp\_NativeLanguageId | String | Read-only |
| PersonBirthCountryRegion | mserp\_PersonBirthCountryRegion | String | Read-only |
| PersonBirthCity | mserp\_PersonBirthCity | String | Read-only |
| IsDisabledVeteran | mserp\_IsDisabledVeteran | Enum | Read-only |
| IsExpatriateRulingApplicable | mserp\_IsExpatriateRulingApplicable | Enum | Read-only |
| ExpatriateRulingValidFrom | mserp\_ExpatriateRulingValidFrom | Date time offset | Read-only |
| ExpatriateRulingValidTo | mserp\_ExpatriateRulingValidTo | Date time offset | Read-only |
| MaritalStatus | mserp\_MaritalStatus | Enum | Read-only |
| NumberOfDependents | mserp\_NumberOfDependents | Int | Read-only |
| MilitaryServiceStartDate | mserp\_MilitaryServiceStartDate | Date time offset | Read-only |
| MilitaryServiceEndDate | mserp\_MilitaryServiceEndDate | Date time offset | Read-only |
| VeteranStatusId | mserp\_VeteranStatusId | String | Read-only |
| PersonDetailsValidFrom | mserp\_PersonDetailsValidFrom | Date time offset | Read-only |
| PersonDetailsValidTo | mserp\_PersonDetailsValidTo | Date time offset | Read-only |
| AddressBooks | mserp\_AddressBooks | String | Read-only |
| AddressCity | mserp\_AddressCity | String | Read-only |
| AddressCountryRegionId | mserp\_AddressCountryRegionId | String | Read-only |
| AddressCountryRegionISOCode | mserp\_AddressCountryRegionISOCode | String | Read-only |
| AddressCounty | mserp\_AddressCounty | String | Read-only |
| AddressDistrictName | mserp\_AddressDistrictName | String | Read-only |
| AddressLocationId | mserp\_AddressLocationId | String | Read-only |
| AddressNameDescription | mserp\_AddressNameDescription | String | Read-only |
| AddressPurpose | mserp\_AddressPurpose | String | Read-only |
| AddressState | mserp\_AddressState | String | Read-only |
| AddressStreet | mserp\_AddressStreet | String | Read-only |
| AddressZipCode | mserp\_AddressZipCode | String | Read-only |
| AddressValidFrom | mserp\_AddressValidFrom | Date time offset | Read-only |
| AddressValidTo | mserp\_AddressValidTo | Date time offset | Read-only |
| FirstName | mserp\_FirstName | String | Read-only |
| MiddleName | mserp\_MiddleName | String | Read-only |
| LastNamePrefix | mserp\_LastNamePrefix | String | Read-only |
| LastName | mserp\_LastName | String | Read-only |
| PartyType | mserp\_PartyType | String | Read-only |
| NameSequenceDisplayAs | mserp\_NameSequenceDisplayAs | String | Read-only |
| ElectronicLocationId | mserp\_ElectronicLocationId | String | Read-only |
| WorkerType | mserp\_WorkerType | Enum | Read-only |
| WorkerStatus | mserp\_WorkerStatus | Enum | Read-only |
| AllowRehire | mserp\_AllowRehire | Enum | Read-only |
| WorksFromHome | mserp\_WorksFromHome | Enum | Read-only |
| User | mserp\_User | String | Read-only |
| PersonUserValidFrom | mserp\_PersonUserValidFrom | Date time offset | Read-only |
| PersonUserValidTo | mserp\_PersonUserValidTo | Date time offset | Read-only |
| IdentityEmail | mserp\_IdentityEmail | String | Read-only |
| ObjectId | mserp\_ObjectId | GUID | Read-only |
| IdentityProvider | mserp\_IdentityProvider | String | Read-only |
| EthnicOrigin | mserp\_EthnicOrigin | Int64 | Read-only |
| Location | mserp\_Location | Int64 | Read-only |
| NameValidFrom | mserp\_NameValidFrom | Date time offset | Read-only |
| NameValidTo | mserp\_NameValidTo | Date time offset | Read-only |
| NativeLanguage | mserp\_NativeLanguage | String | Read-only |
| Person | mserp\_Person | Int64 | Read-only |
| PrimaryContactEmailRecordId | mserp\_PrimaryContactEmailRecordId | Int64 | Read-only |
| PrimaryContactFacebookRecordId | mserp\_PrimaryContactFacebookRecordId | Int64 | Read-only |
| PrimaryContactFaxRecordId | mserp\_PrimaryContactFaxRecordId | Int64 | Read-only |
| PrimaryContactLinkedInRecordId | mserp\_PrimaryContactLinkedInRecordId | Int64 | Read-only |
| PrimaryContactPhoneRecordId | mserp\_PrimaryContactPhoneRecordId | Int64 | Read-only |
| PrimaryContactTwitterRecordId | mserp\_PrimaryContactTwitterRecordId | Int64 | Read-only |
| PrimaryContactURLRecordId | mserp\_PrimaryContactURLRecordId | Int64 | Read-only |
| Title | mserp\_Title | Int64 | Read-only |
| VeteranStatus | mserp\_VeteranStatus | Int64 | Read-only |

## Example query for PayIntV1WorkerEntity

Physical name: mserp\_payintv1workerentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1workerentities_
```

**Response**

```JSON
{  
    "mserp_personnelnumber": "000001",  
    "mserp_partynumber": "000000032",  
    "mserp_knownas": "",  
    "mserp_languageid": "en-us",  
    "mserp_name": "Jodi Christiansen",  
    "mserp_namealias": "Jodi Christiansen",  
    "mserp_phoneticfirstname": "",  
    "mserp_phoneticlastname": "",  
    "mserp_phoneticmiddlename": "",  
    "mserp_primarycontactemail": "<jodi@contoso.com>",  
    "mserp_primarycontactemaildescription": "Work",  
    "mserp_primarycontactemailisim": 200000001,  
    "mserp_primarycontactemailisprivate": 200000000,  
    "mserp_primarycontactemailpurpose": "Home",  
    "mserp_primarycontactfax": "",  
    "mserp_primarycontactfaxdescription": "",  
    "mserp_primarycontactfaxextension": "",  
    "mserp_primarycontactfaxisprivate": 200000000,  
    "mserp_primarycontactfaxpurpose": "",  
    "mserp_primarycontactphone": "425-555-5049",  
    "mserp_primarycontactphonedescription": "Work",  
    "mserp_primarycontactphoneextension": "5049",  
    "mserp_primarycontactphoneismobile": 200000000,  
    "mserp_primarycontactphoneisprivate": 200000000,  
    "mserp_primarycontactphonepurpose": "Home",  
    "mserp_primarycontacturl": "",  
    "mserp_primarycontacturldescription": "",  
    "mserp_primarycontacturlisprivate": 200000000,  
    "mserp_primarycontacturlpurpose": "",  
    "mserp_primarycontactfacebook": "",  
    "mserp_primarycontactfacebookdescription": "",  
    "mserp_primarycontactfacebookisprivate": 200000000,  
    "mserp_primarycontactfacebookpurpose": "",  
    "mserp_primarycontactlinkedin": "",  
    "mserp_primarycontactlinkedindescription": "",  
    "mserp_primarycontactlinkedinisprivate": 200000000,  
    "mserp_primarycontactlinkedinpurpose": "",  
    "mserp_primarycontacttwitter": "",  
    "mserp_primarycontacttwitterpurpose": "",  
    "mserp_primarycontacttwitterisprivate": 200000000,  
    "mserp_primarycontacttwitterdescription": "",  
    "mserp_professionalsuffix": "",  
    "mserp_professionaltitle": "",  
    "mserp_personaltitle": "",  
    "mserp_personalsuffix": "",  
    "mserp_titleid": "Compensation & Benefits Cons.",  
    "mserp_senioritydate": "2006-02-01T08:00:00Z",  
    "mserp_officelocation": "Building B - 5049",  
    "mserp_officelocationid": "000000034",  
    "mserp_summaryvalidfrom": "2012-09-20T21:23:17Z",  
    "mserp_summaryvalidto": "2154-12-31T23:59:59Z",  
    "mserp_birthdate": "1972-03-06T00:00:00Z",  
    "mserp_citizenshipcountryregion": "",  
    "mserp_nationalitycountryregion": "",  
    "mserp_education": "",  
    "mserp_ethnicoriginid": "White",  
    "mserp_fatherbirthcountryregion": "",  
    "mserp_gender": 200000002,  
    "mserp_isdisabled": 200000000,  
    "mserp_isfulltimestudent": 200000000,  
    "mserp_motherbirthcountryregion": "",  
    "mserp_nativelanguageid": "English",  
    "mserp_personbirthcountryregion": "",  
    "mserp_personbirthcity": "",  
    "mserp_isdisabledveteran": 200000000,  
    "mserp_isexpatriaterulingapplicable": 200000000,  
    "mserp_maritalstatus": 200000001,  
    "mserp_numberofdependents": 2,  
    "mserp_veteranstatusid": "",  
    "mserp_persondetailsvalidfrom": "2012-09-11T20:09:56Z",  
    "mserp_persondetailsvalidto": "2154-12-31T23:59:59Z",  
    "mserp_addressbooks": "",  
    "mserp_addresscity": "Bellevue",  
    "mserp_addresscountryregionid": "USA",  
    "mserp_addresscountryregionisocode": "US",  
    "mserp_addresscounty": "KING",  
    "mserp_addressdistrictname": "",  
    "mserp_addresslocationid": "000000594",  
    "mserp_addressnamedescription": "Home address",  
    "mserp_addresspurpose": "Home",  
    "mserp_addressstate": "WA",  
    "mserp_addressstreet": "3219 Oak St",  
    "mserp_addresszipcode": "98107",  
    "mserp_addressvalidfrom": "2012-09-20T21:23:11Z",  
    "mserp_addressvalidto": "2154-12-31T23:59:59Z",  
    "mserp_firstname": "Jodi",  
    "mserp_middlename": "",  
    "mserp_lastnameprefix": "",  
    "mserp_lastname": "Christiansen",  
    "mserp_partytype": "Person",  
    "mserp_namesequencedisplayas": "FirstMiddleLast",  
    "mserp_electroniclocationid": "000000042",  
    "mserp_workertype": 200000001,  
    "mserp_workerstatus": 200000001,  
    "mserp_allowrehire": 200000000,  
    "mserp_worksfromhome": 200000000,  
    "mserp_user": "JODI",  
    "mserp_personuservalidfrom": "2013-03-10T18:17:42Z",  
    "mserp_personuservalidto": "2154-12-31T23:59:59Z",  
    "mserp_identityemail": "<JODI@contosoax7.onmicrosoft.com>",  
    "mserp_identityprovider": "<https://sts.windows.net/>",  
    "mserp_objectid": "4545ac9b-a78d-4721-b626-f0f700517eab",  
    "mserp_namevalidto": "2154-12-31T23:59:59Z",  
    "mserp_militaryserviceenddate": null,  
    "mserp_anniversarydatetime": null,  
    "mserp_expatriaterulingvalidto": null,  
    "mserp_militaryservicestartdate": null,  
    "mserp_deceaseddate": null,  
    "mserp_disabledverificationdate": null,  
    "mserp_expatriaterulingvalidfrom": null,  
    "versionnumber": null,  
    "mserp_namevalidfrom": null,  
    "mserp_originalhiredatetime": null  
}
```
