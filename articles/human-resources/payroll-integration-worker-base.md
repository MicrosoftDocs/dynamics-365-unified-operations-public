---
# required metadata

title: Worker Base entity
description: This article provides details and an example query for the Hcm Worker Base entity in Microsoft Dynamics 365 Human Resources.
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

# Worker Base entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.42.

This article describes the Hcm Worker Base entity (PayIntV2HcmWorkerBaseEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about worker base.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Isfulltimestudent | mserp_isfulltimestudent | Enum | Read-only |
| Personbirthcountryregion | mserp_personbirthcountryregion | String | Read-only |
| Namesequencedisplayas | mserp_namesequencedisplayas | String | Read-only |
| Personnelnumber | mserp_personnelnumber | String | Read-only |
| Namealias | mserp_namealias | String | Read-only |
| Deceaseddate | mserp_deceaseddate | Date time offset | Read-only |
| Motherbirthcountryregion | mserp_motherbirthcountryregion | String | Read-only |
| Nativelanguageid | mserp_nativelanguageid | String | Read-only |
| Languageid | mserp_languageid | String | Read-only |
| Name | mserp_name | String | Read-only |
| Lastnameprefix | mserp_lastnameprefix | String | Read-only |
| Personalsuffix | mserp_personalsuffix | String | Read-only |
| Firstname | mserp_firstname | String | Read-only |
| Professionalsuffix | mserp_professionalsuffix | String | Read-only |
| Fatherbirthcountryregion | mserp_fatherbirthcountryregion | String | Read-only |
| Knownas | mserp_knownas | String | Read-only |
| Phoneticlastname | mserp_phoneticlastname | String | Read-only |
| Middlename | mserp_middlename | String | Read-only |
| Partytype | mserp_partytype | String | Read-only |
| Gender | mserp_gender | Enum | Read-only |
| Phoneticmiddlename | mserp_phoneticmiddlename | String | Read-only |
| Nationalitycountryregion | mserp_nationalitycountryregion | String | Read-only |
| Personbirthcity | mserp_personbirthcity | String | Read-only |
| Allowrehire | mserp_allowrehire | Enum | Read-only |
| Isdisabled | mserp_isdisabled | Enum | Read-only |
| Phoneticfirstname | mserp_phoneticfirstname | String | Read-only |
| Namevalidfrom | mserp_namevalidfrom | Date time offset | Read-only |
| Namevalidto | mserp_namevalidto | Date time offset | Read-only |
| Birthdate | mserp_birthdate | Date time offset | Read-only |
| Citizenshipcountryregion | mserp_citizenshipcountryregion | String | Read-only |
| Personaltitle | mserp_personaltitle | String | Read-only |
| Education | mserp_education | String | Read-only |
| Ethnicoriginid | mserp_ethnicoriginid | String | Read-only |
| Lastname | mserp_lastname | String | Read-only |
| Electroniclocationid | mserp_electroniclocationid | String | Read-only |
| Partynumber | mserp_partynumber | String | Read-only |
| Professionaltitle | mserp_professionaltitle | String | Read-only |
| Disabledverificationdate | mserp_disabledverificationdate | Date time offset | Read-only |
| Primarycontactemail | mserp_primarycontactemail | String | Read-only |

## Example query for PayIntV2HcmWorkerBaseEntity

Entity name: mserp_payintv2hcmworkerbaseentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv2hcmworkerbaseentities
```

**Response**

```JSON
{  
    "mserp_disabledverificationdate": null,
    "mserp_personaltitle": "",
    "mserp_citizenshipcountryregion": "",
    "mserp_personalsuffix": "",
    "mserp_deceaseddate": null,
    "mserp_middlename": "",
    "mserp_personnelnumber": "000001",
    "mserp_namevalidto": "2154-12-31T23:59:59Z",
    "mserp_nationalitycountryregion": "",
    "mserp_professionalsuffix": "",
    "mserp_birthdate": "1972-03-06T00:00:00Z",
    "mserp_namevalidfrom": null,
    "mserp_partynumber": "000000032",
    "mserp_phoneticmiddlename": "",
    "mserp_primarycontactemail": "jodi@contoso.com",
    "mserp_education": "",
    "mserp_fatherbirthcountryregion": "",
    "mserp_partytype": "Person",
    "mserp_gender": 200000002,
    "mserp_name": "Jodi Christiansen",
    "mserp_personbirthcountryregion": "",
    "mserp_personbirthcity": "",
    "mserp_ethnicoriginid": "White",
    "mserp_namesequencedisplayas": "FirstMiddleLast",
    "mserp_phoneticfirstname": "",
    "mserp_lastname": "Christiansen",
    "mserp_namealias": "Jodi Christiansen",
    "mserp_languageid": "en-us",
    "mserp_professionaltitle": "",
    "mserp_motherbirthcountryregion": "",
    "mserp_lastnameprefix": "",
    "mserp_isfulltimestudent": 200000000,
    "mserp_knownas": "",
    "mserp_isdisabled": 200000000,
    "mserp_phoneticlastname": "",
    "mserp_allowrehire": 200000000,
    "mserp_nativelanguageid": "English",
    "mserp_electroniclocationid": "000000042",
    "mserp_firstname": "Jodi"
}
```
