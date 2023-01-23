---
# required metadata

title: Party contact
description: This article describes the Party contact entity for Dynamics 365 Human Resources.
author: jaredha
ms.date: 01/03/2023
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

# Party contact


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Party contact entity for Dynamics 365 Human Resources.

Physical name: mshr_dirpartycontactentities

## Description

This entity describes the candidate’s contact information, including phone, email, and social media accounts.

## JSON representation

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

## Properties

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
| **Locator Extension**<br>mshr_locatorextension<br>*String* | Read/write<br>Optional | The locator extension. For example, if the type is **Phone**, then this property would contain the phone number extension. |
| **Is Mobile**<br>mshr_ismobilephone<br>*mshr_noyes option set* | Read/write<br>Required | Specifies whether the phone is a mobile number. |
| **Is Instant Message**<br>mshr_isinstantmessage<br>*mshr_noyes option set* | Read/write<br>Required | Specifies whether the phone is enabled for instant messaging. |
| **Is Primary**<br>mshr_isprimary<br>*mshr_noyes option set* | Read/write<br>Required | Determines the primary contact of the contact type. There must be only one primary record per contact type. |
| **Is Private**<br>mshr_isprivate<br>*mshr_noyes option set* | Read/write<br>Required | Identifies whether this address is a private address for the person. |
| **Purpose**<br>mshr_purpose<br>*String* | Read/write<br>Optional | The purpose/role of the contact details. |
| **Primary Field**<br>mshr_primaryfield<br>*String* | Read-only<br>Required | Field used as a primary identifier of the entity record. Combination of party number, type, description, and locator. |

## See also

[Applicant Tracking System integration API introduction](hr-admin-integration-ats-api-introduction.md)<br>
[Example query for Candidate to hire](hr-admin-integration-ats-api-candidate-to-hire-example-query.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
