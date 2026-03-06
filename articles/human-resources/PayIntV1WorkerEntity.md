---
# required metadata

title: Worker entity
description: This article provides details and an example query for the Worker entity in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 02/20/2026
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

This article describes the Worker entity (PayIntV1WorkerEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the worker.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Primarycontactphoneismobile | mserp_primarycontactphoneismobile | Enum | Read-only |
| Senioritydate | mserp_senioritydate | Date time offset | Read-only |
| Expatriaterulingvalidto | mserp_expatriaterulingvalidto | Date time offset | Read-only |
| Addresspurpose | mserp_addresspurpose | String | Read-only |
| Namesequencedisplayas | mserp_namesequencedisplayas | String | Read-only |
| Name | mserp_name | String | Read-only |
| Primarycontactfaxpurpose | mserp_primarycontactfaxpurpose | String | Read-only |
| Worksfromhome | mserp_worksfromhome | Enum | Read-only |
| Officelocation | mserp_officelocation | String | Read-only |
| Fatherbirthcountryregion | mserp_fatherbirthcountryregion | String | Read-only |
| Addresscountryregionid | mserp_addresscountryregionid | String | Read-only |
| User | mserp_user | String | Read-only |
| Primarycontactphonedescription | mserp_primarycontactphonedescription | String | Read-only |
| Identityemail | mserp_identityemail | String | Read-only |
| Primarycontactfaxisprivate | mserp_primarycontactfaxisprivate | Enum | Read-only |
| Primarycontacttwitterisprivate | mserp_primarycontacttwitterisprivate | Enum | Read-only |
| Isexpatriaterulingapplicable | mserp_isexpatriaterulingapplicable | Enum | Read-only |
| Personaltitle | mserp_personaltitle | String | Read-only |
| Nativelanguageid | mserp_nativelanguageid | String | Read-only |
| Addresscounty | mserp_addresscounty | String | Read-only |
| Middlename | mserp_middlename | String | Read-only |
| Personnelnumber | mserp_personnelnumber | String | Read-only |
| Primarycontactemailpurpose | mserp_primarycontactemailpurpose | String | Read-only |
| Primarycontactlinkedin | mserp_primarycontactlinkedin | String | Read-only |
| Workertype | mserp_workertype | Enum | Read-only |
| Primarycontactfacebookisprivate | mserp_primarycontactfacebookisprivate | Enum | Read-only |
| Isfulltimestudent | mserp_isfulltimestudent | Enum | Read-only |
| Titleid | mserp_titleid | String | Read-only |
| Deceaseddate | mserp_deceaseddate | Date time offset | Read-only |
| Persondetailsvalidfrom | mserp_persondetailsvalidfrom | Date time offset | Read-only |
| Lastname | mserp_lastname | String | Read-only |
| Primarycontactemailisim | mserp_primarycontactemailisim | Enum | Read-only |
| Primarycontactfaxdescription | mserp_primarycontactfaxdescription | String | Read-only |
| Primarycontactlinkedinpurpose | mserp_primarycontactlinkedinpurpose | String | Read-only |
| Primarycontacttwitterpurpose | mserp_primarycontacttwitterpurpose | String | Read-only |
| Education | mserp_education | String | Read-only |
| Addressbooks | mserp_addressbooks | String | Read-only |
| Addresszipcode | mserp_addresszipcode | String | Read-only |
| Objectid | mserp_objectid | String | Read-only |
| Phoneticlastname | mserp_phoneticlastname | String | Read-only |
| Primarycontacturlpurpose | mserp_primarycontacturlpurpose | String | Read-only |
| Professionalsuffix | mserp_professionalsuffix | String | Read-only |
| Summaryvalidto | mserp_summaryvalidto | Date time offset | Read-only |
| Numberofdependents | mserp_numberofdependents | Enum | Read-only |
| Addressvalidto | mserp_addressvalidto | Date time offset | Read-only |
| Namevalidto | mserp_namevalidto | Date time offset | Read-only |
| Primarycontactemail | mserp_primarycontactemail | String | Read-only |
| Primarycontactfacebookdescription | mserp_primarycontactfacebookdescription | String | Read-only |
| Maritalstatus | mserp_maritalstatus | Enum | Read-only |
| Citizenshipcountryregion | mserp_citizenshipcountryregion | String | Read-only |
| Militaryserviceenddate | mserp_militaryserviceenddate | Date time offset | Read-only |
| Addressnamedescription | mserp_addressnamedescription | String | Read-only |
| Personuservalidfrom | mserp_personuservalidfrom | Date time offset | Read-only |
| Languageid | mserp_languageid | String | Read-only |
| Primarycontactphoneextension | mserp_primarycontactphoneextension | String | Read-only |
| Anniversarydatetime | mserp_anniversarydatetime | Date time offset | Read-only |
| Personbirthcountryregion | mserp_personbirthcountryregion | String | Read-only |
| Addressstate | mserp_addressstate | String | Read-only |
| Namealias | mserp_namealias | String | Read-only |
| Primarycontacturl | mserp_primarycontacturl | String | Read-only |
| Primarycontactphoneisprivate | mserp_primarycontactphoneisprivate | Enum | Read-only |
| Gender | mserp_gender | Enum | Read-only |
| Officelocationid | mserp_officelocationid | String | Read-only |
| Expatriaterulingvalidfrom | mserp_expatriaterulingvalidfrom | Date time offset | Read-only |
| Addresscountryregionisocode | mserp_addresscountryregionisocode | String | Read-only |
| Partytype | mserp_partytype | String | Read-only |
| Primarycontactfaxextension | mserp_primarycontactfaxextension | String | Read-only |
| Primarycontactlinkedinisprivate | mserp_primarycontactlinkedinisprivate | Enum | Read-only |
| Personalsuffix | mserp_personalsuffix | String | Read-only |
| Ethnicoriginid | mserp_ethnicoriginid | String | Read-only |
| Addressdistrictname | mserp_addressdistrictname | String | Read-only |
| Electroniclocationid | mserp_electroniclocationid | String | Read-only |
| Partynumber | mserp_partynumber | String | Read-only |
| Primarycontactphone | mserp_primarycontactphone | String | Read-only |
| Primarycontactlinkedindescription | mserp_primarycontactlinkedindescription | String | Read-only |
| Allowrehire | mserp_allowrehire | Enum | Read-only |
| Originalhiredatetime | mserp_originalhiredatetime | Date time offset | Read-only |
| Motherbirthcountryregion | mserp_motherbirthcountryregion | String | Read-only |
| Persondetailsvalidto | mserp_persondetailsvalidto | Date time offset | Read-only |
| Firstname | mserp_firstname | String | Read-only |
| Primarycontactemaildescription | mserp_primarycontactemaildescription | String | Read-only |
| Primarycontacttwitter | mserp_primarycontacttwitter | String | Read-only |
| Primarycontactemailisprivate | mserp_primarycontactemailisprivate | Enum | Read-only |
| Isdisabledveteran | mserp_isdisabledveteran | Enum | Read-only |
| Primarycontacttwitterdescription | mserp_primarycontacttwitterdescription | String | Read-only |
| Nationalitycountryregion | mserp_nationalitycountryregion | String | Read-only |
| Addresscity | mserp_addresscity | String | Read-only |
| Lastnameprefix | mserp_lastnameprefix | String | Read-only |
| Namevalidfrom | mserp_namevalidfrom | Date time offset | Read-only |
| Primarycontactfax | mserp_primarycontactfax | String | Read-only |
| Primarycontactfacebook | mserp_primarycontactfacebook | String | Read-only |
| Isdisabled | mserp_isdisabled | Enum | Read-only |
| Professionaltitle | mserp_professionaltitle | String | Read-only |
| Disabledverificationdate | mserp_disabledverificationdate | Date time offset | Read-only |
| Militaryservicestartdate | mserp_militaryservicestartdate | Date time offset | Read-only |
| Addressstreet | mserp_addressstreet | String | Read-only |
| Workerstatus | mserp_workerstatus | Enum | Read-only |
| Phoneticfirstname | mserp_phoneticfirstname | String | Read-only |
| Primarycontactfacebookpurpose | mserp_primarycontactfacebookpurpose | String | Read-only |
| Summaryvalidfrom | mserp_summaryvalidfrom | Date time offset | Read-only |
| Veteranstatusid | mserp_veteranstatusid | String | Read-only |
| Addressvalidfrom | mserp_addressvalidfrom | Date time offset | Read-only |
| Personuservalidto | mserp_personuservalidto | Date time offset | Read-only |
| Phoneticmiddlename | mserp_phoneticmiddlename | String | Read-only |
| Primarycontactphonepurpose | mserp_primarycontactphonepurpose | String | Read-only |
| Primarycontacturlisprivate | mserp_primarycontacturlisprivate | Enum | Read-only |
| Birthdate | mserp_birthdate | Date time offset | Read-only |
| Personbirthcity | mserp_personbirthcity | String | Read-only |
| Addresslocationid | mserp_addresslocationid | String | Read-only |
| Identityprovider | mserp_identityprovider | String | Read-only |
| Knownas | mserp_knownas | String | Read-only |
| Primarycontacturldescription | mserp_primarycontacturldescription | String | Read-only |

## Example query for PayIntV1WorkerEntity

Entity name: mserp_payintv1workerentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1workerentities
```

**Response**

```JSON
{  
    "mserp_isexpatriaterulingapplicable": 200000000,
    "mserp_primarycontacturl": "",
    "mserp_isdisabled": 200000000,
    "mserp_partynumber": "000000032",
    "mserp_primarycontactphoneextension": "5049",
    "mserp_personbirthcountryregion": "",
    "mserp_workertype": 200000001,
    "mserp_objectid": "4545ac9b-a78d-4721-b626-f0f700517eab",
    "mserp_primarycontactfaxisprivate": 200000000,
    "mserp_addresscountryregionid": "USA",
    "mserp_personbirthcity": "",
    "mserp_isfulltimestudent": 200000000,
    "mserp_militaryserviceenddate": null,
    "mserp_titleid": "Compensation & Benefits Cons.",
    "mserp_namesequencedisplayas": "FirstMiddleLast",
    "mserp_senioritydate": "2006-02-01T08:00:00Z",
    "mserp_primarycontactemailpurpose": "Home",
    "mserp_addresspurpose": "Home",
    "mserp_persondetailsvalidto": "2154-12-31T23:59:59Z",
    "mserp_professionalsuffix": "",
    "mserp_addressvalidto": "2154-12-31T23:59:59Z",
    "mserp_personuservalidto": "2154-12-31T23:59:59Z",
    "mserp_ethnicoriginid": "White",
    "mserp_phoneticfirstname": "",
    "mserp_education": "",
    "mserp_persondetailsvalidfrom": "2012-09-11T20:09:56Z",
    "mserp_anniversarydatetime": null,
    "mserp_primarycontacturlpurpose": "",
    "mserp_personalsuffix": "",
    "mserp_middlename": "",
    "mserp_expatriaterulingvalidto": null,
    "mserp_nationalitycountryregion": "",
    "mserp_primarycontactemaildescription": "Work",
    "mserp_officelocationid": "000000034",
    "mserp_addressdistrictname": "",
    "mserp_primarycontacttwitterdescription": "",
    "mserp_primarycontactlinkedindescription": "",
    "mserp_personnelnumber": "000001",
    "mserp_primarycontactlinkedinpurpose": "",
    "mserp_user": "JODI",
    "mserp_primarycontactfaxextension": "",
    "mserp_summaryvalidto": "2154-12-31T23:59:59Z",
    "mserp_birthdate": "1972-03-06T00:00:00Z",
    "mserp_primarycontactlinkedin": "",
    "mserp_primarycontactfax": "",
    "mserp_maritalstatus": 200000001,
    "mserp_militaryservicestartdate": null,
    "mserp_name": "Jodi Christiansen",
    "mserp_lastnameprefix": "",
    "mserp_addressbooks": "",
    "mserp_primarycontactemail": "jodi@contoso.com",
    "mserp_phoneticlastname": "",
    "mserp_addressnamedescription": "Home address",
    "mserp_personuservalidfrom": "2013-03-10T18:17:42Z",
    "mserp_languageid": "en-us",
    "mserp_primarycontacttwitterpurpose": "",
    "mserp_deceaseddate": null,
    "mserp_namealias": "Jodi Christiansen",
    "mserp_primarycontactfacebookdescription": "",
    "mserp_firstname": "Jodi",
    "mserp_worksfromhome": 200000000,
    "mserp_disabledverificationdate": null,
    "mserp_primarycontactemailisprivate": 200000000,
    "mserp_gender": 200000002,
    "mserp_expatriaterulingvalidfrom": null,
    "mserp_addresscounty": "KING",
    "mserp_personaltitle": "",
    "mserp_addresszipcode": "98107",
    "mserp_phoneticmiddlename": "",
    "mserp_primarycontactphone": "425-555-5049",
    "mserp_primarycontactphonepurpose": "Home",
    "mserp_primarycontactemailisim": 200000001,
    "mserp_knownas": "",
    "mserp_lastname": "Christiansen",
    "mserp_primarycontactfaxdescription": "",
    "mserp_primarycontactphoneisprivate": 200000000,
    "mserp_veteranstatusid": "",
    "mserp_electroniclocationid": "000000042",
    "mserp_summaryvalidfrom": "2012-09-20T21:23:17Z",
    "mserp_addressvalidfrom": "2012-09-20T21:23:11Z",
    "mserp_primarycontactfaxpurpose": "",
    "mserp_primarycontacttwitterisprivate": 200000000,
    "mserp_workerstatus": 200000001,
    "mserp_citizenshipcountryregion": "",
    "mserp_primarycontacturldescription": "",
    "mserp_addressstreet": "3219 Oak St",
    "mserp_numberofdependents": 2,
    "mserp_primarycontactfacebook": "",
    "mserp_addresscountryregionisocode": "US",
    "mserp_isdisabledveteran": 200000000,
    "mserp_namevalidfrom": null,
    "mserp_allowrehire": 200000000,
    "mserp_addressstate": "WA",
    "mserp_nativelanguageid": "English",
    "mserp_primarycontactlinkedinisprivate": 200000000,
    "mserp_officelocation": "Building B - 5049",
    "mserp_primarycontacturlisprivate": 200000000,
    "mserp_partytype": "Person",
    "mserp_primarycontactphonedescription": "Work",
    "mserp_primarycontactfacebookpurpose": "",
    "mserp_addresslocationid": "000000594",
    "mserp_addresscity": "Bellevue",
    "mserp_originalhiredatetime": null,
    "mserp_primarycontacttwitter": "",
    "mserp_primarycontactphoneismobile": 200000000,
    "mserp_professionaltitle": "",
    "mserp_identityemail": "JODI@contosoax7.onmicrosoft.com",
    "mserp_primarycontactfacebookisprivate": 200000000,
    "mserp_fatherbirthcountryregion": "",
    "mserp_identityprovider": "https://sts.windows.net/",
    "mserp_motherbirthcountryregion": "",
    "mserp_namevalidto": "2154-12-31T23:59:59Z"
}
```
