---
# required metadata

title: Worker entity
description: This article provides details and an example query for the PayIntV1WorkerEntity entity in Microsoft Dynamics 365 Human Resources.
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

This article describes the PayIntV1HcmEmploymentEmployeeEntity entity for Dynamics 365 Human Resources.

## Description

This entity provides information about the employee. You must set the payroll integration parameters before using this entity.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| PersonnelNumber |mserp_PersonnelNumber|String | Read-only |
| PartyNumber|mserp_PartyNumber|_String_ | Read-only |
| KnownAs |mserp_KnownAs|_String_ | Read-only |
| LanguageId|mserp_LanguageId|_String_ | Read-only |
| Name|mserp_Name|_String_ | Read-only |
| NameAlias|mserp_NameAlias|_String_ | Read-only |
| PhoneticFirstName|mserp_PhoneticFirstName|_String_ | Read-only |
| PhoneticLastName|mserp_PhoneticLastName|String | Read-only |
| PhoneticMiddleName|mserp_PhoneticMiddleName|_String_ | Read-only |
| PrimaryAddressLocation|mserp_PrimaryAddressLocation|_Int64_ | Read-only |
| PrimaryContactEmail|mserp_PrimaryContactEmail|String | Read-only |
| PrimaryContactEmailDescription|mserp_PrimaryContactEmailDescription|String | Read-only |
| PrimaryContactEmailIsIM|mserp_PrimaryContactEmailIsIM|Enum | Read-only |
| PrimaryContactEmailIsPrivate|mserp_PrimaryContactEmailIsPrivate|Enum | Read-only |
| PrimaryContactEmailPurpose|mserp_PrimaryContactEmailPurpose|String | Read-only |
| PrimaryContactFax|mserp_PrimaryContactFax|String | Read-only |
| PrimaryContactFaxDescription|mserp_PrimaryContactFaxDescription|String | Read-only |
| PrimaryContactFaxExtension|mserp_PrimaryContactFaxExtension|String | Read-only |
| PrimaryContactFaxIsPrivate|mserp_PrimaryContactFaxIsPrivate|Enum | Read-only |
| PrimaryContactFaxPurpose|mserp_PrimaryContactFaxPurpose|String | Read-only |
| PrimaryContactPhone|mserp_PrimaryContactPhone|String | Read-only |
| PrimaryContactPhoneDescription|mserp_PrimaryContactPhoneDescription|String | Read-only |
| PrimaryContactPhoneExtension|mserp_PrimaryContactPhoneExtension|String | Read-only |
| PrimaryContactPhoneIsMobile|mserp_PrimaryContactPhoneIsMobile|Enum | Read-only |
| PrimaryContactURLPurpose|mserp_PrimaryContactURLPurpose|String | Read-only |
| PrimaryContactURLIsPrivate|mserp_PrimaryContactURLIsPrivate|Enum | Read-only |
| PrimaryContactURLDescription|mserp_PrimaryContactURLDescription|String | Read-only |
| PrimaryContactPhonePurpose|mserp_PrimaryContactPhonePurpose|String | Read-only |
| PrimaryContactPhoneIsPrivate|mserp_PrimaryContactPhoneIsPrivate|Enum | Read-only |
| PrimaryContactURL|mserp_PrimaryContactURL|String | Read-only |
| PrimaryContactFacebook|mserp_PrimaryContactFacebook|String | Read-only |
| PrimaryContactFacebookDescription|mserp_PrimaryContactFacebookDescription|String | Read-only |
| PrimaryContactFacebookIsPrivate|mserp_PrimaryContactFacebookIsPrivate|Enum | Read-only |
| PrimaryContactFacebookPurpose|mserp_PrimaryContactFacebookPurpose|String | Read-only |
| PrimaryContactLinkedIn|mserp_PrimaryContactLinkedIn|String | Read-only |
| PrimaryContactLinkedInDescription|mserp_PrimaryContactLinkedInDescription|String | Read-only |
| PrimaryContactLinkedInIsPrivate|mserp_PrimaryContactLinkedInIsPrivate|Enum | Read-only |
| PrimaryContactLinkedInPurpose|mserp_PrimaryContactLinkedInPurpose|String | Read-only |
| PrimaryContactTwitter|mserp_PrimaryContactTwitter|String | Read-only |
| PrimaryContactTwitterPurpose|mserp_PrimaryContactTwitterPurpose|String | Read-only |
| PrimaryContactTwitterIsPrivate|mserp_PrimaryContactTwitterIsPrivate|Enum | Read-only |
| PrimaryContactTwitterDescription|mserp_PrimaryContactTwitterDescription|String | Read-only |
| ProfessionalSuffix|mserp_ProfessionalSuffix|String | Read-only |
| ProfessionalTitle|mserp_ProfessionalTitle|String | Read-only |
| PersonalTitle|mserp_PersonalTitle|String | Read-only |
| PersonalSuffix|mserp_PersonalSuffix|String | Read-only |
| TitleId|mserp_TitleId|String | Read-only |
| OriginalHireDateTime|mserp_OriginalHireDateTime|Date time offset | Read-only |
| SeniorityDate|mserp_SeniorityDate|Date time offset | Read-only |
| AnniversaryDateTime|mserp_AnniversaryDateTime|Date time offset | Read-only |
| OfficeLocation|mserp_OfficeLocation|String | Read-only |
| OfficeLocationId|mserp_OfficeLocationId|String | Read-only |
| SummaryValidFrom|mserp_SummaryValidFrom|Date time offset | Read-only |
| SummaryValidTo|mserp_SummaryValidTo|Date time offset | Read-only |
| BirthDate|mserp_BirthDate|Date time offset | Read-only |
| CitizenshipCountryRegion|mserp_CitizenshipCountryRegion|String | Read-only |
| NationalityCountryRegion|mserp_NationalityCountryRegion|String | Read-only |
| DeceasedDate|mserp_DeceasedDate|Date time offset | Read-only |
| DisabledVerificationDate|mserp_DisabledVerificationDate|Date time offset | Read-only |
| Education|mserp_Education|String | Read-only |
| EthnicOriginId|mserp_EthnicOriginId|String | Read-only |
| FatherBirthCountryRegion|mserp_FatherBirthCountryRegion|String | Read-only |
| Gender|mserp_Gender|Enum | Read-only |
| IsDisabled|mserp_IsDisabled|Enum | Read-only |
| IsFulltimeStudent|mserp_IsFulltimeStudent|Enum | Read-only |
| MotherBirthCountryRegion|mserp_MotherBirthCountryRegion|String | Read-only |
| NativeLanguageId|mserp_NativeLanguageId|String | Read-only |
| PersonBirthCountryRegion|mserp_PersonBirthCountryRegion|String | Read-only |
| PersonBirthCity|mserp_PersonBirthCity|String | Read-only |
| IsDisabledVeteran|mserp_IsDisabledVeteran|Enum | Read-only |
| IsExpatriateRulingApplicable|mserp_IsExpatriateRulingApplicable|Enum | Read-only |
| ExpatriateRulingValidFrom|mserp_ExpatriateRulingValidFrom|Date time offset | Read-only |
| ExpatriateRulingValidTo|mserp_ExpatriateRulingValidTo|Date time offset | Read-only |
| MaritalStatus|mserp_MaritalStatus|Enum | Read-only |
| NumberOfDependents|mserp_NumberOfDependents|Int | Read-only |
| MilitaryServiceStartDate|mserp_MilitaryServiceStartDate|Date time offset | Read-only |
| MilitaryServiceEndDate|mserp_MilitaryServiceEndDate|Date time offset | Read-only |
| VeteranStatusId|mserp_VeteranStatusId|String | Read-only |
| PersonDetailsValidFrom|mserp_PersonDetailsValidFrom|Date time offset | Read-only |
| PersonDetailsValidTo|mserp_PersonDetailsValidTo|Date time offset | Read-only |
| AddressBooks|mserp_AddressBooks|String | Read-only |
| AddressCity|mserp_AddressCity|String | Read-only |
| AddressCountryRegionId|mserp_AddressCountryRegionId|String | Read-only |
| AddressCountryRegionISOCode|mserp_AddressCountryRegionISOCode|String | Read-only |
| AddressCounty|mserp_AddressCounty|String | Read-only |
| AddressDistrictName|mserp_AddressDistrictName|String | Read-only |
| AddressLocationId|mserp_AddressLocationId|String | Read-only |
| AddressNameDescription|mserp_AddressNameDescription|String | Read-only |
| AddressPurpose|mserp_AddressPurpose|String | Read-only |
| AddressState|mserp_AddressState|String | Read-only |
| AddressStreet|mserp_AddressStreet|String | Read-only |
| AddressZipCode|mserp_AddressZipCode|String | Read-only |
| AddressValidFrom|mserp_AddressValidFrom|Date time offset | Read-only |
| AddressValidTo|mserp_AddressValidTo|Date time offset | Read-only |
| FirstName|mserp_FirstName|String | Read-only |
| MiddleName|mserp_MiddleName|String | Read-only |
| LastNamePrefix|mserp_LastNamePrefix|String | Read-only |
| LastName|mserp_LastName|String | Read-only |
| PartyType|mserp_PartyType|String | Read-only |
| NameSequenceDisplayAs|mserp_NameSequenceDisplayAs|String | Read-only |
| ElectronicLocationId|mserp_ElectronicLocationId|String | Read-only |
| WorkerType|mserp_WorkerType|Enum | Read-only |
| WorkerStatus|mserp_WorkerStatus|Enum | Read-only |
| AllowRehire|mserp_AllowRehire|Enum | Read-only |
| WorksFromHome|mserp_WorksFromHome|Enum | Read-only |
| User|mserp_User|String | Read-only |
| PersonUserValidFrom|mserp_PersonUserValidFrom|Date time offset | Read-only |
| PersonUserValidTo|mserp_PersonUserValidTo|Date time offset | Read-only |
| IdentityEmail|mserp_IdentityEmail|String | Read-only |
| ObjectId|mserp_ObjectId|GUID | Read-only |
| IdentityProvider|mserp_IdentityProvider|String | Read-only |
| EthnicOrigin|mserp_EthnicOrigin|Int64 | Read-only |
| Location|mserp_Location|Int64 | Read-only |
| NameValidFrom|mserp_NameValidFrom|Date time offset | Read-only |
| NameValidTo|mserp_NameValidTo|Date time offset | Read-only |
| NativeLanguage|mserp_NativeLanguage|String | Read-only |
| Person|mserp_Person|Int64 | Read-only |
| PrimaryContactEmailRecordId|mserp_PrimaryContactEmailRecordId|Int64 | Read-only |
| PrimaryContactFacebookRecordId|mserp_PrimaryContactFacebookRecordId|Int64 | Read-only |
| PrimaryContactFaxRecordId| mserp_PrimaryContactFaxRecordId|Int64 | Read-only |
| PrimaryContactLinkedInRecordId| mserp_PrimaryContactLinkedInRecordId|Int64 | Read-only |
| PrimaryContactPhoneRecordId| mserp_PrimaryContactPhoneRecordId|Int64 | Read-only |
| PrimaryContactTwitterRecordId|mserp_PrimaryContactTwitterRecordId|Int64 | Read-only |
| PrimaryContactURLRecordId |mserp_PrimaryContactURLRecordId| Int64 | Read-only |
| Title| mserp_Title|Int64 | Read-only |
| VeteranStatus|mserp_VeteranStatus|Int64 | Read-only |


## Example query for PayInt V1 worker entity

Physical name: mserp_payintv1workerentities

**Request**

```HTTP
GET \[Organizaton URI\]/api/data/v9.1/mserp_payintv1workerentities_
```

**Response**

```JSONCopy
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

